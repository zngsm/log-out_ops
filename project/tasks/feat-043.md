# feat-043 Implement 2 Sound/Audio Atmosphere Enhancements (EMERGENCY LOCKDOWN siren loop integration, gameplay phase dark tension ambient BGM auto-play & mute/volume/pause integration, and audio tone matching)

## Status

- status: done
- type: feat
- priority: 60
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-043 integrate emergency lockdown siren loop and gameplay phase dark tension ambient BGM with audio tone matching`

## Goal

Implement two sound/audio atmosphere enhancement requirements during emergency lockdown cutscenes and gameplay puzzle phases with perfect oscillator tone matching in `audioSystem.ts`.

## Scope

- 1. **EMERGENCY LOCKDOWN Siren Loop Integration**: Continuously play the two-tone repeating emergency siren loop during emergency lockdown cutscenes/presentations (`appPhase === "opening"` and the rebooting emergency lockdown sequence).
- 2. **Gameplay Phase Dark Tension Ambient BGM Integration**: Auto-play the Web Audio API-based dark tension ambient BGM (suspense low pad & pulsation) during the main log exploration and ECHO evidence submission puzzle stage (`appPhase === "gameplay"`), seamlessly integrated with mute (`audioMuted`), volume, and pause (`isPaused`) states.
- 3. **Audio Tone Matching**: Design the ambient BGM and emergency siren synthesized audio to match and harmonize perfectly with existing `audioSystem.ts` Web Audio oscillator tones without timbre dissonance.

## Dependencies

- before: `feat-018`, `feat-039`, `feat-041`, `feat-042`
- after: human visual review

## Acceptance Criteria

- [x] Emergency siren loop (two-tone repeating emergency siren loop) plays continuously during emergency lockdown cutscenes (`appPhase === "opening"` and rebooting emergency sequence).
- [x] Dark tension ambient BGM (suspense low pad & pulsation) automatically plays during main log exploration and ECHO evidence submission phase (`appPhase === "gameplay"`).
- [x] The dark tension ambient BGM correctly reacts to audio mute (`audioMuted`), volume adjustment, and pause modal (`isPaused`) states.
- [x] Synthesized audio and BGM tones naturally match existing `audioSystem.ts` Web Audio oscillator tones without audio dissonance.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-10 | pm-agent | todo -> in_progress | Defined task for 2 sound/audio atmosphere enhancements (feat-043) |
| 2026-08-10 | dev-agent | todo -> in_progress | Started implementation of emergency siren loop & gameplay dark tension ambient BGM |
| 2026-08-10 | dev-agent | in_progress -> done | Implemented emergency siren loop and dark tension BGM with Web Audio API, verified audio controls & tone matching |
