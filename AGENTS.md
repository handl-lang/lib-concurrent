# lib-concurrent

`concurrent` — the cooperative concurrency **contract** (step-arrow
model): the `.hnl` interface port for spawn/await/channels/locks/timers.
Backends are sibling repos (`lib-concurrent-epoll`, `lib-concurrent-js`).

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | the contract — step-arrow port surface |
| `pkg.hnl` | manifest — `modules: ["concurrent"]` |
| `scripts/hnl-gate.sh` | `.hnl` gate |
| `workflows/gate.yaml` | CI — shared `handl-gates` campaign |

## Contract

- Contract-only repo: declare the surface here; scheduler
  implementations are separate packages depending on `concurrent`
  (`branch:main`).
- The model is cooperative step arrows, not OS threads.

## Verification

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
