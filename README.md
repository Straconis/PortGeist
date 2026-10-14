# PortGeist

**Autonomous AI KVM**  
*Plug in. Set a goal. Let the ghost work.*

> **Status: Concept and documentation only.** No implementation exists. Hardware and model choices are provisional.

PortGeist is a proposed portable, local-first autonomous computer operator. It observes an external computer through HDMI capture, interacts using USB keyboard/mouse emulation, and works toward a user-defined objective. It does not require an agent installed on the target computer. Repairing a nonbooting PC is one use case, not the limit of the concept.

## Intended interaction

1. Connect PortGeist to the target's video output and a USB input port.
2. Give it an objective through its local web interface.
3. Its AI observes the screen, reasons, acts, and verifies the outcome.
4. An onboard LCD shows status, progress, and questions.
5. Physical **YES** and **NO** buttons answer binary prompts; complex questions can be reviewed on the LCD and answered through the web interface.
6. A physical **STOP/PAUSE** control interrupts automation immediately.

## Design principles

- **Offline-first:** no mandatory internet connection, paid APIs, or per-token costs.
- **Flexible inference:** onboard Pi model, optional user-owned LAN inference server, or automatic selection with safe fallback.
- **Out-of-band control:** the target OS need not be healthy or running, although video output and usable input support are required.
- **Human authority:** destructive and high-risk actions require explicit approval.
- **Transparent operation:** keep local action logs, screenshots where appropriate, checkpoints, and outcomes.
- **Hardware independence:** separate KVM I/O from AI and orchestration so implementations can evolve.

## Proposed hardware

Raspberry Pi 5 (16 GB is a research candidate), USB HDMI capture adapter, USB HID-capable controller or proven KVM hardware, 3.5â€“5-inch LCD, YES/NO/STOP controls, green/yellow/red status LEDs, cooling, and power supply. The Raspberry Pi AI HAT+ 2 is a candidate **only if** compatible models and practical performance are demonstrated.

## Documentation

- [Vision and use cases](docs/vision.md)
- [Architecture](docs/architecture.md)
- [Hardware research](docs/hardware.md)
- [Agent and inference](docs/agent.md)
- [Human interface](docs/interface.md)
- [Safety and privacy](docs/safety.md)
- [Feasibility questions](docs/feasibility.md)
- [Roadmap](docs/roadmap.md)

## Project scope

This repository records ideas, assumptions, requirements, and research questions. It is **not** a working product, build guide, or claim of validated feasibility. PortGeist is a working name; commercial name/trademark clearance has not been completed.
