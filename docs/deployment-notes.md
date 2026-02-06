# Deployment & Debugging Notes

This document captures real-world deployment and debugging steps
encountered while running a local AI agent orchestration stack
(OpenClaw) on macOS (Apple Silicon).

Environment:
- macOS 26.x (arm64)
- Node 22.x
- LaunchAgent background service
- Anthropic model integration


Deployment & Debugging Notes
1️⃣ Gateway Token Mismatch Resolution

Observed error:

unauthorized: gateway token mismatch


Root cause:
CLI was not using the same gateway token as the service.

Fix:
Exported token as environment variable:

export OPENCLAW_GATEWAY_TOKEN=<token>


Reloaded shell and verified:

echo $OPENCLAW_GATEWAY_TOKEN
openclaw status

2️⃣ LaunchAgent Service Management

Gateway runs via macOS LaunchAgent:

openclaw gateway restart
openclaw gateway stop
launchctl list | grep openclaw


Ensures persistence across reboots.

3️⃣ Anthropic API Authentication Setup

Configured agent-level auth profile:

~/.openclaw/agents/main/agent/auth-profiles.json


Resolved:

No API key found for provider "anthropic"

4️⃣ Local-Only Security Model

Bound to 127.0.0.1

No external exposure

No hardcoded secrets in repository

---

## Lessons Learned

- Local services must share consistent auth tokens across CLI and background agents.
- macOS LaunchAgent services require full restarts when environment variables change.
- AI agent frameworks enforce strict provider-level API authentication.
- Debugging distributed local systems requires checking both service logs and CLI config.

---
