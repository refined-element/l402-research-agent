---
created: 2026-05-25
project: lightning-enable
tags: [l402, agent-commerce, prompt, reproducible]
---

# The prompt (reproducible)

Paste this into an AI agent connected to the **Lightning Enable MCP server** with a funded Lightning wallet. It will discover the data sources, pay for them per call over L402, and produce the paper — no API keys, no accounts.

> I want to write a blog post about the yen carry trade unwinding, well-researched and with cited sources. Using up to **25 sats** from my wallet, discover the **FRED economic-data API on agent-commerce.store** (via the `discover_api` tool on the Lightning Enable MCP server) and pull the data you need — USD/JPY, the Nikkei 225, the VIX, and the US 10-year Treasury yield — to support the analysis with real figures, charts, and proper citations. Note: each L402 payment is valid for ~60 minutes for that **same endpoint**, so reuse the token for repeat calls to the same series; **different series are different endpoints and each needs its own payment**. Then use the **tech-innovation-journalist** agent to write the paper, and distinguish the August 2024 carry unwind from any later shocks the data reveals.

## What actually happened when this ran (2026-05-25)
- `discover_api` surfaced FRED (and the rest of agent-commerce.store) by category.
- 4 paid L402 calls, one per series: `DEXJPUS`, `NIKKEI225`, `VIXCLS`, `DGS10`.
- **5 sats each → 20 sats total (~US$0.01)**; wallet 2,054 → 2,034 sats (confirmed).
- 0 API keys, 0 accounts, 0 human approvals.
- Verified token behavior: L402 macaroon is **path-scoped** with a **~60-min expiry** — reusable for the *same* endpoint within the window, not across different endpoints (FRED puts the series in the path, `/series/{id}/data`, so each series = its own payment).
- The real data forced an accuracy correction the agent would otherwise miss: the window's most extreme Nikkei/VIX prints were the **April 2025 tariff shock**, not the Aug 2024 carry unwind.
