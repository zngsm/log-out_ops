# feat-029 Add First Play Mission Onboarding

## Document Meta

- type: feat
- status: done
- owner: dev-agent
- priority: 44
- created: 2026-08-09
- completed: 2026-08-09

## User Request

현재 게임에 들어가면 무엇을 해야 하는지 감이 오지 않고, 게임인지조차 알기 어렵다. 첫 플레이어가 목표, 조작, 승리 조건을 즉시 이해할 수 있도록 보강한다.

## Scope

- Add an in-world mission brief when gameplay starts.
- Explain the core loop: open file, attach evidence, explain contradiction to ECHO, submit.
- Add a persistent `NEXT ACTION` strip that changes based on act progression, attached evidence, security unlock, and recovery state.
- Provide a first-file shortcut so the player can immediately inspect `sensor_calib.log`.
- Preserve diegetic Hermes OS presentation instead of adding external webpage-style help text.

## Acceptance Criteria

- On first terminal entry, the player sees why they are trapped and what the win condition is.
- The player can understand that this is an evidence-investigation game.
- The first required action points to `sensor_calib.log`.
- The right-side ECHO submit loop is explained before the player needs to discover it alone.
- `NEXT ACTION` updates through Act 1, Act 2, Act 3, and ending-ready states.
- Production build passes.

## Dependencies

- Previous: `feat-028`
- Next: human play review or QA follow-up bugs

## Implementation Notes

- Code commit: `feat-029 add first play mission onboarding`
- Verification: `npm run build`, `git diff --check`

## Status Log

- todo: user reported first-play purpose and game loop are unclear.
- in_progress: mission brief modal and dynamic next-action strip added.
- done: build passed and ops tracking updated.

## Change-001 Impact Note

- First-play mission onboarding is integrated into the 5-minute Rapport Phase (routine work tasks + ECHO assistant interaction) prior to ECHO reboot and quarantine declaration.
- Follow-up implementation defined in `feat-033`.

