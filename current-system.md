# Salsa current system

Updated 22 November 2026. Decisions live in [decisions.md](decisions.md); this file states
what is true now. Nothing is designed, built or flown yet.

Owner: Nooner (Seán Noone). Helpers: Anav, Richard. Next milestone: Requirements captured by 14 Dec.

Seeded from the [Notion brief](https://app.notion.com/p/3e3cc5f72fe28132960ad0d28a1006ff) and from Ogma2's decisions as they stood on
22 November. Where they disagree, Ogma2's decisions win, and the difference is
listed below.

## Purpose

Drive the merged RCS and grid-fin module, only when Burrito allows it: two cold-gas solenoids, four fin servos and a lock servo ([D-19Nov.6](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md)). It runs its own loop on its own IMU and magnetometer ([D-5Nov.1](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md)). One Salsa also drives Ériú's nose canards at IREC ([D-21Nov.7](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md)), and the IREC rocket flies Burrito, Churro and Salsa as the flight test of the core ([D-20Nov.3](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md)).

## Must demonstrate

- Eight bench tests, AB-01 to AB-08.
- Talks only over bus 2, and goes to neutral within [__] ms of stale permission.
- Acts only on a fresh Active, after dormancy. Abort holds until a power cycle on the ground.
- The neutral path works with the firmware hung.
- Lasts 6 h on the rail plus a flight. The arm key cuts actuator power. It flashes from the panel.

## Interfaces

Set by Ogma2's decisions unless marked proposed. Changing one needs the other
owner's agreement and a row in both repositories.

| With | What | Ogma2 decision |
| --- | --- | --- |
| Burrito | CAN bus 2 only, on Burrito's flight MCU FDCAN2: Gecko 3-way, 500 kbit/s Classical CAN, fixed resistors at both ends. Burrito sends Safe, Active or Abort with a counter at 10–20 Hz; a stale message counts as Safe. Slow flight state goes out, health comes back. Burrito gives permission, never commands; the loop runs on Salsa. | [D-5Nov.3](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md), [D-5Nov.2](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md) |
| Churro | Power from Churro's ACT branch off the 6S actuator pack, with Salsa's arm key in series. Salsa converts to its actuators' voltages itself. | [D-21Nov.1](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md) |
| Access panel | Arm key and one USB-C at the panel; no firmware over CAN. | [D-19Nov.9](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md) |

## Also known

- Rules for closed-loop actuator nodes stand from [D-2Nov.8](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md) (its pack clause replaced by D-21Nov.1).

## External rules

LV-0650–0700, active control: allowed uses only; stable with the actuators locked; fail safe to neutral with the thrusters off; dormant to at least 1500 m AGL without flight history; electronics meet the recovery redundancy rule (LV-0690); stored energy. LV-0260–0280 for its key. Active control triggers EuRoC's Design Review, and its scripts go in the RocketPy simulation.

## Parts one person can own

1. Power, arming and the neutral path: the arm key, the actuator power switch, the hardware path to neutral
2. Actuator drivers: two solenoid drivers, five servo outputs, current sensing
3. Bus 2 and the safety logic: the transceiver, Safe/Active/Abort, the stale timeout, dormancy, the abort latch
4. Sensing and the loop: IMU, magnetometer, the control law with Radion, the RocketPy scripts
5. The bench rig and the eight tests

## Known discrepancy

The Notion brief (edited 20 Nov) still says Salsa has its own pack and takes no power from Churro in flight. Ogma2's D-21Nov.1 replaced that: power comes from Churro's ACT branch with the arm key in series. This repository follows D-21Nov.1; the Notion page needs the same fix.

## Timeline

| Milestone | Date |
| --- | --- |
| Requirements captured | 14 December 2026 |
| Schematics reviewed | 28 December 2026 |
| PCBs laid out and ordered | 11 January 2027 |
| Boards in hand | 1 February 2027 |
| Testing, firmware and integration | from 1 February 2027 |
| All electronics on one table | 3 weeks before the integrated vehicle |

From the [Electronics page](https://app.notion.com/p/3c8cc5f72fe28092aaf7dc3baacb4f67)'s avionics timeline.

## State

Repository created 22 November 2026. No requirements, schematic, layout or
firmware yet. Open questions are in [decisions.md](decisions.md#open).
