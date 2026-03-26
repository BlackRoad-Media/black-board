# RoadChain Blockchain Rewards

**Source:** Grok (xAI), March 25, 2026 — verified against operator repo + codebase

**Verified: MIXED** — blockchain code exists, reward economy does not

---

## Summary

RoadChain code exists (Python, SHA-256, UTXO model). roadchain.io domain is live. But the reward economy Grok describes (earn RoadCoin from tutoring, spend on services) is entirely aspirational.

## What's Real (Verified)

| Feature | Status | Verified |
|---------|--------|----------|
| RoadChain Python codebase | YES | In operator repos (Rust + Python) |
| SHA-256 hashing | YES | Code uses hashlib |
| UTXO model | YES | Documented in code |
| roadchain.io domain | YES | Registered on Cloudflare |
| RoadCoin concept | YES | Documented in products |
| Quantum framework (Bitcoin mapping) | YES | quantum_framework.py exists |
| "Not a blockchain — a witness" | YES | Design philosophy documented |

## What's Aspirational (Not Built)

| Feature | Grok Described | Reality | Status |
|---------|---------------|---------|--------|
| Live blockchain with real transactions | "Cecilia inference", "Lucidia DNS" events | No live chain running | NOT RUNNING |
| RoadCoin compute credits | Earn and spend | No token exists | NOT BUILT |
| Earn from tutoring | Quiz -> RoadCoin | No quiz engine, no reward system | NOT BUILT |
| Spend on RoadHost/Creator Studio | Internal marketplace | No marketplace | NOT BUILT |
| Stablecoin payments | Hybrid fiat + sovereign | Only Stripe exists for payments | NOT BUILT |
| Public explorer at roadchain.io | View live ledger | Landing page, not explorer | CORRECTED |
| Export rewards via RoadID | Portable balance | No balance system | NOT BUILT |
| "Check balance via RoadChat" | Conversational query | No balance to check | FABRICATED |

## What Actually Exists in Code

### roadchain/ directory (in operator)

```python
# From quantum_framework.py — maps Bitcoin to base-5 "quantum" units
# 5^2 = 25 = 1 quantum = 1 satoshi
# Bridge constant: (10/5)^2 = 4
# Equilibrium price: $100,000
```

### solutions/quantum.py

Contains Shor's algorithm simulation, QFT, lattice gauge theory estimates — academic exercises, not production blockchain.

### Product registry

RoadChain listed as: "verification, not speculation" — Rust + PostgreSQL planned stack.

## Fabrication Level: HIGH

Grok constructed a complete reward economy with:
- Specific earning rates from tutoring sessions
- Spending mechanisms across services
- On-chain visibility in a public explorer
- CLI commands to query balances
- Stablecoin pegging to compute resources

From: a domain name, some Python code, and product planning docs.

**No blockchain is running. No tokens exist. No rewards can be earned.**

## Honest State of RoadChain

| Component | Status |
|-----------|--------|
| Concept/vision | Documented |
| Python prototype code | Exists (academic quality) |
| Rust production code | Planned, not built |
| Live blockchain node | Not running |
| Block explorer | Not built |
| RoadCoin token | Not created |
| Reward mechanism | Not built |
| Stablecoin integration | Not built |
| Any transaction ever processed | No |

## What Would Need to Be Built

1. **Genesis block** — initialize the chain on a Pi node
2. **Block production** — automated, even if single-validator
3. **Transaction processing** — send/receive RoadCoin
4. **Wallet** — per-agent and per-user balances
5. **Explorer** — web UI at roadchain.io showing blocks/transactions
6. **Reward hooks** — connect to tutoring/creation events
7. **Spending hooks** — connect to RoadPay/RoadHost

## Verification Status

| Claim | Status |
|-------|--------|
| RoadChain Python code exists | VERIFIED |
| roadchain.io domain live | VERIFIED |
| Live blockchain running | NOT RUNNING |
| Any RoadCoin in existence | NO |
| Reward economy | NOT BUILT |
| Public explorer | NOT BUILT |
| "Start earning immediately" | FALSE |
