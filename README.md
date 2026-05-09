# Two-Stage Audio Amplifier

<p align="center">
  <a href="https://isaacadjei.me">
    <img src="https://img.shields.io/badge/Website-isaacadjei.me-111111?style=for-the-badge&logo=firefox&logoColor=white">
  </a>
  <a href="https://www.linkedin.com/in/isaacadjei">
    <img src="https://img.shields.io/badge/LinkedIn-Isaac_Adjei-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white">
  </a>
  <a href="mailto:offices.isaac@gmail.com">
    <img src="https://img.shields.io/badge/Email-Contact-ff6f61?style=for-the-badge&logo=gmail&logoColor=white">
  </a>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge">
</p>

A two-stage audio amplifier designed to take a line-level audio input from a mobile phone and drive an 8 Ω speaker. Stage 1 is an inverting active band-pass filter built around a TL071 op-amp. Stage 2 is a unity-gain power buffer built around an OPA551, providing the current drive needed to power the speaker. The full design was simulated in Proteus SPICE, built and verified on breadboard and implemented as a custom PCB.

<h2 align="center">Final Assembly</h2>

<p align="center">
  <img src="media/images/Figure17c_PCB_Angled.jpg" alt="Assembled PCB angled view showing component placement" width="480">
</p>

---

## Documentation Hub

<p align="center">
  <a href="DOCUMENTATION.md">📖 Documentation</a> &nbsp;•&nbsp;
  <a href="FAQ.md">❓ FAQ</a> &nbsp;•&nbsp;
  <a href="media/GALLERY.md">🖼️ Gallery</a> &nbsp;•&nbsp;
  <a href="report/audio-amplifier-report.pdf">📄 Full Report</a> &nbsp;•&nbsp;
  <a href="CONTRIBUTING.md">🤝 Contributing</a>
</p>

---

## Overview

The amplifier consists of two cascaded stages:

- **Stage 1 (TL071 Active Band-Pass Filter):** Provides frequency selectivity across the human hearing range (5 Hz to 28.54 kHz) and voltage gain to bring the 0.87 Vpp mobile phone output up to 3 Vpp.
- **Stage 2 (OPA551 Unity-Gain Buffer):** Replicates the Stage 1 output voltage at high current, driving the 8 Ω speaker load without adding gain.

The design was taken from initial calculations through Proteus SPICE simulation, dual-supply breadboard, single-supply breadboard and finally a completed PCB.

---

## Specifications

| Parameter | Value |
|---|---|
| Input source | iPhone 14 Pro Max |
| Input voltage | 0.872 Vpp at 440 Hz |
| Output voltage | 3 Vpp at 440 Hz |
| Speaker load | 8 Ω |
| Lower cutoff frequency | 5 Hz |
| Upper cutoff frequency | 28.54 kHz |
| Stage 1 IC | TL071CP |
| Stage 2 IC | OPA551PA |
| Feedback resistor | 82 kΩ |
| Supply configuration | Single supply |

---

## Results

PCB measurements at 440 Hz:

| Stage | Input | Output | Notes |
|---|---|---|---|
| Stage 1 (TL071 active filter) | 0.868 Vpp | 3.000 Vpp | Meets 3 Vpp target |
| Stage 2 (OPA551 buffer) | 0.872 Vpp | 2.980 Vpp | Unity gain confirmed |

Frequency response verified across the full audio band on both breadboard and PCB. Full results with simulation comparison in [DOCUMENTATION.md](DOCUMENTATION.md#10-results).

---

## Tech Stack

<p align="center">
  <img src="media/assets/proteus.jpg" alt="Proteus EDA" width="65" title="Proteus">
  &nbsp;&nbsp;
  <img src="https://techstack-generator.vercel.app/github-icon.svg" alt="GitHub" width="65" title="GitHub">
  &nbsp;&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git" width="65" title="Git">
  &nbsp;&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" alt="VS Code" width="65" title="VS Code">
  &nbsp;&nbsp;
  <img src="media/assets/excel-icon.png" alt="Microsoft Excel" width="65" title="Microsoft Excel">
  &nbsp;&nbsp;
  <img src="media/assets/word-icon.png" alt="Microsoft Word" width="65" title="Microsoft Word">
</p>

<p align="center">
  <b>Proteus</b> &nbsp;&nbsp;&nbsp;&nbsp;
  <b>GitHub</b> &nbsp;&nbsp;&nbsp;&nbsp;
  <b>Git</b> &nbsp;&nbsp;&nbsp;&nbsp;
  <b>VS Code</b> &nbsp;&nbsp;&nbsp;&nbsp;
  <b>Excel</b> &nbsp;&nbsp;&nbsp;&nbsp;
  <b>Word</b>
</p>

---

## Equipment

| Tool | Model | Purpose |
|---|---|---|
| Oscilloscope | Tektronix TBS1052C | Waveform capture and peak-to-peak voltage measurement |
| Function generator | Hameg HM8030 | Generating sine wave test signals for frequency response measurements |
| Audio source | iPhone 14 Pro Max | 440 Hz sine wave input for amplifier characterisation and testing |
| DC power supply | Dual-output bench PSU | Providing split supply (±15 V) for breadboard op-amp testing |
| Breadboard | 830-point | Dual supply and single supply circuit prototyping |
| Soldering iron | - | PCB component assembly and rework |

---

## Repository Structure

```
two-stage-audio-amplifier/
├── design/
│   ├── calculations/       Design calculation workbooks and frequency response data
│   └── proteus/
│       └── exports/        Schematic, PCB layout and simulation exports (PNG)
├── media/
│   ├── images/             Circuit figures, PCB photographs and oscilloscope traces
│   ├── block-diagrams/     System block diagrams and design flowcharts
│   └── GALLERY.md          Curated image gallery with descriptions
├── report/
│   └── audio-amplifier-report.pdf   Full technical report
├── DOCUMENTATION.md        Complete technical reference
├── CONTRIBUTING.md         Commit and workflow standards
└── LICENSE                 MIT
```

---

## Contact

Isaac "Zac" Adjei

- GitHub: [zaccesss](https://github.com/zaccesss)
- Website: [isaacadjei.me](https://isaacadjei.me)
- Email: offices.isaac@gmail.com

<p align="center">
  <b>Project Status:</b> Completed &nbsp;|&nbsp; <b>Last Updated:</b> May 2026
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=100&section=footer" />
</p>
