# Results

Run date: 2026-09-21

The ranking rule is simple: sort by success rate first, then by estimated cost per successful task. Timing is shown separately so a fast failure does not look like a good result.

## Overall snapshot

| System | Simple browser | Longer browser | Native desktop | Cost / time note |
| --- | ---: | ---: | ---: | --- |
| Hybrid | 39/42 - 92.9% | 7/10 - 70% | 5/5 - 100% | $0.0069 / 25.19s simple; $0.0177 / 45.3s longer browser |
| Luna | 39/42 - 92.9% | 7/10 - 70% | 5/5 - 100% | $0.0107 / 32.49s simple; $0.0268 / 98.7s longer browser |
| Jev Browser | 18/42 - 42.9% | 0/10 - 0% | 1/5 - 20% | $0.0003 / 1.77s simple |
| Jev Ultrafast | 18/42 - 42.9% | 1/9 - 11.1%* | not measured | $0.0005 / 0.77s simple |

\* The Jev Ultrafast longer-browser number comes from a separate public nine-flow lane.

## Simple browser tasks

| Rank | System | Success | Average time | Estimated cost per success |
| ---: | --- | ---: | ---: | ---: |
| 1 | Hybrid | 39/42 - 92.9% | 25.19s | $0.0069 |
| 2 | Luna | 39/42 - 92.9% | 32.49s | $0.0107 |
| 3 | Jev Browser | 18/42 - 42.9% | 1.77s | $0.0003 |
| 4 | Jev Ultrafast | 18/42 - 42.9% | 0.77s | $0.0005 |

## Longer browser workflows

These are meaningful multi-step flows, but the benchmark stops before an irreversible final submit.

| Rank | System | Success | Average time | Estimated cost per success |
| ---: | --- | ---: | ---: | ---: |
| 1 | Hybrid | 7/10 - 70% | 45.3s | $0.0177 |
| 2 | Luna | 7/10 - 70% | 98.7s | $0.0268 |
| 3 | Jev Ultrafast* | 1/9 - 11.1% | 2.45s | $0.0142 |
| 4 | Jev Browser | 0/10 - 0% | 11.4s | not meaningful |

\* Separate public nine-flow lane, not the same fixture set as the exact ten-flow comparison.

Representative workflows included flight search and fare selection, a Thai restaurant reservation up to the final confirmation boundary, TodoMVC project tracking, Google Drive, Notion, Figma, mail, and other authenticated app checkpoints.

## Native desktop computer use

| Rank | System | Success | Average time | Estimated cost per success |
| ---: | --- | ---: | ---: | ---: |
| 1 | Luna | 5/5 - 100% | 37.82s | about $0.0091 |
| 2 | Hybrid | 5/5 - 100% | 36.11s | about $0.0126 |
| 3 | Jev | 1/5 - 20% | 9.3s | about $0.0227 |
| 4 | Jev Ultrafast | not measured | not measured | not measured |

The five apps/tasks were Spotify playback, TextEdit typing, Pages drafting, Keynote slide creation, and Numbers spreadsheet entry. Jev succeeded on the simple native text-entry task, but failed or stopped incorrectly on richer interaction tasks. Luna completed all five. Hybrid used Jev when its result could be verified and used Luna when it could not.

## What the numbers mean

- Jev is excellent at fast, known, mechanical actions with stable targets.
- Luna is slower and more expensive, but it can interpret the screen, type, recover from drift, and verify richer state.
- Hybrid is the practical compromise in this run: try the cheap action path, verify the result, and spend Luna effort only when needed.
- The Hybrid result is not a magical new model. It is a policy plus verification and fallback, and the real-world browser comparison used a staged recorded fallback rather than one uninterrupted live turn. That limitation is called out so the tie with Luna is not overstated.

