# Local AI Agent Orchestration

Self-hosted AI agent runtime with secure gateway authentication, Telegram channel routing, and Anthropic integration on macOS.

---

## 🧠 Overview

This project documents my hands-on deployment and configuration of a locally hosted AI agent runtime using OpenClaw.

The setup includes:

- Secure WebSocket gateway with token-based authentication
- Anthropic LLM provider integration
- Agent auth profile configuration
- Telegram channel binding
- macOS LaunchAgent service lifecycle management
- Environment variable injection via zsh

This project was executed on Apple Silicon (macOS ARM64).

---

## 🏗 Architecture

User (Telegram / CLI)
        ↓
WebSocket Gateway (localhost:18789)
        ↓
Auth Layer (token validation)
        ↓
Agent Runtime
        ↓
Anthropic API (Claude Opus)

---

## 🔐 Security Considerations

- Gateway token stored via environment variable
- LaunchAgent process isolation
- Localhost-only WebSocket binding
- No secrets committed to repository

---

## ⚙️ Key Technical Learnings

- Debugging token mismatch errors between gateway.auth.token and remote clients
- Managing macOS LaunchAgents for persistent services
- Handling provider-level API key authentication failures
- Channel routing and binding configuration
- Runtime diagnostics via CLI and log inspection

---

## 🛠 Tech Stack

- macOS (ARM64)
- Node.js 22
- WebSocket Gateway
- Anthropic Claude Opus 4.5
- Telegram Bot API
- Zsh environment configuration

---

## 📌 Why This Matters

Understanding agent orchestration, authentication layers, and runtime lifecycle management is critical for:

- AI infrastructure roles
- Data Engineering automation
- Platform engineering
- LLM operations

This project reflects real debugging, real configuration, and real systems thinking.
