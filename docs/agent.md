# Agent and local inference

## Core loop

1. Observe a screen frame and current task state.
2. Interpret the UI and formulate a hypothesis or next action.
3. Assess action risk and obtain required approval.
4. Send a bounded keyboard/mouse action.
5. Observe again, verify the result, update the journal, and repeat.

## Inference modes

- **Onboard:** lightweight model runs entirely on PortGeist.
- **LAN-assisted:** inference runs on another user-owned local machine, without cloud APIs.
- **Automatic:** select an available capable local backend; if unavailable, safely pause or fall back only when the onboard model can handle the task.

Potential software stacks to research include llama.cpp and Ollama; model and accelerator compatibility are unverified. Candidate approaches include small vision-language models, OCR plus a reasoning model, and structured action generation. Benchmark on actual BIOS, Windows, Linux, and recovery screenshots before committing.

## Reliability requirements

Maintain bounded action sequences, confidence/uncertainty handling, retry limits, progress checkpoints, clear task-completion criteria, and an explicit escalation path. Never interpret a model's assertion of success as proof without observing the target state.
