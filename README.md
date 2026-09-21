# Jev browser and computer-use benchmark

This is a small, reproducible snapshot of a benchmark comparing a fast Jev browser-action system, a Jev-first fallback system, and Luna-style visual computer use.

The short version:

| Lane | Jev Browser | Jev Ultrafast | Hybrid | Luna |
| --- | ---: | ---: | ---: | ---: |
| Simple browser tasks | 18/42 (42.9%) | 18/42 (42.9%) | **39/42 (92.9%)** | **39/42 (92.9%)** |
| Longer browser workflows | 0/10 (0%) | 1/9 (11.1%) separate public lane | **7/10 (70%)** | **7/10 (70%)** |
| Native desktop tasks | 1/5 (20%) | not measured | **5/5 (100%)** | **5/5 (100%)** |

## Overall aggregate

The report's **Overall** view combines every measured task for each system. It ranks by success rate first, then estimated cost per successful task.

| Rank | System | Successes | Rate | Average time | Cost per success |
| ---: | --- | ---: | ---: | ---: | ---: |
| 1 | Hybrid | 51/57 | 89.5% | 29.68s | $0.0090 |
| 2 | Luna | 51/57 | 89.5% | 44.57s | $0.0128 |
| 3 | Jev Ultrafast | 19/51* | 37.3% | 1.07s | $0.0012 |
| 4 | Jev Browser | 19/57 | 33.3% | 4.12s | $0.0018 |

\* Jev Ultrafast was not measured on native desktop computer use, so its denominator is 51 rather than 57.

Hybrid ties Luna on the scored success rates while using fewer Luna actions on the tasks Jev can handle. In the simple lane it averaged 25.19 seconds and about $0.0069 per successful task, versus 32.49 seconds and about $0.0107 for Luna. Jev itself was much faster and cheaper, but its success rate fell sharply as tasks required interpretation, typing, verification, or recovery.

## What is in this repository

- `data/results.json` - machine-readable scores, timings, and cost estimates.
- `RESULTS.md` - the plain-language methodology and tables.
- `report.html` - a standalone light/dark report with a cost-versus-success chart.
- `report/` - report screenshots.
- `videos/README.md` - why authenticated recordings are not copied into this public repository and how the local verified video library is organized.

## The lanes

### Simple browser tasks

42 controlled tasks covering navigation, clicking, selecting, scrolling, forms, small edits, and state checks. These are useful for measuring the mechanical ceiling of a browser-action system, but they are not a claim that every task represents a normal day of computer use.

### Longer browser workflows

Ten longer browser flows such as a flight search, restaurant reservation, project-tracker editing, and authenticated app checkpoints. The safe stopping point was before an irreversible purchase, booking, or message send. A pass means the defined checkpoint was reached and verified, not that money was charged or a reservation was finalized.

The separate Jev Ultrafast result is a public nine-flow lane and is not directly comparable to the exact ten-flow lane.

### Native desktop computer use

Five tasks in desktop apps: Spotify, TextEdit, Pages, Keynote, and Numbers. The tasks required real visual interaction and, where relevant, typing or structured editing. This lane is intentionally separate from browser automation.

## Browser tools and JavaScript

Page inspection, accessibility information, and JavaScript evaluation are normal browser-tool capabilities for an LLM browser integration. A separate deterministic probe achieved 14/14, and a Jev-plus-replay experiment reached 42/42. Those are capability checks, not model-controlled Luna scores, so they are kept out of the headline tables. A fair follow-up would give Luna and Hybrid the same browser-tools interface and rerun the same fixtures under matched conditions.

## Cost and timing

Costs are estimates, not invoices. Jev values use the recorded API estimate. Luna values use the recorded token/action proxy. Local browser and desktop tooling is treated as $0. The estimates are useful for comparing approaches within this run, not for predicting a provider bill without the provider's current pricing and billing export.

## Reproduce the public snapshot

No credentials, auth URLs, private traces, or authenticated recordings are included here.

```bash
python3 -m json.tool data/results.json
open report.html
```

The complete local runner depends on private test accounts, local browser sessions, and desktop applications, so this public snapshot publishes the safe results and methodology rather than pretending that a clean-room checkout can replay those private sessions.

## Recording audit

The local report links only to clips whose sampled frames were checked for the intended browser or desktop app. Several earlier long captures showed the wrong blank Chrome window for their entire duration; those links were removed from the report instead of being presented as evidence.
