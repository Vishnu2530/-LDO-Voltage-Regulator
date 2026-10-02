# Project 1 — Precision LDO Voltage Regulator

## Overview
Designed and validated a 3.3 V precision LDO regulator using a TL431 shunt reference and TIP42C PNP pass transistor. Achieved 3.308 V regulated output with 0.24% output voltage error and accurate 2.495 V reference operation. Completed schematic design, PCB layout, manufacturing documentation generation, and design verification through simulation and hardware implementation.

## Specifications

| Parameter        | Target       | Simulated  |
|------------------|--------------|------------|
| Vout             | 3.3V ±1%     | 3.308 V ✓  |
| REF pin voltage  | 2.495 V      | 2.495 V ✓  |
| PSRR @ 1kHz      | >60 dB       | TBD        |
| Load regulation  | <1%          | TBD        |
| Line regulation  | <0.5%        | TBD        |
| Output noise     | <50 µV/√Hz   | TBD        |
| Dropout voltage  | <300 mV      | ~690 mV    |

## PCB & 3D Render

![3D render](3D-renders/render_angle.png)

## Simulation Waveforms

![Load transient](waveforms/load_transient.png)
![Line regulation](waveforms/line_regulation.png)
![PSRR](waveforms/psrr.png)
![Output noise](waveforms/noise.png)

## Design Decisions
- TL431 chosen over Zener: 0.5% accuracy vs ~5% for Zener
- PNP pass transistor (TIP42C): lower cost; PMOS gives better 
  PSRR but requires gate drive — PNP simpler for discrete design
- Cc = 100nF across R1 adds phase-compensating zero, reduces 
  transient overshoot
- Low-ESR Cout (100µF): too low ESR causes oscillation, too high 
  degrades transient response

## Files
- `schematic.pdf` — KiCad 10 schematic
- `pcb_layout.pdf` — PCB layout (2-layer)
- `LDO.asc` — LTspice XVII simulation file
- `TL431.sub` — TL431 behavioral SPICE model
- `gerbers/` — Gerber files for PCB fabrication
- `waveforms/` — Simulation result screenshots
- `3D-renders/` — KiCad 3D PCB renders

## Tools
LTspice XVII · KiCad 10 · TI TL431 SPICE model

## References
- TI TL431 Datasheet (SLVS543)
- TI App Note SLVA756 — LDO Basics
- TIP42C Datasheet — ST Microelectronics
