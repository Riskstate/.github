## RiskState — decision and risk infrastructure for crypto capital

Three independent engines, each answering a different question before a trade is placed.
Deterministic, hash-audited, and callable by a human or an agent.

**See them live, no key required:** [app.riskstate.ai](https://app.riskstate.ai) — intelligence, [market structure](https://app.riskstate.ai/structure), [playbooks](https://app.riskstate.ai/playbooks) and the [risk governor](https://app.riskstate.ai/risk-gate) for BTC/USD and ETH/USD.

| Engine | The question it answers | Endpoint | Auth |
|---|---|---|---|
| [**Risk Engine**](https://github.com/Riskstate/risk-engine) | *How much exposure is allowed?* | `POST /v1/risk-state` | API key |
| [**Market Structure Engine**](https://github.com/Riskstate/market-structure-engine) | *Are we near a structural inflection?* | `POST /v1/market-structure` | API key |
| [**Trading Playbook Engine**](https://github.com/Riskstate/trading-playbook-engine) | *Is a setup live right now?* | `GET /api/playbook-data` | public |

BTC/USD and ETH/USD. Spot, perpetual futures, and DeFi borrowing aware.
Not a signal. Not an oracle. A policy engine that governs size.

```
POST /v1/risk-state { "asset": "BTC" }

→ max_size: 35%  ·  leverage_max: 1.5x  ·  blocked: ["LEVERAGE_GT_2X"]
```

---

### Ask Claude or ChatGPT directly

A keyless remote MCP server — nothing to install:

```
https://api.riskstate.ai/mcp
```

Add it as a custom connector in **[Claude](https://riskstate.ai/connect/claude)** or **[ChatGPT](https://riskstate.ai/connect/chatgpt)**, then ask what the risk state of BTC is.
On the official MCP registry as `ai.riskstate/mcp`.

### Or build on it

```bash
npm  install @riskstate/market-structure-engine   # or @riskstate/trading-playbook-engine
pip  install riskstate-market-structure           # or riskstate-trading-playbook
npx  @riskstate/mcp-server                        # stdio MCP server
```

---

### Repositories

| Repo | What's inside |
|---|---|
| [`risk-engine`](https://github.com/Riskstate/risk-engine) | REST docs for `/v1/risk-state` + the `SKILL.md` agent-discovery file |
| [`market-structure-engine`](https://github.com/Riskstate/market-structure-engine) | Typed TS + Python client, response types, examples, offline fixture |
| [`trading-playbook-engine`](https://github.com/Riskstate/trading-playbook-engine) | The same integration kit for the playbook registry |
| [`mcp`](https://github.com/Riskstate/mcp) | MCP server — published as `@riskstate/mcp-server` |
| [`agent-setups`](https://github.com/Riskstate/agent-setups) | Reference architectures wiring autonomous agents to external risk governance |

The engines themselves are closed-source. These repos are the integration surface: clients, types, docs and examples.

### Free, no key required

[App](https://app.riskstate.ai) · [Market Structure](https://app.riskstate.ai/structure) · [Playbooks](https://app.riskstate.ai/playbooks) · [Risk Governor](https://app.riskstate.ai/risk-gate)

Running a desk or a fund? The `/v2` endpoints aggregate risk across a whole book — portfolio limits, stress scenarios, expected shortfall, audit trail. See [institutional docs](https://riskstate.ai/docs/institutional).

---

<sub><a href="https://riskstate.ai">riskstate.ai</a> · <a href="https://riskstate.ai/docs">Docs</a> · <a href="https://riskstate.ai/stack">The stack</a> · <a href="https://x.com/riskstate_ai">@riskstate_ai</a> · API v1.4.0 · Risk governance data, not financial advice.</sub>
