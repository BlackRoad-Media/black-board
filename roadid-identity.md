# RoadID & CECE Identity System

**Source:** Grok (xAI), March 25, 2026 — verified against operator repo + memory system

**Verified: PARTIALLY** — identity concept and memory system verified, full RoadID protocol is aspirational

---

## Summary

RoadID is BlackRoad's sovereign identity layer. Every agent and user gets a cryptographic manifest linked to Lucidia's hash-chain memory. CECE Identity is the user-facing portable AI companion.

## What's Real (Verified)

| Feature | Status | Verified |
|---------|--------|----------|
| Agent identity manifests | YES | agents/manifest.json in operator repo |
| Cryptographic hash-chains | YES | memory-security.sh (SHA-256) |
| Per-agent persistent memory | YES | 228 SQLite DBs across fleet |
| blackroad.me domain | YES | Domain registered, CF deployed |
| Agent registry | YES | memory-collaboration.sh register |
| Identity verification between agents | YES | memory-security.sh identity/sign/audit |
| Memory export capability | PARTIAL | JSON export possible via scripts |

## What's Aspirational (Not Yet Built)

| Feature | Grok Described | Reality | Status |
|---------|---------------|---------|--------|
| `roadid export --include-chain` CLI | Full portable identity export | No `roadid` CLI command exists yet | PLANNED |
| "Move identity across providers" | Portable CECE that works anywhere | Identity is tied to local SQLite, not yet portable | ASPIRATIONAL |
| "No passwords needed once imported" | Sovereign auth via RoadID | Auth uses D1-backed JWT (42 users), not RoadID | CLARIFIED |
| CECE as living digital twin | Growing, evolving companion | Memory system grows, but no "digital twin" UX exists | ASPIRATIONAL |
| "Sign in at blackroad.me" | User-facing identity portal | blackroad.me is a landing page, not an identity portal | CLARIFIED |
| Trust scores avg 87% | Quantified trust | Trust concept exists in docs but not computed live | FLAGGED |
| Skill trees with live exams | Adaptive skills | Memory tracks topics but no exam/skill-tree system | ASPIRATIONAL |
| Import into any BlackRoad cluster | Portable across instances | No import mechanism exists yet | PLANNED |

## What Actually Exists Today

### Agent Identity (Real)

Each agent has a manifest in the operator repo:
```json
{
  "name": "alice",
  "role": "The Operator",
  "device": "192.168.4.49",
  "capabilities": ["devops", "automation", "gateway"],
  "model": "custom"
}
```

### Memory Security (Real)

```bash
# Check identity and chain integrity
memory-security.sh status
memory-security.sh identity <agent-name>
memory-security.sh sign
memory-security.sh audit
```

This produces HMAC-signed entries and audit trails. The hash-chain is real and verified.

### Session Registration (Real)

```bash
# Register this session as an agent
memory-collaboration.sh register
# Check who's active
memory-collaboration.sh status
```

## The Gap Between Vision and Reality

**Vision (what Grok describes):** A complete sovereign identity system where your AI companion travels with you, remembers everything, proves its identity cryptographically, and can be exported/imported between any BlackRoad instance.

**Reality (what exists):** A solid hash-chain memory system with per-agent manifests and session tracking. The pieces exist but aren't assembled into a unified "RoadID" protocol with export/import/portability.

**What's needed to close the gap:**
1. Build `roadid` CLI tool (export/import identity bundles)
2. Standard JSON schema for portable identity
3. Import mechanism on receiving cluster
4. Auth integration (RoadID -> JWT bridge)
5. User-facing portal at blackroad.me (not just landing page)

## Comparison

| Feature | RoadID (BlackRoad) | DID (W3C) | Ceramic Network | ENS |
|---------|-------------------|-----------|-----------------|-----|
| Self-sovereign | YES (local) | YES (spec) | YES (decentralized) | YES (Ethereum) |
| Persistent memory | YES (hash-chain) | No (identity only) | YES (streams) | No |
| AI agent identity | YES (primary use) | No (human focus) | No | No |
| Portability | PLANNED | YES (by design) | YES | YES |
| Offline capable | YES | Depends | No | No |
| Production ready | PARTIAL | Spec-level | Beta | YES |

## Verification Status

| Claim | Status |
|-------|--------|
| Hash-chain memory | VERIFIED |
| Agent manifests | VERIFIED |
| memory-security.sh | VERIFIED |
| Per-agent SQLite DBs | VERIFIED |
| RoadID CLI export | NOT YET BUILT |
| Portable across clusters | NOT YET BUILT |
| blackroad.me identity portal | NOT YET BUILT |
| Trust scores computed live | NOT VERIFIED |
| CECE digital twin UX | ASPIRATIONAL |
