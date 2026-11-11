# Changelog

All notable changes to this project are recorded here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

## [0.3.0] - 2026-11-11

### Fixed

- The README stack icons load from the icon project's own repository at a fixed commit. The old host refuses every request, so they showed as broken images

## [0.2.1] - 2026-11-09

### Fixed

- Output power is 141 mW average (9 / 64 W). 281 mW was the peak figure
- Peak current for 3 Vpp across 8 Ω is 187.5 mA, not 375 mA
- The results tables no longer call the 0.872 Vpp to 2.980 Vpp reading unity gain: that is the overall gain and Stage 2 alone is 3.000 Vpp to 2.980 Vpp
- The C8 cut-off (9.04 Hz) sits above the filter's 6.63 Hz, so the two combine to about 12 Hz
- D2 and D3 are described from the schematic as clamps on the OPA551 output
- The phone table now has the real reading for every volume step
- Component designators and values in the documentation match the report's bill of materials
- Gain figures agree between the report text and its comparison table. The summary table in the documentation is filled in
- Supply figures, the 29 kHz target, the low output impedance wording and the wording on why the workbooks were replaced

## [0.2.0] - 2026-11-03

### Added

- A signal-flow diagram in the README: phone source, TL071 band-pass stage, OPA551 buffer and the 8 Ω speaker
- The Proteus PCB layout and 3D views as images in `media/images/`

### Changed

- The Proteus exports live in `media/images/` with the other figures and the `design/` folder is gone; the duplicate schematic export is removed
- Routine tidy-up

### Fixed

- The lower cutoff frequency reads 6.63 Hz, the value set by the 1 µF capacitor used for C2, with 5 Hz kept as the design target, matching the report

## [0.1.2] - 2026-08-12

### Changed

- Badge row rebuilt as flat, left-aligned status, licence, version and DOI badges instead of a centred box of large badges
- DOI badge now uses the Zenodo concept DOI, which always resolves to the latest release

## [0.1.1] - 2026-08-12

### Added

- Community health files, markdown lint configuration and issue and pull request templates
- CITATION.cff and a Citing This Work section
- Registered the repository with Zenodo for a permanent, citable DOI

### Changed

- Tech Stack section now uses an animated icon table
- Contact and Attribution sections presented as callouts

## [0.1.0] - 2026-05-09

### Added

- Initial release: full technical report, Proteus design files, PCB layout exports and build documentation for the two-stage audio amplifier
