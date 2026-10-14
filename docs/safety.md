# Safety, authorization, and privacy

- Operate only computers the user owns or is authorized to administer.
- Require explicit approval for destructive, irreversible, or security-sensitive operations (e.g. formatting disks, changing boot records, altering credentials, firmware changes).
- Use a physical stop mechanism independent of the model; bound each action and release held HID inputs on interruption.
- Preserve personal files by default; disclose uncertainty and potential data-loss risks before changes.
- Avoid unbounded retries, loops, or blind clicks. Escalate when the screen cannot be interpreted reliably.
- Keep screenshots, logs, and task data local by default, with configurable retention and protection for secrets visible on screen.
- Authenticate the web interface, restrict LAN access, and avoid exposing it directly to the public internet.
- Do not bypass passwords, encryption, access restrictions, or other security controls.
- Record what was attempted and distinguish verified success from inferred success.
