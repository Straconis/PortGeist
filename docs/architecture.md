# Conceptual architecture

```text
User / Web UI / LCD + Buttons
             |
       Task supervisor
   (goals, approvals, journal)
             |
    AI inference interface <----> Onboard model or LAN model
             |
   Observe -> Plan -> Act -> Verify
        |                 |
  HDMI capture       USB HID output
        |                 |
        +---- Target PC --+
```

## Components

- **Capture adapter:** obtains frames from the target's video output.
- **Perception:** interprets frames, text, dialogs, and UI controls.
- **Planner:** maintains the objective, current hypothesis, and next proposed action.
- **Action executor:** translates approved actions into keyboard/mouse HID commands.
- **Verifier:** observes subsequent frames and compares them to expected results.
- **Supervisor:** enforces permissions, risk policies, budgets, retries, and stop conditions.
- **Journal:** locally records decisions, observations, approvals, and outcomes.

All model-specific inference details should sit behind a replaceable interface. Loss of the LAN server must not leave keys held down or actions executing unattended.
