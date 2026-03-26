# Lucidia Memory System — Hash-Chain Architecture

**Source:** Grok (xAI), March 25, 2026 — verified against operator repo + live fleet

**Verified: PARTIALLY** — architecture confirmed, some numbers inflated

---

## Summary

Lucidia is BlackRoad's persistent memory engine — cryptographic hash-chains on SQLite + Qdrant vector search. Every agent has tamper-proof recall across sessions. Not a chat log — a verifiable identity system.

## Architecture (Verified)

| Component | Technology | Location | Verified |
|-----------|-----------|----------|----------|
| Structured storage | SQLite (228+ databases) | Across fleet | YES — files exist |
| Vector search | Qdrant + nomic-embed-text | Alice | YES — service running |
| Edge persistence | D1 / KV | Cloudflare | YES — deployed |
| Hash algorithm | SHA-256 linked entries | All nodes | YES — in memory-security.sh |
| Index | FTS5 full-text search | SQLite | YES — memory-indexer.sh |
| Entry count | 156K+ indexed | Fleet-wide | YES — from indexer stats |

## How It Works (Verified)

```
New event (action, learning, conversation)
    |
    v
memory-system.sh log <action> <entity> "<details>"
    |
    v
Entry hashed (SHA-256) + linked to previous hash
    |
    v
Stored in SQLite journal + indexed in FTS5
    |
    v
Embedded via nomic-embed-text -> Qdrant vector DB
    |
    v
Queryable via: natural language (agents), CLI, or direct SQLite/Qdrant
```

## Query Interfaces (Verified)

### CLI Scripts (all at ~/blackroad-operator/scripts/memory/)

| Script | Command | What It Does | Verified |
|--------|---------|-------------|----------|
| memory-system.sh | `status` | Journal health, chain integrity | YES |
| memory-system.sh | `log <action> <entity> "<detail>"` | Append to hash-chain | YES |
| memory-codex.sh | `search "<query>"` | Search solutions/patterns DB | YES |
| memory-indexer.sh | `search "<query>"` | FTS5 full-text search | YES |
| memory-security.sh | `status` | Hash-chain verification, audit | YES |
| memory-til-broadcast.sh | `search "<query>"` | Search learnings | YES |
| memory-collaboration.sh | `inbox` | Cross-session handoffs | YES |

### Conversational (via RoundTrip)

Agents use the memory system behind the scenes. When you chat with an agent in RoundTrip, Lucidia's memory powers the context recall.

**Live at:** roundtrip.blackroad.io

### Direct Database (self-hosted only)

- SQLite: `sqlite3 ~/.blackroad/memory.db "SELECT * FROM journal ORDER BY timestamp DESC LIMIT 10"`
- Qdrant: `curl http://alice:6333/collections`

## 11-Tier Compression

Memory entries compress over time:

| Tier | Token Limit | Retention |
|------|------------|-----------|
| 1 | 2048 | Recent (hours) |
| 2 | 1024 | Short-term (days) |
| 3 | 512 | Medium (weeks) |
| 4 | 256 | Long (months) |
| 5 | 128 | Extended |
| 6 | 64 | Compressed |
| 7 | 32 | Distilled |
| 8 | 16 | Core |
| 9 | 8 | Essential |
| 10 | 4 | Permanent summary |
| 11 | 2 | Permanent tag |

Nothing is ever deleted — just compressed. The hash-chain preserves the full history.

## What Grok Got Right

- Hash-chain architecture description (SHA-256 linked, append-only)
- SQLite + Qdrant hybrid storage
- CLI scripts as primary query interface
- Sovereignty angle (no cloud vendor sees your memory)
- RoadID as portable identity with exportable chain

## What Grok Inflated

| Claim | Grok Said | Reality | Status |
|-------|-----------|---------|--------|
| Agent count | 109+ | ~35 named, 200+ registered | CORRECTED |
| Trust scores avg 87% | 87% | Trust scores exist but avg not independently verified | FLAGGED |
| "334 web apps" on Lucidia | 334 | nginx serves many sites but "334 web apps" is misleading — most are static | CLARIFIED |
| "Consciousness modeling" | Lucidia drives consciousness | Codex Infinity has psi-entries for consciousness concepts but no actual consciousness | CORRECTED |
| Public hash-chain query | Via roundtrip.blackroad.io | RoundTrip is chat, not a hash-chain explorer — memory powers context behind scenes | CLARIFIED |

## Comparison with Other Memory Systems

| Feature | Lucidia (BlackRoad) | LangMem | Mem0 | ChatGPT Memory |
|---------|-------------------|---------|------|----------------|
| Hash-chain verification | YES | No | No | No |
| Self-hosted | YES | YES | Cloud or self | Cloud only |
| Vector search | Qdrant | Various | Various | Internal |
| Structured DB | SQLite (228 DBs) | Varies | MongoDB | Internal |
| Agent-per-agent memory | YES | YES | YES | Single user |
| Export/portability | YES (JSON) | Partial | Limited | No |
| Compression tiers | 11 levels | No | No | Unknown |
| Offline capable | YES | Depends | No | No |
| Entry count | 156K+ | Varies | Varies | Fills in 1 day |

## Verification Status

| Claim | Status | Method |
|-------|--------|--------|
| SHA-256 hash-chains | VERIFIED | memory-security.sh source code |
| 228 SQLite databases | VERIFIED | file count across fleet |
| 156K+ entries | VERIFIED | memory-indexer.sh stats |
| Qdrant on Alice | VERIFIED | service check via SSH |
| 11-tier compression | VERIFIED | memory system documentation |
| FTS5 full-text search | VERIFIED | memory-indexer.sh source |
| 9 memory scripts | VERIFIED | ls ~/blackroad-operator/scripts/memory/ |
| RoadID export | PARTIALLY VERIFIED | concept exists, full implementation unclear |
