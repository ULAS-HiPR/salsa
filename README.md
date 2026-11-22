# Salsa

HiPR's active control board for RCS and grid fins. Owner: Nooner (Seán Noone). Helpers: Anav, Richard.
Nothing is designed, built or flown yet.

**Start here:** [current system](current-system.md) → [decisions](decisions.md) → [Notion brief](https://app.notion.com/p/3e3cc5f72fe28132960ad0d28a1006ff).

## Read in this order

1. [Current system](current-system.md): what is true now.
2. [Decisions](decisions.md): what is settled, what is proposed, what is open.
3. [Requirements](docs/requirements/README.md): captured by 14 December.
4. [Interfaces](interfaces/README.md): where Salsa meets the rest of the vehicle.
5. [Hardware](hardware/README.md) for CAD.

Don't start at the project log.

## Where things live

| Where | What |
| --- | --- |
| This repository | Decisions, requirements, interfaces, design files: the truth |
| [Notion brief](https://app.notion.com/p/3e3cc5f72fe28132960ad0d28a1006ff) | The brief, for newcomers |
| Discord, avionics-projects → Salsa | Questions and chat |
| [Ogma2](https://github.com/ULAS-HiPR/Ogma2) | Burrito and Churro, the core Salsa connects to, and the template this repository copies |

## Repository

| Path | Contents |
| --- | --- |
| `docs/requirements/` | Requirements with their source, mechanism and verification |
| `interfaces/` | Contracts with neighbouring boards |
| `hardware/` | Native KiCad and drawings, tracked directly |
| `sources/` | Only evidence a current decision needs |
| `project-log.md` | Append-only history |

CAD, measurements and datasheets outrank prose. No raw transcripts, private
correspondence or generated dumps. This repository is public.
