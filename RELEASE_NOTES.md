# AXIOM — Release Notes

## v1.0.0 — Final Release Freeze

AXIOM V1 is frozen. This is the first stable release of the Monarch
Leveling System: a gamified self-development platform with server-authoritative
XP/level/rank progression, quests, bosses, skills, trials, and a cinematic
3D presentation layer.

### Highlights

- **Progression system** — XP, levels (1–104), 9 ranks (E → SUPREME MONARCH),
  8 stats, quests, boss encounters, and Monarch Trials, all calculated and
  validated server-side (`backend/server.py`) with idempotent, duplicate-safe
  completion endpoints.
- **Cinematic presentation** — staged Level-Up (~3.85s) and Rank Ascension
  (~4.4s) sequences with the full official AXIOM art library (ranks,
  Architect states, bosses, quests, medals, achievements, skill domains,
  environments), integrated via a centralized asset registry
  (`services/assets/registry.js`).
- **3D environment** — a shared, route-aware Three.js/React Three Fiber scene
  (`components/3d/AxiomScene.jsx`) with adaptive HIGH/BALANCED/LOW quality
  tiers (device detection + live FPS sampling), adaptive pixel ratio, and
  automatic render-loop pausing on backgrounded tabs.
- **Audio architecture** — 15 named sound hooks (`services/sound.js`) with
  master/SFX volume, mute, autoplay-safe gesture gating, and a file-manifest
  system ready to accept real audio assets later without touching any call
  site.
- **Production architecture** — layered `src/` structure
  (`app/engine/state/components/{common,3d,cinematic}/views/hooks/services/
  config/utils/styles`), 8 thin domain-scoped engine modules over the API
  layer, an additive event-type system, versioned/failure-safe localStorage
  persistence, and a top-level error boundary. Zero circular dependencies.

### Known Limitations (carried forward, not blocking release)

- `event.new_achievements` is read by the achievement toaster but not yet
  populated by the backend — achievement/medal/artifact unlock toasts are
  wired and ready but currently dormant pending a server-side change.
- No user-facing quality-tier toggle; quality adaptation is automatic only.
- Automated test coverage is currently empty (`frontend/src/tests/`) —
  see `tests/README.md` for suggested first tests.

### Verified for this release

- Production build (`npm run build`) — clean, zero errors
- All 16 navigation links resolve to real routes
- All 88 unique asset registry references resolve to real files on disk
- No hardcoded secrets/API keys; all credentials load from environment
  variables server-side
- No development-only debug code (`console.log`, `debugger`, dev bypass
  flags) present in shipped source
- Zero circular module dependencies
- Backend compiles clean (`python3 -m py_compile`)

---

*Previous version: 0.1.0 (pre-release/development)*
