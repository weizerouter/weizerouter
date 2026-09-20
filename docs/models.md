# WeizeRouter Model Catalog & Specifications

WeizeRouter provides unified OpenAI-compatible access to a curated portfolio of state-of-the-art Large Language Models.

---

## 🌐 Regular Ecosystem Models

Available to all active API key holders with regular token balance. Token consumption is calculated dynamically based on raw prompt & completion tokens multiplied by the official model multiplier.

### Flagship Coding & Large Context

| Model Identifier | Context Window | Best For | Multiplier |
| :--- | :---: | :--- | :---: |
| `wz/muse-spark-1.3-contributor` | **1,000,000 Tokens** | ♾️ Large-repo refactoring, whole-codebase AST analysis, and multimodal processing. | `×2.3` |
| `wz/gemini-3.8-flash-high` | 128,000 Tokens | ⚡ Primary IDE coding workhorse (Cursor, Cline, Roo Code). Ultra-low TTFT. | `×2.3` |
| `wz/gemini-3.8-flash` | 128,000 Tokens | 🚀 Lightweight chat, fast autocomplete, and low-latency agent loops. | `×1.6` |
| `wz/gemini-3.7-flash` | 128,000 Tokens | ⚖️ Stable, balanced generation with strong instruction-following capabilities. | `×2.0` |

### Reasoning & Technical Problem Solving

| Model Identifier | Context Window | Best For | Multiplier |
| :--- | :---: | :--- | :---: |
| `wz/grok-4.5` | 128,000 Tokens | 🧠 Objective engineering analysis, rapid debugging, and system scripting. | `×3.5` |
| `wz/grok-4.6` | 128,000 Tokens | 🔬 Deep multi-step reasoning, mathematical proofs, and architectural design. | `×5.0` |
| `wz/glm-5.3-flash` | 128,000 Tokens | ⚡ High-speed agentic execution, structured data extraction, and tool calling. | `×1.5` |
| `wz/qwen-3.8-max` | 128,000 Tokens | 📐 High-precision polyglot programming and complex algorithms. | `×3.5` |
| `wz/deepseek-v4.1-flash` | 128,000 Tokens | 💡 Algorithmic efficiency, logic puzzle breakdown, and concise synthesis. | `×2.5` |
| `wz/kimi-k3` | 128,000 Tokens | 📚 Long document synthesis, technical writing, and structured summaries. | `×2.0` |

---

## 👑 Weize Premium VIP Models

Exclusive frontier tier running on dedicated high-performance clusters with **500 RPM** rate limits. Requires an active Weize Premium wallet.

| Model Identifier | Backend Engine | Strengths & Capabilities | Multiplier |
| :--- | :--- | :--- | :---: |
| `cx/gpt-6-astra` | ChatGPT Team Frontier | Sovereign-tier software architecture and complex multi-file engineering. | `×15` |
| `cx/gpt-5.6-sol` | Codex Multi-Workspace | High-accuracy code generation, deep refactoring, and AST manipulation. | `×10` |
| `cx/gpt-5.6-terra` | Codex Multi-Workspace | High-throughput system programming and compiler optimization. | `×8` |
| `cx/gpt-5.6-luna` | Codex Multi-Workspace | Ultra-fast frontier coding with low latency and high precision. | `×4` |
| `ag/claude-opus-4-6-thinking` | Antigravity VIP | Deep philosophical depth, formal verification, and subtle edge-case detection. | `×7` |
| `ag/claude-sonnet-4-6` | Antigravity VIP | Balanced frontier coding, API design, and rapid technical documentation. | `×5` |

---

## ⚙️ How Billing Multipliers Work

When a request is processed, the gateway debits the user's wallet using the exact formula:

$$\text{Debit Tokens} = (\text{Input Tokens} + \text{Output Tokens}) \times \text{Multiplier}$$

- **100% Saldo Permanen:** Tokens do not expire over time.
- **No Hidden Fees:** You are only debited when upstream answers with `HTTP 200 OK`. Failed requests are never debited.
