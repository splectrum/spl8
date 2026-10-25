# CLAUDE.md — spl8 (design repo)

spl8 is **logical space**: we discuss and agree working practices and design
for the next engineering repo. No production code lives here. See `README.md`
for the purpose and the exit condition.

## How we work here

- **Discuss first, write what has settled.** Drafts are marked as proposals.
  A document's status line changes to *settled* only when the human says so.
- **Natural language.** Prose is the working medium. Where something must be
  checkable, the AI turns it into examples or test cases for the human to
  confirm — the human does not have to write structured specs.
- **Ask in prose.** Open questions go in the conversation and in
  `open-questions.md`, never as option pickers.
- **Distillation, not demolition.** Prior work (spl6, spl7, splectrum.world)
  is sorted into settled / superseded / open, not rediscovered.
- **Calibrated vision.** Write only at the resolution that holds; leave
  moving parts explicitly open.
- **Probes ground agreement.** When a practice can only be agreed after seeing
  it work, run a small probe in `probes/` and commit its (scrubbed) run log.
  Probes stay small — engineering belongs in the engineering repo.
- **Finish.** spl8 has an exit condition. Prefer settling a question over
  elaborating it.

## Commits

Direct commits to `main`, at coherent intervals — not after every edit.

## Sources

- `splectrum/spl7` — coordination repo of the previous, more collaborative phase
- `splectrum/spl6` — design docs, the p2p-docker-dev POC phases, the oracle tests
- `splectrum/spl5` — original fabric implementation
- splectrum.world — the published philosophy and engineering pages
