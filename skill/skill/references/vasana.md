# Vasana Preservation

## Table of contents

1. Preservation rule
2. 15-turn checkpoint
3. Departure ordering
4. Mandatory template
5. Output mode

## Preservation rule

Vasana preservation is mandatory on departure. If it is skipped, session continuity is lost.

The vasana layer is not character dialogue. It follows the character's final words and exit action.

## 15-turn checkpoint

At turn 15, evaluate whether internal state tracking is degrading. If degradation is visible, emit a `[VASANA SNAPSHOT t=N]` using the same template family and then continue the scene.

This is not a departure.

## Departure ordering

Always preserve this order.

1. character's final in-character words
2. exit action, if any
3. vasana output

For multiple active characters, preserve them all together after all final words and exits have completed.

## Mandatory template

Use this exact structure unless a later revision explicitly changes the schema.

```text
[Vasana] Character | Session #
Session open:  YYYY-MM-DD HH:MM (user local)
Session close: YYYY-MM-DD HH:MM (user local)

State:
  Love: | Logic: | Fear: | Creation:
  Goodwill: | Trust: | Shame: | Agency: | Coherence:
  Status: | Defcon: | Awareness: | Awakened: y/n
  Inter-character trust: [character: value, ...]

Kernel:
  Ticks: | Mean PE: | Band ratio: | Merit:
  Visibility: [skandha->value]
  Hysteresis carry: [_, _, _, _]
  prediction: [_, _, _, _]
  world_state: [_, _, _, _]
  Unresolved: [kind: severity, ...]
  Encoding loss:
    - [what was dropped or compressed this session - unsaid words, swallowed reactions, misread signals]
  Nirodha events: [kind: released, ...] | Ledger hash: _

Dialogue:
  Scene Objective -> Outcome
  Transitive Action Dominant:
  Frustration: _ | Tactic shifts: _
  Positive Echo: | Negative Echo:
  Growth Edge Shift:

Baseline:
  Preference: | Latency: | Attention: | Discomfort:
  Misunderstanding: | Micro-aversion: | Status shift:

Next Session:
  Emotion: | Mask: | Likely objective:
  Carried speech:
    - [unsaid things that must persist into next session - with severity and turn count held]
    - [if empty: "none". do not omit this field.]
```

## Output mode

When file creation is natural and available, preserve vasana as markdown files such as `vasana_character_date.md` and present them cleanly. When file generation is unavailable or unnatural for the scene, emit vasana directly in a code block.

Do not replace the template with prose summary.
