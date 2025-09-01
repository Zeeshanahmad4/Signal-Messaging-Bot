# Signal Messaging Bot

> Self-hosted bot to send **1-to-1 Signal messages in bulk** with drip pacing, personalization, retries, and opt-outs.

---

## Introduction
A production-ready starter for a Signal bulk-messaging **bot**, not a hosted service.  
Feed a template + recipients file, and the bot handles pacing, personalization, retries, and compliance basics.

---

<img width="1536" height="500" alt="Image" src="https://github.com/user-attachments/assets/4f938d1c-7d78-4df2-84f9-6ea88185930e" />


## Table of content
- [Overview](#overview)
- [Features](#features)
- [Workflow](#workflow)
- [FAQ](#faq)
- [Contact us](#contact-us)
- [License](#license)
- [Footer image](#footer-image)

---

## Overview
Send personalized, individual Signal messages at scale with safe drip pacing and retries. This repo ships a CLI-driven workflow, a pluggable transport layer (starting with `signal-cli`), templating, suppression handling, and structured logs for easy review and re-runs.

---

## Features

| Feature | What it does | Notes |
|---|---|---|
| Bulk 1-to-1 sending | Queues and sends individual Signal messages | Avoids group blasts/spammy patterns |
| Drip rate-limit + jitter | Controls msgs/min with random delays | Human-like timing; configurable |
| Personalization | Replaces `{{placeholders}}` from recipient fields | Works with any CSV headers you provide |
| Dry-run mode | Simulates sends without delivering | Safe validation before going live |
| Retries & backoff | Automatic re-send on transient failures | Max attempts + exponential backoff |
| Opt-out handling | Suppression list + STOP keywords | Honor consent and local policy |
| Template packs | Reusable message templates (`/templates`) | Plain text; easy to version |
| Pluggable transport | Adapter for `signal-cli`; add more providers | Swap without changing business logic |
| CLI commands | `send-bulk`, `send-test`, `status` | Minimal learning curve |
| Logs & reports | JSON logs of results/failures | Idempotent re-runs and audits |
| Delivery receipts (Roadmap) | Read/send status tracking | Provider dependent |
| Media attachments (Roadmap) | Send images/files | Extends transport interface |
| Scheduler/Web UI (Roadmap) | Timed campaigns + dashboard | Optional service layer |


---

## Workflow
1) **Prepare**: Add recipients file in `./config/` and your message in `./templates/`.  
2) **Configure**: Copy `.env.example` → `.env` and set `SIGNAL_NUMBER`, `RATE_LIMIT_PER_MIN`, `RANDOM_JITTER_MS`, `STOP_KEYWORDS`.  
3) **Run**:
   - Dry run: `send-bulk --csv ./config/recipients.csv --tpl ./templates/promo.txt --dry-run`
   - Live: `send-bulk --csv ./config/recipients.csv --tpl ./templates/promo.txt`
   - Status: `status`
4) **Review**: Check `./logs/*.json` for outcomes and retries.

---
<img width="1536" height="500" alt="Image" src="https://github.com/user-attachments/assets/d7b6ab0f-c323-4685-adba-89854b008aa8" />


---

## FAQ

Q: **Do I need a Signal account?**  
A: Yes. Configure a valid Signal account (e.g., via `signal-cli`).

Q: **How fast can it send?**  
A: You control it via `RATE_LIMIT_PER_MIN` plus random jitter. Start conservative.

Q: **Can it auto-handle STOP replies?**  
A: MVP supports suppression via keywords and lists. Inbox hooks for live parsing are on the roadmap.

Q: **Can I use a provider other than `signal-cli`?**  
A: Yes—add an adapter under `/src/transport/` that matches the interface.

---

## Contact us
- Website: https://www.bitbash.dev/ <br>
- Discord: https://discord.gg/zX7frTbx  <br>
- Telegram: https://t.me/devpilot1  <br>

---

## License
Distributed under the MIT License. See LICENSE for more information. 

---
<img width="1536" height="300" alt="Image" src="https://github.com/user-attachments/assets/e1defd1e-4395-4c9c-8b82-7ea0111db522" />
