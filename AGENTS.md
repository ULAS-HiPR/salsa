# Salsa engineering and documentation instructions

Copied from Ogma2's layout. Read [Ogma2's AGENTS.md](https://github.com/ULAS-HiPR/Ogma2/blob/main/AGENTS.md) for the
full version; this file keeps what applies here.

## Read order

1. `decisions.md`
2. `current-system.md`
3. The relevant file under `interfaces/` and `docs/requirements/`
4. `project-log.md`, newest entries last
5. The specific CAD, datasheet, measurement or test evidence needed

## Documentation rules

- `current-system.md` is the prose baseline: what is true now.
- `decisions.md` records every decision with its status. A proposal anywhere
  becomes design only when it appears there as Decided and `current-system.md`
  reflects it. Only the owner (Nooner (Seán Noone)) marks a row Decided.
- `project-log.md` is append-only. Correct an old conclusion with a new dated
  entry; don't rewrite history.
- `interfaces/` owns contracts with other boards. A boundary change must be
  agreed with the other board's owner and recorded in both repositories.
  Ogma2 controls the core's side of every interface with Burrito or Churro.
- Keep observed, stated, decided, inferred, guessed and unknown distinct.
- Quote EuRoC's rule number (LV-, SE- and others) where one applies.

## Design rules

- Every part needs a named job, a failure boundary and a test.
- Real parts only: cite the datasheet; never invent a part number or rating.
- Stale or missing data means Safe. Bench tests use inert loads.
- Anything that flies uses keyed, shrouded, positive-locking connectors.
- Simplest design that meets the requirement. No flexibility nobody asked for.

## Collaboration rules

- `main` is reviewed truth. Keep commits bounded: don't mix a design decision,
  prose cleanup and an unrelated import.
- A design change updates `decisions.md`, `current-system.md`, the affected
  interface, and appends `project-log.md`, in the same commit.
- Never commit credentials, private correspondence, personal data or raw
  model output. This repository is public.
