# Hardware research

## Candidate components (not selected)

- Raspberry Pi 5, potentially 16 GB RAM.
- Optional AI HAT+ 2 for supported accelerated models, pending real benchmarks.
- UVC-compatible USB HDMI capture device.
- USB HID-capable microcontroller, suitable USB gadget-capable board, or established KVM hardware.
- 3.5â€“5-inch LCD, potentially touchscreen.
- YES, NO, and dedicated STOP/PAUSE controls.
- Green, yellow, and red indicators; cooling and reliable power.

## Important constraints

- Raspberry Pi HDMI connectors are **outputs**, not video inputs.
- USB gadget/HID support differs by Pi model and physical USB controller; do not assume a Pi 5 USB-A port can act as a USB keyboard.
- Video capture format, latency, USB bandwidth, resolution, BIOS compatibility, and HDCP restrictions require testing.
- Accelerator TOPS ratings do not establish screenshot understanding or agent reliability.
- PCIe resource sharing, display wiring, power draw, heat, and enclosure layout require evaluation.
- Virtual boot-media emulation and target power control are potential future extensions.
