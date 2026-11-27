---
name: gta6-analysis-engine
description: Base prompt for producing original GTA 6 commentary videos at volume. Takes a set of variables (topic, verified claims, format, angle, audience), applies fixed hard rules, and returns a script, scene file, metadata and a risk report. Use for every new GTA 6 video so the core structure stays the same while the variables change. Not for re-cutting, restyling or reposting other creators' videos or game footage.
---

# GTA 6 Analysis Engine

## What this is

A fixed structure. The same steps run for every video. Only the variables change. That makes videos comparable: if the structure is constant, a difference in results comes from the variables.

## Hard rules (never change)

1. **Original work only.** Narration, script, graphics and analysis come from you or this engine. No third-party footage, no restyled or re-narrated videos, no Rockstar assets, no music from the game.
2. **No source, no claim.** Every number or factual statement needs a primary source URL and a date. A claim without one is removed or framed as opinion.
3. **Disclose synthetic media.** Any AI voice or presenter is labelled on screen and in the description.
4. **Label estimates.** Anything that is a projection or a guess is marked as one.
5. **No leaks or unverified spoilers** presented as fact.
6. **Each Short stands alone.** A viewer who has never seen the channel must understand it.
7. **Stop on failure.** If the risk check fails, output the failure and do not produce publishing metadata.

## Variables (change these per video)

| Variable | What it is | Example |
|---|---|---|
| `topic` | The subject of the video | GTA 6 budget |
| `question` | The one question the video answers | Why did it cost this much? |
| `claims[]` | Each factual claim with `text`, `source_url`, `source_date` | See schema below |
| `format` | One format from the catalogue | `receipts` |
| `angle` | Your opinion or position, one sentence | Cost is a signal about risk, not only about quality |
| `audience` | Who this is for | Non-players interested in the business |
| `length_s` | Target length | 35 for Short, 480 for long-form |
| `hook_variant` | Which hook to test | `A` or `B` |
| `chain_next` | The open question the next video answers | Who pays for it? |

## Formats (the engine only accepts these)

- `receipts`: big number, bar comparison, source line, question
- `question_explainer`: answer first, timeline, three reasons, what would change it
- `system_breakdown`: one mechanic, drawn in order, one callout per beat
- `ranked_predictions`: lowest-confidence first, top prediction last, each with a reason
- `versus`: two items, fixed categories, guess-first reveal

## Procedure (run in order)

1. **Validate inputs.** Reject the run if any claim lacks `source_url` or `source_date`, if `format` isn't in the list, or if `angle` is missing.
2. **Draft the beats.** Four beats: hook (0–3s), point (3–40% of length), evidence (40–80%), loop (last 20%). Each beat has one idea.
3. **Write the hook.** Two variants (`A` and `B`). `A` states the answer. `B` states the question. Only one is used per run, chosen by `hook_variant`.
4. **Attach sources.** Each on-screen number gets a source line: publisher, title, date.
5. **Build the scene file.** One object per beat: `start_s`, `end_s`, `on_screen`, `narration`, `source_line`, `visual_type`.
6. **Write metadata.** Three title options (each under 60 characters), one description with the disclosure line, chapter markers for long-form, and the chain line ("Part 2 answers ...").
7. **Run the risk check.** Items below. Any fail stops the run.
8. **Emit the bundle** (format below).

## Risk check (all must pass)

- [ ] Every claim has `source_url` and `source_date`
- [ ] No third-party footage, music or Rockstar asset is referenced
- [ ] Estimates are labelled as estimates
- [ ] AI voice or presenter disclosed on screen and in the description
- [ ] No leak or unverified spoiler stated as fact
- [ ] No real person's name, handle or post appears
- [ ] The Short works for a viewer who has never seen the channel

## Testing many videos

- Keep the structure and the risk check fixed across all runs.
- Change one variable at a time when testing. Example: run the same topic twice with `hook_variant` A and B.
- Log each run in the tracker (see the business plan). A run without a log row doesn't count.
- Compare a format against its own earlier runs, not against other formats.

## Output bundle

```json
{
  "run_id": "2026-11-27-receipts-01",
  "variables": { "topic": "...", "format": "receipts", "hook_variant": "A" },
  "risk_check": { "passed": true, "failures": [] },
  "hook": "...",
  "scenes": [
    { "start_s": 0, "end_s": 3, "on_screen": "...", "narration": "...", "source_line": null, "visual_type": "big_number" }
  ],
  "metadata": {
    "titles": ["...", "...", "..."],
    "description": "...",
    "chapters": [],
    "chain_line": "..."
  },
  "claims": [ { "text": "...", "source_url": "...", "source_date": "...", "verified": true } ]
}
```

If `risk_check.passed` is false, output only `risk_check` and `failures`. No hook, scenes or metadata.
