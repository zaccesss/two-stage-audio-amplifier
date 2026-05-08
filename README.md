# Two-Stage Audio Amplifier

A two-stage audio amplifier designed to take a line-level audio input from a mobile phone and drive an 8 ohm speaker. The amplifier was designed, simulated, prototyped and implemented as a custom PCB during first-year Electronic Engineering studies at Aston University.

---

## Overview

The design consists of two cascaded stages:

- **Stage 1 - Active Band-Pass Filter:** An inverting summing active band-pass filter built around a TL071 operational amplifier. This stage provides frequency selectivity across the human hearing range and delivers the required voltage gain to bring the input signal up to the target output level.
- **Stage 2 - Power Buffer:** A unity-gain power buffer built around an OPA551 operational amplifier, providing the current drive capability required to power an 8 ohm speaker load without adding gain.

The full design was developed through hand calculations, verified using Proteus SPICE simulation, built and tested on breadboard (first with a dual supply, then adapted for single supply) and implemented as a final PCB.

---

## Specifications

| Parameter | Value |
|---|---|
| Input source | iPhone 14 Pro Max (3.5 mm audio) |
| Input voltage | 0.872 Vpp at 440 Hz |
| Output voltage target | 3 Vpp |
| Speaker load | 8 ohm |
| Lower cutoff frequency | 5 Hz |
| Upper cutoff frequency | 28.54 kHz |
| Stage 1 IC | TL071CP |
| Stage 2 IC | OPA551PA |
| Feedback resistor | 82 kohm |
| Supply configuration | Single supply (final design) |

---

## Results

PCB measurements at 440 Hz:

| Stage | Input | Output |
|---|---|---|
| Stage 1 (TL071 active filter) | 0.868 Vpp | 3.000 Vpp |
| Stage 2 (OPA551 buffer) | 0.872 Vpp | 2.980 Vpp |

Both stages met design targets. The frequency response was verified across the full audio band on breadboard and PCB.

---

## Repository Structure

```
two-stage-audio-amplifier/
├── design/
│   ├── calculations/       Design calculation workbooks and frequency response data
│   └── proteus/
│       └── exports/        Proteus SPICE simulation and PCB design exports
├── docs/
│   ├── briefing/           Project briefing, assignment brief and bill of materials
│   └── reference/          Reference materials used during design
├── labs/
│   └── op-amp-practical/   Op-amp practical lab work supporting the design
├── media/
│   ├── block-diagrams/     System block diagrams and design flowcharts
│   └── images/             Circuit figures, PCB photographs and oscilloscope traces
├── report/                 Final technical report (PDF)
└── workbooks/              Project management workbooks (BOM, Gantt, dashboard)
```

---

## Tools

| Tool | Purpose |
|---|---|
| Proteus | Schematic capture, PCB layout and SPICE simulation |
| Microsoft Excel | Design calculations and frequency response data analysis |
| Microsoft Word | Technical report with IEEE formatting |
| Oscilloscope (TBS1052C) | Breadboard and PCB measurements |

---

## Contact

Isaac "Zac" Adjei

- GitHub: [zaccesss](https://github.com/zaccesss)
- Email: isaacc.adjeii@gmail.com
