# AXIOM — MONARCH SYSTEM · PRD

## Vision
Cinematic personal-development RPG operating system. Real-world action → XP → stats → skills → bosses → level → rank. 104 levels across 9 ranks (E → SPARK ... 104 → SUPREME MONARCH).

## User choices (2026-02-11)
- AI Architect: **GPT 5.6 Terra** via Emergent Universal Key
- Auth: **JWT email/password**
- 3D: **Cinematic R3F** (Command Center + Auth ambient scenes)
- Sound: **ON by default**, toggle in HUD
- Scope: 6 deep screens + 8 elegant placeholders

## Architecture
- **Backend** FastAPI + Motor + MongoDB. Deterministic XP/level/rank engine (`server.py`). JWT via `pyjwt`.
- **AI** `emergentintegrations.LlmChat` → `openai/gpt-5.6-terra`, streaming SSE (`X-Accel-Buffering: no`).
- **Frontend** React 19 + React Three Fiber 9 + Framer Motion + Tailwind + Shadcn + Sonner. Sound via WebAudio synthesized SFX (no assets required).
- **Design** Michroma display + Rajdhani heading + JetBrains Mono data. Obsidian black / cyan #00F0FF / amber #FFB000 / crimson #FF2A2A. Clip-tech cut corners, corner brackets, scanlines, segmented XP bars.

## Implemented (2026-02-11)
- Auth: register/login/me/settings/name endpoints; players collection with unique email index.
- Quest engine: 10 seeded starter quests per player; 6 kinds (MAIN/SUPPORT/MICRO/CHALLENGE/BOSS/SECRET) × 5 difficulties. Idempotent completion. Trains stats, streaks, credits, domains.
- Boss engine: 9 canonical bosses seeded per player. Damage from linked quests, phases, defeated state.
- Event log: level_up, rank_up, boss_result recorded and shown in HUD.
- Cinematic overlay: quest complete / level up / rank up / boss defeated variants with synthesized SFX.
- AXIOM Architect: streaming SSE from GPT 5.6 Terra with player-state context injected. History persisted.
- 6 deep screens: Command Center (with 3D scene), Daily Operations, Quest Board, Boss Archive, Player Evolution, Architect.
- 8 placeholder screens with elegant "SEALED PROTOCOL" ComingSoon panel.
- Sound toggle in top HUD; ambient drone + UI/completion/level-up/rank-up/boss cues.

## Deferred / Next
- **P0** Skill Matrix visual tree, Adaptive War Room diagnostics.
- **P1** Reality Simulator (trajectory projection using Architect tool-calls), Monarch Trials, Campaign engine.
- **P1** Custom quest creation UI, quest editing, failure/expiry cron.
- **P2** Hall of Ascension trophy 3D artifacts, Monarch Sanctum evolving citadel, Codex full manual.
- **P2** Reduced-motion strict mode, mobile 3D fallback, accessibility audit.
- **P2** Achievement/medal engine (currently list-only), Titles unlock rules.

## Test Credentials
See `/app/memory/test_credentials.md`.
