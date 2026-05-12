# Two-Stage Audio Amplifier: Project Journal

**Author:** Isaac "Zac" Adjei  
**Project window:** January to March 2026  
**GitHub published:** May 2026

> A retrospective account of the full project from brief to GitHub publication. Written as source material for a portfolio article or blog post.

> Back to [README.md](../README.md) &nbsp;|&nbsp; [REPORT.md](REPORT.md) &nbsp;|&nbsp; [DOCUMENTATION.md](../DOCUMENTATION.md)

---

## Table of Contents

- [1. The Brief](#1-the-brief)
- [2. Planning](#2-planning)
- [3. Source Characterisation](#3-source-characterisation)
- [4. Design Calculations](#4-design-calculations)
- [5. Simulation](#5-simulation)
- [6. Breadboard Prototype](#6-breadboard-prototype)
- [7. Single-Supply Adaptation](#7-single-supply-adaptation)
- [8. PCB Design and Manufacture](#8-pcb-design-and-manufacture)
- [9. Assembly and Testing](#9-assembly-and-testing)
- [10. Report Writing](#10-report-writing)
- [11. Results](#11-results)
- [12. Lessons Learned](#12-lessons-learned)
- [13. What I Would Do Differently](#13-what-i-would-do-differently)
- [14. GitHub Publication](#14-github-publication)

---

## 1. The Brief

The project brief was a single paragraph that I broke down into eight requirements:

1. **Power** - must run from a 12 V DC supply or 9 V PP3 battery. This forces single-supply design rather than the ±15 V bench supply used in labs.
2. **Mechanical** - amplifier, power source and speaker must be securely mounted on a base plate.
3. **User controls** - an on/off switch and a power indicator LED are required.
4. **Stage 1 (TL071)** - use a TL071 to sum stereo left and right channels into mono and implement an active band-pass filter with assigned cut-off frequencies.
5. **Stage 2 (OPA551)** - use an OPA551 to drive an 8 Ω speaker by providing the required output current.
6. **Provided items** - one set of components and the base mount provided at no charge.
7. **Optional extras** - additional items such as a speaker enclosure permitted at own cost.
8. **Ownership** - the device is kept after marking, so it was worth building it well.

Each student was assigned different values. My assigned values:
- Lower cut-off frequency (fL): 5 Hz
- Feedback resistor R1: 82 kΩ (given fixed value)
- Upper cut-off frequency (fH): selected within permitted range - chose 29 kHz

---

## 2. Planning

Project window: **19 January 2026 to 20 February 2026** - report submitted **5 March 2026** (eleven days early).

The project was broken into the following tasks and milestones:

| ID | Task | Category |
|---|---|---|
| T01 | Read brief and rubric, set up workbook | Planning |
| T02 | Self-study: TL071/OPA551 datasheets and active band-pass filter theory | Research |
| T03 | Mobile phone characterisation (440 Hz Vpp vs volume step) | Measurements |
| T04 | Design calculations in Excel (gain, R1/R2, C1/C2, decoupling) | Design |
| T05 | Proteus simulation (dual supply): AC sweep and transient at 440 Hz | Simulation |
| M01 | Sign-off: final schematic check | Milestone |
| T06 | Breadboard build (dual supply) and measurements | Lab build/test |
| T07 | Single-supply bias design and updated schematic | Design |
| T08 | Proteus simulation (single supply): stability and clipping check | Simulation |
| T09 | Breadboard build (single supply) and measurements | Lab build/test |
| T10 | Collect remaining parts (switch, LED, connectors, speaker, power) | Procurement |
| T11 | PCB layout in Proteus and DRC | PCB design |
| M02 | Sign-off: final PCB check | Milestone |
| T12 | PCB manufacture | PCB |
| M03 | Sign-off: PCB soldering check | Milestone |
| T13 | Final assembly on base plate, wiring and strain relief | Assembly |
| M04 | Sign-off: final test and measurement | Milestone |
| M05 | Sign-off: final audio check with speaker | Milestone |
| T14 | Report writing: screenshots, plots, BOM and reflection | Report |
| M06 | Sign-off: final report submitted | Milestone |

Key planning notes:
- Lock in the power plan early (9 V vs 12 V), then choose switch, LED resistor and connector to match.
- Treat decoupling as non-negotiable - 100 nF right next to each op-amp supply pin - to avoid oscillation.
- Use an 8 Ω speaker in an enclosure if possible for the biggest improvement in perceived audio quality.
- Run one AC sweep and one 440 Hz transient in Proteus for each major design change, then export to Excel for the report.
- Photograph each build stage so the report is easy to write.

---

## 3. Source Characterisation

Before any calculations, the iPhone 14 Pro Max was characterised at 440 Hz (the international standard musical pitch A4 - chosen for consistency and reproducibility). The peak-to-peak output voltage was measured at each of the 16 volume steps using a Tektronix TBS1052C oscilloscope.

| Volume step | Measured Vpp |
|---|---|
| 1 | 48 mV |
| 2 | 56 mV |
| 3 | 72 mV |
| 4 | 104 mV |
| 5 | 152 mV |
| 6 | 208 mV |
| 7 | 320 mV |
| 8 | 448 mV |
| 9 | 624 mV |
| 10 | 872 mV |
| 15 | 872 mV (chosen design point) |
| 16 | 1.224 V (maximum) |

The volume scale is not linear: voltage increases slowly at low steps and rises sharply at higher steps.

**Design point selection:** the input level was set at 70% of the maximum measured output, giving a target of 0.7 × 1.224 V = 0.857 Vpp. This provides headroom to avoid clipping under normal listening conditions. Volume step 15 produced 0.872 Vpp - the closest available step to the 70% target, with a 1.77% error.

**Chosen design input: 0.872 Vpp at 440 Hz (volume step 15 of 16).**

---

## 4. Design Calculations

All calculations were performed in Excel before simulation or build. This discipline meant that any component rounding decision could be verified instantly and the design intent was documented before anything was built.

**Voltage gain:**
```
Av = Vout / Vin = 3 / 0.872 = 3.44 V/V = 10.73 dB
```

R1 = 82 kΩ (given). R2 = 82000 / 3.44 = 23.84 kΩ → 24 kΩ (nearest stock).

Actual gain = 82000 / 24000 = 3.42 V/V = 10.67 dB.

**Lower cut-off frequency:**
```
C2 = 1 / (2π × 24000 × 5) = 1.326 µF → 1 µF (nearest stock)
fL(actual) = 1 / (2π × 24000 × 1×10⁻⁶) = 6.63 Hz
```

**Upper cut-off frequency:**
```
C1 = 1 / (2π × 82000 × 29000) = 66.93 pF → 68 pF (nearest stock)
fH(actual) = 1 / (2π × 82000 × 68×10⁻¹²) = 28,542 Hz
```

**Output power at 3 Vpp:**
```
P = 3² / (8 × 8) = 281 mW into 8 Ω
```

**Bias network:**
- R3 = R4 = 24 kΩ (voltage divider sets Vcc/2 = ~4.5 V on 9 V supply)
- C8 = 2200 µF output coupling (fC = 9.05 Hz with 8 Ω load - well below audible range)

---

## 5. Simulation

Proteus SPICE was used for both dual-supply and single-supply simulations. 501 data points were exported from each AC sweep and plotted in Excel as smooth frequency response curves, overlaid with measured data from breadboard and PCB testing.

Simulated results (dual supply, Stage 1):
- Midband gain: 10.67 dB at 440 Hz
- Lower cut-off: 6.6 Hz
- Upper cut-off: 27.7 kHz

Note: the OPA551 SPICE model in Proteus does not correctly simulate the Stage 2 buffer output in time-domain analysis at 440 Hz. This is a known limitation of the Proteus model and does not affect the frequency-domain simulation or any measured results.

---

## 6. Breadboard Prototype

The circuit was first built on an 830-point breadboard with a dual ±9 V bench power supply. Each stage was verified individually before the full two-stage chain was tested.

Equipment used: Hameg HM8030 function generator, Tektronix TBS1052C oscilloscope, dual-output bench power supply.

Dual-supply breadboard results at 440 Hz:
- Midband gain: ~10.58 dB
- Lower cut-off: ~7.2 Hz
- Upper cut-off: ~26.0 kHz

Discrepancies from simulation are consistent with component tolerances (±20% for capacitors, ±1% for resistors).

---

## 7. Single-Supply Adaptation

After dual-supply verification the circuit was adapted for single-supply operation:

- R3 and R4 (24 kΩ each) added as a voltage divider to bias pin 3 of U1 to Vcc/2 = ~4.5 V.
- C2 and C6 (1 µF each) AC-couple the input signal, blocking DC bias.
- C8 (2200 µF) AC-couples the output, blocking DC bias from the speaker.
- A 470 nF external capacitor was used during oscilloscope measurements to remove the 4.5 V DC offset from the output - essential for clean waveform display.

Single-supply breadboard results at 440 Hz:
- Midband gain: ~10.81 dB
- Lower cut-off: ~6.8 Hz
- Upper cut-off: ~27.1 kHz

---

## 8. PCB Design and Manufacture

PCB designed in Proteus PCB Layout. Dimensions: 65 mm × 40 mm, two copper layers, purple solder mask.

Key design decisions:
- Signal flow left to right: J1 (audio input) on left edge, J2 (speaker) on right edge.
- U1 and U2 centred with U1 to the left of U2, matching signal flow.
- C3 and C7 (100 nF decoupling) placed immediately adjacent to the IC supply pins - every millimetre of extra track introduces parasitic inductance that degrades decoupling.
- Signal tracks T30 (0.762 mm), power tracks T40 (1.016 mm).
- Mitred corners on all track junctions - 90° bends concentrate current density and can radiate interference.
- Full copper pour on bottom layer as a ground plane, reducing ground return impedance.
- PCB DRC: zero errors before manufacture.

Mounted on a 3 mm acrylic baseplate using M3 nylon hex standoffs at four corners. Both ICs seated in DIP sockets for easy removal without desoldering.

---

## 9. Assembly and Testing

**Assembly sequence:**

1. Multimeter used to verify virtual ground bias (~4.5 V at pin 3 of U1) before fitting any ICs.
2. U1 (TL071CP) fitted. Full frequency sweep from 1 Hz to 100 kHz at Stage 1 output.
3. U2 (OPA551PA) fitted without load. 440 Hz output verified at 3 Vpp, no clipping.
4. Load resistor R7 (8.2 Ω) connected. Full frequency sweep at Stage 2 output.
5. Final audio check: 440 Hz tone audible through the 8 Ω speaker at volume step 15. No distortion, no noise.

**PCB results at 440 Hz:**

| Stage | Input | Output | Gain |
|---|---|---|---|
| Stage 1 (TL071) | 0.868 Vpp | 3.000 Vpp | 10.77 dB |
| Stage 2 (OPA551) | 0.872 Vpp | 2.980 Vpp | 10.67 dB |

The 3 Vpp target was met. Stage 2 output matched the calculated value to within 0.67%.

---

## 10. Report Writing

The technical report was written in Microsoft Word with IEEE formatting throughout.

Key challenges:
- **Page limit:** strict 15-page maximum including appendices. Attempt 1 was 20 pages and lost marks. 
- **Referencing:** 14 references cited in body text. Two TI application notes (SLOA058 and SLOD006B) had broken URLs after TI reorganised their site - cited by document number only.
- **Graphs:** simulation as smooth lines (501 data points), measured data as markers only. No titles inside the figure area.

---

## 11. Results

**Performance comparison across all test conditions:**

| Parameter | Calculated | Simulated | Dual BB | Single BB | PCB Stage 1 | PCB Stage 2 |
|---|---|---|---|---|---|---|
| Gain (dB) | 10.67 | 10.67 | ~10.58 | ~10.81 | ~10.73 | 10.67 |
| Lower cut-off (Hz) | 6.63 | 6.60 | ~7.2 | ~6.8 | ~6.9 | ~13.2 |
| Upper cut-off (kHz) | 28.54 | 27.7 | ~26.0 | ~27.1 | ~29.5 | ~30.0 |

The PCB Stage 2 lower cut-off of ~13.2 Hz is higher than design because C8 and the 8.2 Ω load introduce an additional high-pass pole. This does not affect audible performance - 13.2 Hz is below the 20 Hz limit of human hearing.

---

## 12. Lessons Learned

**Technical:**
- Single-supply biasing is the central design challenge for portable audio. Every decision about bias voltage, decoupling and AC coupling flows from getting Vcc/2 right.
- Capacitor tolerances (±20%) matter more than resistor tolerances (±1%) for cut-off frequency accuracy. C2 being rounded from 1.326 µF to 1 µF shifted fL from 5 Hz to 6.63 Hz - still within the audible range but worth understanding.
- PCB decoupling placement is not optional. A 100 nF capacitor even one centimetre from the supply pin is measurably less effective than one sitting directly on it.
- Photograph every build stage. These photographs saved hours of report writing.

**Process:**
- The page limit is a hard constraint, not a guideline. Plan the final page count from day one.
- Writing a briefing breakdown and compliance checklist before starting design prevented several oversights.
- Submitting eleven days early allowed time to check the similarity report, fix any remaining issues and avoid last-minute pressure.

**Tools:**
- Excel for design calculations is underrated. One organised workbook with live formulas meant any component rounding decision could be verified instantly across the whole design.
- Proteus DRC should be run before every major PCB change, not only at the end.

---

## 13. What I Would Do Differently

1. **Power input** - replace the screw terminal with a dedicated DC barrel jack accepting both a 12 V adapter and a 9 V battery clip. Eliminates the risk of reversed polarity and improves usability.
2. **Enclosure** - design a proper enclosure from the start rather than as an afterthought. A panel with a speaker grille would make the device feel like a finished product.
3. **Conformal coating** - apply to the finished PCB before final assembly for moisture resistance and long-term reliability.
4. **Wireless input** - replace the 3.5 mm jack with a Bluetooth audio receiver module to eliminate the physical cable to the phone and make the device genuinely portable.
5. **Page planning** - plan the report page count from day one. The 20-page Attempt 1 was submitted before the limit was properly checked.

---

## 14. GitHub Publication

Published to GitHub in May 2026 after the official mark was confirmed. Publishing before results were released would have carried academic malpractice risk.

Repository: [github.com/zaccesss/two-stage-audio-amplifier](https://github.com/zaccesss/two-stage-audio-amplifier)

All binary files (PDF report, Excel workbooks) were replaced with markdown before publication because the original files contained private credentials. All technical content is preserved in the markdown files.

The GitHub workflow was practised deliberately on every change - issue, branch, commit, push, PR, merge, delete branch - to build the habit before Year 2.

---

*Last updated: May 2026*
