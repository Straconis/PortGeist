# Orange Pi 5 Plus + ESP32-S3 Architecture

**Project:** PortGeist
**Status:** Research candidate - not implemented
**Purpose:** Evaluate an alternative to Raspberry Pi 5 + AI HAT+ 2.

## Overview

PortGeist is an autonomous, local-first AI KVM appliance.

An Orange Pi 5 Plus could serve as the main computer, while
an ESP32-S3 handles physical controls and USB HID emulation.

This is an architectural proposal, not a validated design.

## Why Orange Pi 5 Plus?

The Orange Pi 5 Plus uses the Rockchip RK3588 SoC.

Potential advantages:

- Native HDMI input, potentially eliminating USB capture hardware.
- Integrated 6 TOPS NPU for compatible AI workloads.
- Eight-core CPU for orchestration and general processing.
- NVMe storage support.
- USB and GPIO connectivity.
- Optional self-hosted LAN AI inference.
- Potentially fewer components than a Pi 5 plus accelerator.

The HDMI input must be tested for Linux driver support,
capture reliability, resolution, latency, and compatibility
with BIOS, UEFI, and recovery screens.

## Proposed Architecture

Target Computer
    | HDMI video
    v
Orange Pi 5 Plus
    - HDMI input and frame capture
    - Screenshot preprocessing
    - AI inference
    - Agent planning and memory
    - Observe / reason / act / verify loop
    - Local web interface
    - Logging and checkpoints
    |
    | UART or other suitable communication link
    v
ESP32-S3
    - USB HID keyboard and mouse emulation
    - Physical YES and NO buttons
    - Status LEDs
    - LCD interface, if supported by selected hardware
    - Input watchdog and safety controls
    |
    | USB HID
    v
Target Computer

A dedicated hardware emergency-stop mechanism is required.

The final architecture may assign the LCD to the Orange Pi
rather than the ESP32, depending on interface and performance.

## ESP32-S3 Responsibilities

The ESP32-S3 is a hardware-control coprocessor.

Its proposed responsibilities include:

1. Receive structured keyboard and mouse commands.
2. Validate commands against safety constraints.
3. Present itself as a USB HID device to the target.
4. Read physical YES and NO button inputs.
5. Drive status indicators and potentially the LCD.
6. Enforce communication timeouts.
7. Release held keys and mouse buttons on interruption.
8. Report controller status to the main computer.

The ESP32-S3 is not intended to accelerate a large language
model or vision-language model.

USB device support and the exact ESP32-S3 board wiring must
be verified before hardware selection.

## AI Workload Separation

Potential division of work:

Orange Pi NPU:
- Compatible computer-vision workloads
- Compatible small vision-language models, if supported

Orange Pi CPU:
- Agent orchestration
- Planning and tool coordination
- Memory, logs, and checkpoints
- Model inference when NPU support is unavailable

ESP32-S3:
- Real-time physical control
- Buttons and indicators
- USB HID
- Watchdog and input safety

The NPU and CPU may execute separate workloads concurrently,
but actual performance requires benchmarking.

## Inference Modes

PortGeist remains offline-first.

### Onboard

Use models running directly on the Orange Pi.

### LAN-assisted

Connect to a user-owned inference server on the local network.
No paid cloud AI API is required.

### Automatic

Prefer a suitable LAN inference server when available.
Fall back to onboard inference only when the task can be handled
safely by the available local model.

Otherwise pause and request human intervention.

No account activation or internet connection should be required
for core operation.

## Comparison With Raspberry Pi Approach

### Raspberry Pi 5 + AI HAT+ 2

Advantages:
- Hailo accelerator with dedicated memory.
- Established Raspberry Pi software ecosystem.
- Potentially stronger supported accelerator workloads.

Disadvantages:
- External HDMI capture required.
- Additional accelerator hardware.
- USB HID implementation requires hardware planning.

### Orange Pi 5 Plus + ESP32-S3

Advantages:
- Integrated HDMI input.
- Integrated Rockchip NPU.
- Dedicated HID and physical-control processor.
- Potentially simpler external connections.

Disadvantages:
- Rockchip NPU model compatibility constraints.
- HDMI capture driver validation required.
- Additional controller firmware to develop.
- Less certain AI model support and tooling.

The 40 TOPS Hailo and 6 TOPS Rockchip figures must not be
treated as directly comparable performance measurements.

## Validation Milestones

1. Confirm HDMI input functionality under the chosen Linux OS.
2. Capture BIOS, UEFI, Windows, and Linux screenshots.
3. Measure capture latency and reliability.
4. Test supported NPU model formats and runtimes.
5. Benchmark screenshot interpretation accuracy.
6. Benchmark multi-step reasoning and task completion.
7. Verify ESP32-S3 USB HID keyboard and mouse operation.
8. Test button, LED, LCD, and watchdog behavior.
9. Test emergency-stop behavior.
10. Compare cost, power consumption, and performance against
    Raspberry Pi 5 + AI HAT+ 2.

## Open Questions

- Which Rockchip-compatible vision-language models are usable?
- Can the NPU handle useful desktop screenshot understanding?
- Is OCR plus a small reasoning model more reliable?
- Which Linux distribution provides the best HDMI input support?
- How much RAM is required for acceptable local inference?
- Which ESP32-S3 board best supports USB HID and controls?
- Should the LCD be attached to the Orange Pi or ESP32?
- What is the real bill of materials for each architecture?
- How should PortGeist behave if the AI model crashes?
- Can a completely offline device accomplish useful multi-step tasks?

## Decision

Orange Pi 5 Plus + ESP32-S3 is a priority research candidate.

No final hardware platform has been selected.

The Raspberry Pi 5 + AI HAT+ 2 architecture remains under
consideration until model benchmarks and hardware tests
establish which approach is more suitable.

## References

- Orange Pi: http://www.orangepi.org/
- Rockchip: https://www.rock-chips.com/
- Espressif ESP32-S3: https://www.espressif.com/en/products/socs/esp32-s3
- PortGeist: https://github.com/Straconis/PortGeist
