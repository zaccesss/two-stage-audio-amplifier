# FAQ: Two-Stage Audio Amplifier

> Back to [README.md](README.md) &nbsp;|&nbsp; [DOCUMENTATION.md](DOCUMENTATION.md)

---

## Project Basics

**What is this project?**

A two-stage audio amplifier that takes a line-level signal from a mobile phone headphone output and drives an 8 Ω speaker. The design was completed from hand calculations through Proteus SPICE simulation, breadboard prototyping and a final custom PCB.

**What are the two stages?**

Stage 1 is an inverting active band-pass filter built around a TL071CP operational amplifier. It provides frequency selectivity across the audio range and voltage gain to bring the input signal up to the target output level.

Stage 2 is a unity-gain power buffer built around an OPA551PA operational amplifier. It replicates the Stage 1 output voltage at high current, providing the drive capability needed to power an 8 Ω speaker load.

**What audio source was used?**

An iPhone 14 Pro Max, characterised at 440 Hz with a measured output of 0.872 Vpp.

**What is the target output?**

3 Vpp across an 8 Ω speaker load. The PCB achieved 3.000 Vpp at Stage 1 and 2.980 Vpp at Stage 2, both measured at 440 Hz.

---

## Circuit Design

**Why use a TL071 for Stage 1?**

The TL071 has a JFET input stage giving high input impedance, low input bias current and low noise, all of which are beneficial for audio-frequency work. Its gain-bandwidth product of 3 MHz and slew rate of 13 V/µs are sufficient for the 28.54 kHz upper cutoff frequency of this design.

**Why use an OPA551 for Stage 2?**

The OPA551 can deliver up to ±200 mA continuous output current, which is needed to drive an 8 Ω speaker at 3 Vpp without clipping or thermal shutdown. Standard audio op-amps do not have sufficient current output for this load.

**Can the cutoff frequencies be changed?**

Yes. The lower cutoff frequency (fL = 5 Hz) is set by R2 and C2. The upper cutoff frequency (fH = 28.54 kHz) is set by R1 and C1. Changing either RC pair adjusts the corresponding cutoff. The exact component values are in `design/calculations/Audio Amplifier Design Calculations.xlsx`.

**What supply voltage does the circuit use?**

The final design uses a single supply. The TL071 bias network sets a virtual mid-supply reference at Vcc/2. The supply voltage must be within the operating range of both ICs. Refer to the TL071 and OPA551 datasheets for minimum and maximum supply limits.

**What is the 470 nF capacitor used during testing?**

A 470 nF capacitor was connected in series with the oscilloscope probe tip to AC-couple the measurement. This removes the DC bias offset present in the single-supply design output and allows the oscilloscope to display the AC signal cleanly.

---

## Simulation and Tools

**What software was used?**

Proteus was used for schematic capture, PCB layout and SPICE frequency sweep and time-domain simulation. Microsoft Excel was used for design calculations and frequency response data analysis. Microsoft Word was used for the technical report with IEEE formatting.

**How do I open the Proteus design files?**

Proteus design files (`.pdsprj`) require Labcenter Electronics Proteus to open. The key schematic and PCB views are exported as PNG files in `design/proteus/exports/` for reference without needing Proteus installed.

**How do I open the Excel workbooks?**

Any version of Microsoft Excel or a compatible spreadsheet application. The workbooks in `design/calculations/` contain design calculations, component value derivations and frequency response data.

---

## Repository and Report

**Where is the full technical report?**

The complete technical report is at [report/audio-amplifier-report.pdf](report/audio-amplifier-report.pdf). It covers all design sections, simulation results and measured data with IEEE referencing.

**Where can I see all the project photos?**

The full image gallery is at [media/GALLERY.md](media/GALLERY.md). It includes final assembly photographs, PCB layer views, 3D renders, simulation outputs and oscilloscope traces.

**Can I reuse this design?**

Yes. This project is released under the MIT License. See [LICENSE](LICENSE) for terms.

---

## Contact and Support

Open an issue in this repository for questions or corrections.

You can also reach out directly at offices.isaac@gmail.com.

<p align="center">
  <b>Project Status:</b> Completed &nbsp;|&nbsp; <b>Last Updated:</b> May 2026
</p>
