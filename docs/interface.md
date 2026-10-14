# Human interface

## Physical controls

- **YES:** approve the currently displayed binary question only.
- **NO:** decline the currently displayed binary question only.
- **STOP/PAUSE:** immediately inhibit new HID actions; ideally release held keys/buttons.
- **LCD:** show task, status, recent activity, pending questions, and outcome summaries.

## Status indicators (proposed)

- **Green:** normal operation.
- **Yellow:** yes/no response requested.
- **Red:** complex response needed through the web interface.
- **Blinking red (candidate):** error or safety stop; distinguish from ordinary questions.

## Web interface

Local access for objective entry, complex responses, task status, action history, approvals, model selection (Onboard / LAN / Automatic), and safe pause/resume. Touchscreen text input is a possible future enhancement, not a requirement.

Question IDs and approval context must be tied to a specific action so a delayed button press cannot authorize a different operation.
