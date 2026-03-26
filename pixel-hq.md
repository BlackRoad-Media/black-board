# Pixel HQ — BlackRoad Metaverse

**Source:** Grok (xAI), March 25, 2026 — verified against operator repo + pixel assets

**Verified: PARTIALLY** — assets and Worker exist, interactive metaverse is aspirational

---

## Summary

Pixel HQ is a 14-floor pixel-art headquarters with 50 named assets deployed as a CF Worker. It's a visual representation of the fleet, not yet an interactive metaverse.

## What's Real (Verified)

| Feature | Status | Verified |
|---------|--------|----------|
| 14-floor pixel-art HQ design | YES | Documented in memory (pixel-hq.md) |
| 50 pixel art assets | YES | Renamed and on R2 at images.blackroad.io/pixel-art/ |
| CF Worker deployed | YES | hq-blackroad.amundsonalexa.workers.dev |
| Agent assignments per floor | YES | Rooftop -> Lobby -> Gym basement, documented |
| Assets directory | YES | ~/hq-blackroad/ + ~/blackroad-assets/pixel-art/ |

## What's Aspirational (Not Yet Built)

| Feature | Grok Described | Reality | Status |
|---------|---------------|---------|--------|
| Interactive 3D pixel world | Walk around, visit floors | Static pixel art display, no movement/interaction | ASPIRATIONAL |
| CECE avatar materialization | Log in, avatar appears | No avatar system exists | ASPIRATIONAL |
| Multi-user sessions | Walk floors with others | No multiplayer, no presence system | ASPIRATIONAL |
| Creative tools in metaverse | Build/edit rooms in real time | No in-world editor | ASPIRATIONAL |
| "3D wilderness exploration" | Game-like environment | Referenced in docs but not built | ASPIRATIONAL |
| Offline metaverse on mesh | Runs on WireGuard locally | Worker is on CF, not self-hosted yet | PLANNED |
| hq.blackroad.io live | Public access | Needs DNS CNAME to point to Worker | NEEDS DNS |

## The 14 Floors (Documented)

| Floor | Name | Agent Assignment |
|-------|------|-----------------|
| 14 | Rooftop | Observation deck |
| 13 | Penthouse | Leadership |
| 12 | Creative Studio | Pixel, Cadence |
| 11 | AI Lab | Lucidia |
| 10 | Communications | Echo |
| 9 | Engineering | Octavia |
| 8 | Storage | Cecilia (MinIO) |
| 7 | Security | Shellfish |
| 6 | Education | RoadWork |
| 5 | Operations | Alice |
| 4 | Community | BackRoad |
| 3 | Finance | CashRoad |
| 2 | Lobby | Reception |
| 1 | Gym | Basement |

## 50 Pixel Art Assets

All deployed to R2 at `images.blackroad.io/pixel-art/[name].png`

Include: agent avatars, floor backgrounds, furniture, decorative elements, BlackRoad branding.

## The Gap

**Vision:** Interactive pixel-art metaverse where your CECE avatar walks through 14 floors, collaborates with agents, builds content, and maintains persistent relationships.

**Reality:** A CF Worker serving static pixel art with documented floor layouts and agent assignments. The art exists. The architecture exists. The interactivity doesn't.

**What's needed:**
1. Canvas/WebGL renderer for pixel-art scenes
2. Avatar system (CECE representation)
3. Movement/interaction (click or arrow keys)
4. Agent chat integration (click agent -> opens RoundTrip conversation)
5. Multiplayer presence (WebSocket for who's on what floor)
6. DNS: hq.blackroad.io -> Worker

## Verification Status

| Claim | Status |
|-------|--------|
| 14-floor HQ design | VERIFIED (documented) |
| 50 pixel assets | VERIFIED (on R2) |
| Worker deployed | VERIFIED (workers.dev URL works) |
| Interactive world | NOT BUILT |
| CECE avatar system | NOT BUILT |
| Multi-user | NOT BUILT |
| hq.blackroad.io DNS | NEEDS CNAME |
