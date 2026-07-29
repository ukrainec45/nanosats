# Open-Source Satellite Projects & Resources

> **Last updated**: July 2026

---

## Quick-Reference: Open-Source Space Solutions

| Project | Type | Size | CAD | OBC | ADCS | Status | Reproducible? | Links |
|---------|------|------|-----|-----|------|--------|---------------|-------|
| **Artemis CubeSat Kit** | Educational kit | 1U | PDF only | RP2040 | None | ✗ Educational | Partial | [Web](https://sites.google.com/hawaii.edu/artemiscubesatkit) |
| **BIRDS** | Full bus | 1U–2U | Eagle | PIC | Magtorquers only | ✓ 6 generations | Partial | [GitHub](https://github.com/BIRDSOpenSource) · [Docs](https://birds-project.com/open-source) |
| **Build a CubeSat** | Full bus | 1U–3U | KiCad | STM32 | Basic | ✗ Educational | **Yes** | [Codeberg](https://codeberg.org/buildacubesat-project) |
| **FossaSat** | Full bus | PocketQube | EasyEDA | STM32 (LoRa) | None | ✓ FossaSat-1/2 in orbit | Mostly | [GitHub](https://github.com/FOSSASystems) |
| **KSF Space CubeSat Kit** | Educational kit (commercial) | 1U | **Closed** | STM32 | Basic | ✗ Commercial | **No** (closed) | [Web](https://ksf.space/cubesat-kit) |
| **LibreCube** | Ecosystem | 1U–3U | KiCad / FreeCAD | Various (ref) | Various (ref) | ✗ Methodology | Yes | [GitLab](https://gitlab.com/librecube) · [Web](https://librecube.org) |
| **OreSat** | Full bus | 1U–3U | KiCad | Octavo A8 (Linux) | Star tracker + RWs + magtorquers | ✓ Flown | Hard | [GitHub](https://github.com/oresat) · [Docs](https://oresat.org) |
| **PICOBUS (LSF)** | Deployer | PocketQube | KiCad | — | — | ✓ Built | **Yes** | [GitLab](https://gitlab.com/librespacefoundation/picobus) |
| **PROVES Kit** | Full bus | 1U–3U | KiCad | RP2040/RP2350 | None (basic) | ✓ NASA missions | **Yes** | [GitHub](https://github.com/proveskit) · [Docs](https://proveskit.github.io) |
| **QUBIK (LSF)** | PocketQube | 1P | KiCad | STM32 | None | ✓ Flown | Mostly | [GitLab](https://gitlab.com/librespacefoundation/qubik) |
| **Sapling (Stanford SSI)** | Full bus | 1U | KiCad | SAMD51 (PyCubed) | Magtorquers | ✓ Flown (2 missions) | Mostly | [GitHub](https://github.com/stanford-ssi/sapling) · [Web](https://saplingsat.org) |
| **SatNOGS (LSF)** | Ground segment | — | KiCad / Eagle | — | — | ✓ Active 2014→ | **Yes** | [GitLab](https://gitlab.com/librespacefoundation/satnogs) · [Web](https://satnogs.org) |
| **SIDLOC (LSF)** | Beacon protocol | — | KiCad | — | — | ✓ Active 2024→ | **Yes** | [GitLab](https://gitlab.com/librespacefoundation/sidloc) · [Web](https://sidloc.space) |
| **UPSat (LSF)** | Full bus | 2U | KiCad | STM32F4 | Magtorquers | ✓ First all-OS satellite | Hard | [GitLab](https://gitlab.com/librespacefoundation/upsat) · [Web](https://upsat.gr) |


---

## Table of Contents

1. [Scope & Licensing](#1-scope--licensing)
2. [Complete Open-Source Satellite Platforms](#2-complete-open-source-satellite-platforms)
3. [Open-Source Onboard Computers (OBC)](#3-open-source-onboard-computers-obc)
4. [Open-Source Electrical Power Systems (EPS)](#4-open-source-electrical-power-systems-eps)
5. [Open-Source Communications](#5-open-source-communications)
6. [Open-Source ADCS](#6-open-source-adcs)
7. [Open-Source Structures & Mechanical](#7-open-source-structures--mechanical)
8. [Open-Source Ground Segment](#8-open-source-ground-segment)
9. [Open-Source Flight Software & Firmware](#9-open-source-flight-software--firmware)
10. [Open-Source Educational & Reference Designs](#10-open-source-educational--reference-designs)
11. [Open Protocols & Standards](#11-open-protocols--standards)
12. [Cross-Reference Table](#12-cross-reference-table)
13. [Appendix: All Sources](#13-appendix-all-sources)

---

## 1. Scope & Licensing

### What qualifies as "open-source" here?

| Tier | Label | Criteria |
|------|-------|----------|
| ★★★ | **Fully open** | CAD, PCB files (KiCad/Eagle), BOM, firmware, enclosure design, and docs all public — with an OSI-approved or FSF-approved license |
| ★★☆ | **Mostly open** | Hardware design files OR firmware open, but not both; some documentation missing |
| ★☆☆ | **Reference only** | Documentation / schematics public but not full design files; useful for inspiration |

### Common licenses used in space open-source

| License | Type | Used By |
|---------|------|---------|
| CERN-OHL-P / CERN-OHL-S / CERN-OHL-W | Hardware | OreSat, Libre Space, PROVES |
| Solderpad Hardware License v0.51 | Hardware | Various (SHL is Apache 2.0-derived) |
| TAPR Open Hardware License | Hardware | Some amateur radio projects |
| GNU GPL v3 / LGPL v3 | Software | FSFW, SatNOGS, GNU Radio |
| BSD 2/3-Clause | Software | NASA cFS, KubOS, COSMOS |
| MIT | Software | PyCubed, many libraries |
| Apache 2.0 | Software | Libre Space SDK, CSP |
| CC-BY-SA 4.0 | Documentation | CDS, many guides |
| Open Government Licence | Documentation | Canadian/UK space agency docs |

### How to verify openness

Before adopting any project, check the repo for:
- **KiCad / Eagle / Altium source files** (not just PDF schematics)
- **BOM with manufacturer part numbers** (not just "resistor 10k")
- **Gerber files or fabrication-ready outputs**
- **Firmware source** (not just hex binaries)
- **Mechanical STEP/STL files** for the enclosure
- **License file** (LICENSE, LICENSE.txt, or LICENSE.md)

---

## 2. Complete Open-Source Satellite Platforms

These projects offer the closest thing to a "turnkey open-source satellite" — full bus designs with HW, SW, and docs.

### 2.1 OreSat — Portland State Aerospace Society (PSAS)

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U, 2U, 3U (OreSat0/0.5); planned larger |
| **Status** | OreSat0.5 launched 2025, OreSat1 in development |
| **Openness** | ★★★ Fully open |
| **License** | CERN-OHL-S v2 (HW), GPL v3 (SW) |
| **Repository** | https://github.com/oresat |
| **Docs** | https://oresat.org |

**What's open:**
- OreSat C3 (OBC) — KiCad files, Octavo A8 system-on-module, Linux-capable
- OreSat EPS (power) — KiCad files, MPPT, battery management
- OreSat ADCS — magnetorquers, reaction wheels, star tracker (HW + SW)
- OreSat Antenna board — UHF deployable antenna
- OreSat Star tracker — dedicated camera board with software
- OreSat Software — ADCS algorithms, CAN bus protocol, ground station tools
- Mechanical CAD — full structure STEP files

**Notes:**
- Uses a distributed CAN bus architecture (each board is a CAN node)
- Designed around a Linux-capable OBC (Octavo A8), with a real-time co-processor
- Excellent documentation; one of the most complete open-source space projects
- Originally 1U/2U focused; scalable concepts applicable to 6U/8U/12U

### 2.2 PROVES Kit — NASA / Pennsylvania State University

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U, 2U, 3U |
| **Status** | Launched on NASA missions, active development |
| **Openness** | ★★★ Fully open |
| **License** | CERN-OHL-P v2 (HW), MIT (SW) |
| **Repository** | https://github.com/proveskit |
| **Docs** | https://proveskit.github.io |

**What's open:**
- Flight Controller Board (RP2040/RP2350) — KiCad source, CircuitPython firmware
- Solar Boards — KiCad source for body-mounted panels
- Antenna Board — UHF deployable dipole
- Sensor Boards — temperature, IMU, current sensing
- PROVES Kit 2 (newer) — improved MCU, more I/O
- Full documentation including assembly guide, BOM, parts sourcing

**Notes:**
- Originally 1U-focused but the modular board designs scale well
- Uses CircuitPython — extremely approachable for beginners
- NASA-developed; flown on multiple missions
- RP2040/RP2350 are low-cost ($1-5) and widely available
- Active community on GitHub Discussions

### 2.3 PyCubed — Stanford / GOMspace / Mahia

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U, 3U (designed for) |
| **Status** | Flown on multiple missions (e.g., ADCSat, other Stanford projects) |
| **Openness** | ★★★ Fully open |
| **License** | MIT (SW), various (HW) |
| **Repository** | https://github.com/pycubed |
| **Website** | https://pycubed.org |

**What's open:**
- PyCubed OBC+EPS all-in-one board — KiCad files, SAMD51 MCU
- CircuitPython firmware — full satellite FSW framework
- Battery management, solar input, power conditioning
- Telemetry and command handling
- Extensive documentation and tutorials

**Notes:**
- Uniquely combines OBC and EPS on a single PC/104 board
- SAMD51 offers good performance at low power
- CircuitPython makes FSW development rapid
- Not specifically designed for 6U/8U/12U but the board design is modular

### 2.4 UPSat — Libre Space Foundation / University of Patras

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 2U |
| **Status** | Launched 2017, deorbited; first all-open-source satellite to fly |
| **Openness** | ★★★ Fully open |
| **License** | CERN-OHL (HW), GPL v3 (SW), CC-BY-SA (docs) |
| **Repository** | https://gitlab.com/librespacefoundation/upsat |
| **Website** | https://upsat.gr |

**What's open:**
- Full satellite bus — OBC, EPS, ADCS, COMMS boards
- KiCad PCB source files
- Mechanical CAD (FreeCAD/STEP)
- Flight software (FreeRTOS-based)
- Ground station software
- Telemetry database

**Notes:**
- First all-open-source satellite to reach orbit
- 2U form factor only, but the architecture (CAN bus, modular boards) scales
- Project is in maintenance mode (post-mission) but all files remain available
- Excellent reference for understanding a complete satellite bus

### 2.5 FossaSat-1 & FossaSat-2 — Fossa Systems

| Attribute | Detail |
|-----------|--------|
| **Form factors** | PocketQube (0.25U, 0.5U) |
| **Status** | FossaSat-1 launched 2019, FossaSat-2 launched 2021 |
| **Openness** | ★★★ Fully open |
| **License** | CERN-OHL (HW), GPL v3 (SW) |
| **Repository** | https://gitlab.com/fossasystems |
| **Website** | https://fossa.systems |

**What's open:**
- Complete satellite hardware (KiCad)
- LoRa-based communications payload
- Solar panel design
- Flight software
- Ground station hardware (Yagi antennas, SDR setup)

**Notes:**
- PocketQube form factor (smaller than CubeSat) but the design concepts apply
- Focus on IoT connectivity using LoRa
- Very low cost budget ($5k–$10k for first satellite)
- Good reference for minimal-power satellite design

### 2.6 PhoneSat — NASA Ames

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U, 2U, 3U |
| **Status** | Phonesat 1.0/2.0 launched 2013; mission complete |
| **Openness** | ★★☆ Mostly open |
| **License** | Various NASA open-source |
| **Repository** | https://github.com/nasa/phonesat |
| **Website** | https://www.nasa.gov/centers/ames/engineering/projects/phonesat |

**What's open:**
- CAD models of the structure
- Electronics designs (Nexus S smartphone as OBC)
- Flight software (Android-based)
- Ground station software
- Mission operations documentation

**Notes:**
- Historic project that proved COTS phones can work in space
- Smartphone-based OBC is no longer practical (newer phones not certified)
- The structural and EPS designs are still valuable references
- Files may be on GitHub but some links are dead; NASA's archive is the canonical source

### 2.7 OSSAT-1 (Open Source Satellite) — Japan / Open Space Agency

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U |
| **Status** | Design complete; launch details uncertain |
| **Openness** | ★★☆ Mostly open |
| **License** | Various |
| **Repository** | https://github.com/ossat |
| **Website** | https://opensat.cc |

**What's open:**
- PCB designs for OBC, EPS, and COMMS
- 3D-printable structure files
- Flight software

**Notes:**
- Japanese effort to create a fully open-source satellite
- Some documentation is in Japanese
- Less active than other projects; check for latest status

### 2.8 Sapling — Stanford Student Space Initiative (SSI)

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U |
| **Status** | Sapling Sempervirens launched Jan 2023 (failed to deploy); Sapling Giganteum launched Apr 2023 (deployed, operated ~2 months) |
| **Openness** | ★★☆ Mostly open — HW open, SW private (under maintenance) |
| **License** | Various (licensing folder in systems repo) |
| **Repository** | https://github.com/stanford-ssi/sapling |
| **Docs** | https://saplingsat.org (Notion wiki) |

**Repositories:**
- **sapling** (umbrella) — README, assets, mission status table
- **sapling-avionics** — KiCad hardware files: BatteryBoard (v01c), PyCubed (modified), SolarPanelBoards, docs
- **sapling-systems** — architectures, CONOPS, trades, analysis, datasheets, licensing
- **sapling-test** — test data and reports
- **sapling-software** — flight, groundstation, and test software (private, "under maintenance")
- **sapling-data** — mission data

**What's open:**
- BatteryBoard — KiCad PCB files, battery management
- SolarPanelBoards — KiCad PCB files, solar panel interfaces
- PyCubed hardware — forked/adapted from the main PyCubed project
- Full systems engineering docs — architectures, trade studies, analyses, CONOPS
- Test data and reports
- Mission data (telemetry)

**Notes:**
- Built on PyCubed (SAMD51) as the OBC+EPS, with custom avionics for battery management and solar panels
- Used sheet metal structure (not 3D-printed or milled)
- Added magnetorquers for ADCS on Giganteum (Sempervirens had none)
- Third mission "Sapling Magnifica" (NET 2023) was in build/test phase with a Raspberry Pi camera payload
- Flight software is not publicly available, limiting full reproducibility
- Good reference for a student-built 1U bus that flew; systems engineering docs are valuable regardless

---

## 3. Open-Source Onboard Computers (OBC)

Standalone OBC boards (separate from full platforms above).

### 3.1 CuteSat OBC — famesy

| Attribute | Detail |
|-----------|--------|
| **MCU** | STM32F4 / STM32H7 |
| **Form factor** | PC/104 |
| **Openness** | ★★★ Fully open |
| **License** | MIT |
| **Repository** | https://github.com/famesy/CuteSat |

**What's open:**
- KiCad PCB files
- Firmware with Hamming ECC
- I2C, SPI, UART, CAN interfaces
- Documentation

### 3.2 CACTUS Open — CubeSat Cookbook

| Attribute | Detail |
|-----------|--------|
| **MCU** | Various (STM32, SAM) |
| **Form factor** | Custom |
| **Openness** | ★☆☆ Reference |
| **License** | Various |
| **Repository** | https://github.com/sandyfreelance/cactus-open |

**What's open:**
- Detailed design documentation ("CubeSat Cookbook")
- Schematic diagrams (PDF)
- Component selection guides
- Not full KiCad source files — more of a reference design

### 3.3 BoardRepo — Cubesat tag

A collection of open-source CubeSat boards maintained by the community:

| Board | Function | MCU | Link |
|-------|----------|-----|------|
| CubeSat- OBC-v1 | OBC | STM32F4 | https://boardrepo.com/tag/cubesat |
| CubeSat-EPS-v1 | EPS | Various | https://boardrepo.com/tag/cubesat |
| CubeSat-COMMS-v1 | UHF radio | CC1120 | https://boardrepo.com/tag/cubesat |
| CubeSat-ADCS-v1 | ADCS controller | STM32F0 | https://boardrepo.com/tag/cubesat |
| CubeSat-Payload-v1 | Payload interface | RP2040 | https://boardrepo.com/tag/cubesat |
| OreSat C3 | OBC | Octavo A8 | https://boardrepo.com/tag/cubesat |
| PROVES FC | OBC | RP2040/RP2350 | https://boardrepo.com/tag/cubesat |
| PyCubed | OBC+EPS | SAMD51 | https://boardrepo.com/tag/cubesat |

**Note:** BoardRepo entries vary in openness — check each repo's license and file availability.

### 3.4 RISC-V OBC (Experimental)

| Attribute | Detail |
|-----------|--------|
| **Project** | Various open-source RISC-V SoC designs |
| **Status** | Academic / experimental |
| **Openness** | ★★☆ Mostly open |
| **Relevance** | Radiation-hardened-by-design RISC-V CPUs could be fabricated on cheaper nodes |

- **PULP platform** (ETH Zurich / University of Bologna): https://pulp-platform.org
- **OpenTitan** (Google / lowRISC): https://opentitan.org
- **SHAKTI** (IIT Madras): https://shaktiproject.org
- **Chipyard** (UC Berkeley): https://chipyard.readthedocs.io

These are not CubeSat-ready but represent the future of open-source space computing.

---

## 4. Open-Source Electrical Power Systems (EPS)

### 4.1 OreSat EPS

Part of the OreSat ecosystem. KiCad design with MPPT, battery management, voltage regulation.
- License: CERN-OHL-S v2
- Repository: https://github.com/oresat/oresat-power-hardware

### 4.2 PROVES Solar Boards

Single-sided FR4 solar panel boards with surface-mount solar cells.
- License: CERN-OHL-P v2
- Repository: https://github.com/proveskit/solar_boards

### 4.3 UPSat EPS

Integrated into the UPSat bus design; battery charging and voltage regulation.
- License: CERN-OHL
- Repository: https://gitlab.com/librespacefoundation/upsat

### 4.4 PyCubed EPS

Integrated with the OBC on a single SAMD51 board. Power conditioning, battery management, solar input.
- License: MIT
- Repository: https://github.com/pycubed

### 4.5 Libre Space QUBIK

A free-form battery pack reference design from Libre Space Foundation.
- Repository: https://gitlab.com/librespacefoundation/qubik
- License: CERN-OHL
- Notes: Custom Li-Ion battery geometry, not a board-mount solution

### 4.6 Build a CubeSat EPS

Part of the Build a CubeSat project (codeberg).
- Repository: https://codeberg.org/buildacubesat-project/bac-eps
- License: Various open-source
- Notes: Simple, beginner-friendly design

### 4.7 MPPT Controller Reference Designs

| Project | Description | Link |
|---------|-------------|------|
| LT3652-based MPPT | Simple solar charger IC reference | https://www.analog.com/en/products/lt3652.html |
| SPV1040 MPPT | Low-power MPPT for small satellites | https://www.st.com/en/power-management/spv1040.html |
| CN3722 MPPT | Li-Ion/LiFePO4 charger | https://www.mouser.com |
| Open Source MPPT (Instructables) | DIY MPPT for satellites | https://www.instructables.com/DIY-MPPT-for-CubeSat |

None of these are space-qualified but can serve as starting points.

---

## 5. Open-Source Communications

### 5.1 Libre Space Foundation — Full Radio Stack

Libre Space Foundation maintains several open-source radio projects:

| Project | Description | License | Link |
|---------|-------------|---------|------|
| **SIDLOC** | Sideral Location — a spread-spectrum beacon/positioning protocol for small satellites | CERN-OHL | https://gitlab.com/librespacefoundation/sidloc |
| **PICOBUS** | A CAN-bus-based intra-satellite communication standard | CERN-OHL | https://gitlab.com/librespacefoundation/picobus |
| **Libre Space SDK** | Software library implementing KISS, CSP, and other satellite protocols | Apache 2.0 | https://gitlab.com/librespacefoundation/librf |

### 5.2 openLST — Google / MST

| Attribute | Detail |
|-----------|--------|
| **Type** | LoRa-based satellite radio |
| **Openness** | ★★★ Fully open |
| **License** | Apache 2.0 |
| **Repository** | https://github.com/google/open-lst |

**What's open:**
- Full radio design (KiCad files)
- FPGA bitstream source (Verilog)
- Firmware
- Ground station adapter design

### 5.3 gr-satellites — Daniel Estevez

| Attribute | Detail |
|-----------|--------|
| **Type** | GNU Radio decoder blocks for >80 satellite protocols |
| **Openness** | ★★★ Fully open |
| **License** | GPL v3 |
| **Repository** | https://github.com/daniestevez/gr-satellites |
| **Docs** | https://destevez.net/tag/gr-satellites |

**What's open:**
- GNU Radio OOT modules for decoding satellite telemetry
- Support for AX.25, LoRa, GMSK, BPSK, and many other modulations
- Constantly updated with new satellite protocols
- Essential tool for any satellite ground station

### 5.4 ARDUSAT — Simple UHF Radio

| Attribute | Detail |
|-----------|--------|
| **Type** | Low-cost UHF transceiver |
| **Openness** | ★★☆ Mostly open |
| **License** | Various |
| **Repository** | https://github.com/ardusat |

**Notes:**
- Arduino-compatible radio board
- Limited to lower data rates
- Good for educational / prototyping

### 5.5 DIY Tape-Spring Antenna References

| Project | Description | Link |
|---------|-------------|------|
| Build a CubeSat antenna | Deployable dipole with tape measure | https://codeberg.org/buildacubesat-project |
| OreSat antenna board | KiCad deployable antenna PCB | https://github.com/oresat |
| PROVES antenna board | PCB-based antenna with burn-wire deployment | https://github.com/proveskit/antenna-board |
| Stanford SSI deployable antenna | Reference design from SSI | https://github.com/stanford-ssi |

### 5.6 SDR-Based Ground Station Radios

| Radio | Frequency Range | Cost | Link |
|-------|----------------|------|------|
| LimeSDR | 0.1–3.8 GHz | $300-600 | https://limemicro.com |
| HackRF One | 1 MHz–6 GHz | $300 | https://greatscottgadgets.com/hackrf |
| PlutoSDR | 70 MHz–6 GHz | $200 | https://analog.com |
| Airspy HF+ Discovery | 0–31 MHz (HF) | $200 | https://airspy.com |
| RTL-SDR Blog V4 | 0.5–1.7 GHz | $30 | https://rtl-sdr.com |

---

## 6. Open-Source ADCS

### 6.1 OreSat ADCS

The most complete open-source ADCS package available.

| Component | What's Open | Link |
|-----------|-------------|------|
| Magnetorquers | KiCad PCB + coil design | https://github.com/oresat/oreSat-adcs-hardware |
| Reaction wheels | KiCad + mechanical CAD | https://github.com/oresat/oreSat-adcs-hardware |
| Star tracker | KiCad camera board | https://github.com/oresat/oreSat-star-tracker-hardware |
| Star tracker SW | Python + OpenCV | https://github.com/oresat/oreSat-star-tracker-software |
| ADCS control SW | C / algorithms | https://github.com/oresat/oreSat-adcs-software |

### 6.2 OpenStartracker

| Attribute | Detail |
|-----------|--------|
| **Type** | Star tracker algorithm |
| **Openness** | ★★★ Fully open |
| **License** | GPL v3 |
| **Repository** | https://github.com/oresat/openstartracker |

**Notes:**
- Developed by PSAS (same team as OreSat)
- Python implementation of lost-in-space star identification
- Can be adapted to any camera + lens combination
- Reference: https://www.overleaf.com/read/zbqxwsvxjyss

### 6.3 STM32-Based ADCS Reference

| Project | Description | Link |
|---------|-------------|------|
| STM32 ADCS board | DIY ADCS with IMU + magnetorquer drivers | https://boardrepo.com/tag/cubesat |
| CubeSat ADCS v1 | BoardRepo entry with STM32F0 | https://boardrepo.com/tag/cubesat |
| DIY Magnetorquer Driver | H-bridge-based (DRV8837) | Open reference from OreSat |

### 6.4 Kalman Filter Libraries

| Library | Language | Use Case | Link |
|---------|----------|----------|------|
| EKF/UKF for attitude | Python | ADCS simulation | https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python |
| OpenSatNav | C++ | Space navigation | https://github.com/opensatnav/opensatnav |
| OreSat ADCS filters | C | Real-time attitude | https://github.com/oresat/oreSat-adcs-software |

---

## 7. Open-Source Structures & Mechanical

### 7.1 OreSat Structure CAD

- Full 1U/2U/3U structure STEP files
- Rail profiles, panel mounts, board stacking
- Repository: https://github.com/oresat (mechanical directories)
- License: CERN-OHL-S v2

### 7.2 Build a CubeSat Structure

- 1U/2U/3U frame design in FreeCAD
- Detailed assembly guide
- Repository: https://codeberg.org/buildacubesat-project/bac-structure
- License: Various open-source

### 7.3 PROVES Kit Mechanical

- 1U/2U stack design
- 3D-printable test jigs
- Repository: https://github.com/proveskit (mechanical directories)
- License: CERN-OHL-P v2

### 7.4 CDS Reference Drawings

- The CubeSat Design Specification includes mechanical drawings for all standard form factors (1U–12U)
- Cal Poly's CDS Rev 14.1 drawings: https://www.cubesat.org/s/CDS-Rev14_1-Drawings.pdf
- These are NOT open-source (copyright Cal Poly) but are the essential reference for any CubeSat structure

### 7.5 FreeCAD Design Resources

| Resource | Description | Link |
|----------|-------------|------|
| FreeCAD | Free & open-source parametric CAD | https://freecad.org |
| CubeSat macro for FreeCAD | Automated CubeSat frame generation | Community scripts |
| STEP file library | NASA models of standard components | https://nasa3d.arc.nasa.gov |

---

## 8. Open-Source Ground Segment

### 8.1 SatNOGS — Libre Space Foundation

| Attribute | Detail |
|-----------|--------|
| **Type** | Global open-source satellite ground station network |
| **Openness** | ★★★ Fully open |
| **License** | AGPL v3 / Open Hardware |
| **Repository** | https://gitlab.com/librespacefoundation/satnogs |
| **Website** | https://satnogs.org |

**What's open:**
- SatNOGS Client — software to schedule and run observations
- SatNOGS Network — centralized observation scheduling
- SatNOGS DB — telemetry database for decoded satellite data
- SatNOGS Rotator — open-source antenna rotator design (3D-printable)
- SatNOGS LNB — low-noise block downconverter design
- Flowgraph — GNU Radio flowgraphs for decoding

**Notes:**
- Global network of >500 ground stations
- You can build your own station and join the network
- Essential for any CubeSat mission for telemetry reception
- Rotator design uses stepper motors and 3D-printed parts (~$100 build cost)

### 8.2 GNU Radio

| Attribute | Detail |
|-----------|--------|
| **Type** | Software-defined radio framework |
| **Openness** | ★★★ Fully open |
| **License** | GPL v3 |
| **Repository** | https://github.com/gnuradio/gnuradio |
| **Website** | https://gnuradio.org |

**What's open:**
- Full DSP framework for implementing radios in software
- OOT (Out-of-Tree) module system for custom modulations
- Extensive library of signal processing blocks
- gr-satellites (see §5.3) provides ready-made satellite decoders

### 8.3 Ground Station Antenna Designs

| Design | Band | Gain | Link |
|--------|------|------|------|
| SatNOGS Yagi | VHF/UHF | 8-12 dBi | https://satnogs.org |
| DIY Cross-Yagi | 437 MHz | 10 dBi | Numerous amateur radio guides |
| Helical antenna | UHF/S-band | 12-18 dBi | https://github.com (various) |
| Offset dish + feed | S-band/X-band | 25-35 dBi | Surplus satellite dishes |
| QFH (Quadrifilar Helix) | VHF | 3-5 dBi | https://jcoppens.com/ant/qfh/index.en.php |

### 8.4 COSMOS — Ball Aerospace (now BAE Systems)

| Attribute | Detail |
|-----------|--------|
| **Type** | Satellite command & control system |
| **Openness** | ★★★ Fully open |
| **License** | BSD-3-Clause / GPL |
| **Repository** | https://github.com/BallAerospace/COSMOS |
| **Website** | https://cosmosrb.com |

**What's open:**
- Full satellite C2 (command and control) framework
- Ruby-based scripting for automated operations
- Telemetry display, command sequencing, logging
- Protocol support for TCP, UDP, serial, CAN

**Notes:**
- Used by NASA, DoD, and commercial operators
- Very mature (20+ years of development)
- Steep learning curve (Ruby)
- Overkill for simple missions but scales to complex constellations

---

## 9. Open-Source Flight Software & Firmware

### 9.1 FSFW (Flight Software Framework) — ESA / DCube

| Attribute | Detail |
|-----------|--------|
| **Type** | C++ satellite flight software framework |
| **Openness** | ★★★ Fully open |
| **License** | GPL v3 (with linking exception) |
| **Repository** | https://github.com/ESA-ACT/fsfw |
| **Docs** | https://fsfw.space |

**What's open:**
- Full C++ framework for satellite onboard software
- HALs for STM32, ARM Cortex-M, Linux
- TM/TC packet handling (CCSDS-compatible)
- PUS (Packet Utilization Standard) services
- Health monitoring, fault detection, mode management
- Device handler framework
- Extensive testing framework

**Notes:**
- Developed by ESA and DCube for actual space missions
- Production-quality; used on several ESA missions
- STM32 target ideal for 6U/8U/12U CubeSat OBCs
- Active development and community

### 9.2 KubOS — Kubos Corporation

| Attribute | Detail |
|-----------|--------|
| **Type** | Linux-based satellite flight software |
| **Openness** | ★★★ Fully open |
| **License** | Apache 2.0 / BSD (components) |
| **Repository** | https://github.com/kubos/kubos |
| **Website** | https://kubos.com |

**What's open:**
- Full satellite FSW distribution (Yocto-based Linux)
- Rust and C SDK for satellite applications
- Telemetry and command database
- Satellite API (hardware abstraction)
- Ground station API
- CI/CD pipelines for satellite software

**Notes:**
- Requires a Linux-capable OBC (e.g., OreSat C3, BeagleBone, Raspberry Pi CM)
- More complex than bare-metal solutions but more capable
- Good for missions needing Linux ecosystem (file systems, networking, etc.)

### 9.3 NASA cFS (core Flight System) — NASA

| Attribute | Detail |
|-----------|--------|
| **Type** | NASA's flight software framework |
| **Openness** | ★★★ Fully open |
| **License** | NASA Open Source Agreement / Apache 2.0 |
| **Repository** | https://github.com/nasa/cfs |
| **Website** | https://cfs.gsfc.nasa.gov |

**What's open:**
- OSAL (Operating System Abstraction Layer)
- PSP (Platform Support Package)
- cFE (core Flight Executive) — application runtime
- Multiple example applications (Housekeeping, Data Storage, etc.)
- CCSDS-compliant telemetry and command

**Notes:**
- Flight-proven on dozens of NASA missions
- Designed for RTEMS, VxWorks, Linux, POSIX
- Large and complex; significant learning curve
- Overkill for simple 1U but appropriate for 6U/8U/12U missions
- Best for teams with prior NASA experience

### 9.4 Nanosat Mission Framework — Boston University

| Attribute | Detail |
|-----------|--------|
| **Type** | Lightweight satellite FSW framework |
| **Openness** | ★★★ Fully open |
| **License** | MIT |
| **Repository** | https://github.com/BostonUniversityAI4Space/Nanosat-Mission-Framework |

**What's open:**
- Task scheduler
- Telemetry manager
- Command handler
- Fault detection
- CAN bus driver
- Python and C implementations

### 9.5 PolySat CW — Cal Poly

| Attribute | Detail |
|-----------|--------|
| **Type** | Satellite command/response software |
| **Openness** | ★★☆ Mostly open |
| **Repository** | https://github.com/PolySat |

**Notes:**
- Developed by Cal Poly's CubeSat lab
- Used on multiple CPx missions
- Not as well documented as other options

### 9.6 PyCubed Firmware Framework

| Attribute | Detail |
|-----------|--------|
| **Type** | CircuitPython-based satellite FSW |
| **Openness** | ★★★ Fully open |
| **License** | MIT |
| **Repository** | https://github.com/pycubed |

**What's open:**
- Python framework for satellite operations
- Hardware drivers for PyCubed board
- Battery management, solar charging, telemetry
- Command/telemetry shell
- Test harness

### 9.7 PROVES Kit Firmware

| Attribute | Detail |
|-----------|--------|
| **Type** | CircuitPython-based FSW for PROVES hardware |
| **Openness** | ★★★ Fully open |
| **License** | MIT |
| **Repository** | https://github.com/proveskit/firmware |

**What's open:**
- Sensor reading
- Battery management
- Radio communication
- Telemetry formatting

---

## 10. Open-Source Educational & Reference Designs

### 10.1 BIRDS Project — Kyutech (Japan)

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U, 2U, 3U |
| **Status** | Multiple BIRDS satellites flown (BIRDS-1 through BIRDS-5+) |
| **Openness** | ★★☆ Mostly open (schematics available but not always full source) |
| **Website** | https://www.kyutech.ac.jp/space |
| **Docs** | https://birds-project.com |

**What's open:**
- Detailed documentation (system design, testing, AIT)
- Some PCB schematics (PDF)
- Ground station designs
- Mission operations manuals
- Highly detailed lessons-learned documents

**Notes:**
- UN-sponsored program training engineers from developing nations
- Excellent documentation quality — among the best available
- Focus on capacity building, not just technology
- BIRDS-3, BIRDS-4, etc. all have publicly released documentation

### 10.2 CuteSat — famesy (Academic)

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 1U (modular) |
| **Openness** | ★★★ Fully open |
| **License** | MIT |
| **Repository** | https://github.com/famesy/CuteSat |

**What's open:**
- KiCad PCB files
- STM32 firmware with Hamming ECC
- Modular board stack design
- Tutorial documentation

### 10.3 QB50 — International CubeSat Network

| Attribute | Detail |
|-----------|--------|
| **Form factors** | 2U, 3U |
| **Status** | 36 CubeSats launched 2014-2018; mission complete |
| **Openness** | ★★☆ Mostly open (varies per participant) |
| **Website** | https://www.qb50.eu |

**What's open:**
- QB50 system requirements and interface documents
- Many participant CubeSats published their designs
- Scientific data is publicly archived
- Some individual CubeSat designs are fully open (e.g., DUTHSat from Delft)

### 10.4 CubeSatSim — CubeSat Simulator

| Attribute | Detail |
|-----------|--------|
| **Type** | Desktop CubeSat simulator (hardware + software) |
| **Openness** | ★★★ Fully open |
| **License** | MIT |
| **Repository** | https://github.com/cubesatsim/cubesatsim |

**What's open:**
- PCB designs for the simulator board
- 3D-printable enclosure
- Python-based ground station software
- Full documentation for building your own simulator

**Notes:**
- NOT a flight design — it's a ground-based training tool
- Excellent for learning satellite operations without risking hardware
- Good testing aid for flight software development

### 10.5 LibreCube — Open-Source CubeSat Framework

| Attribute | Detail |
|-----------|--------|
| **Type** | Open-source satellite development framework |
| **Openness** | ★★★ Fully open |
| **License** | Various (CERN-OHL, GPL, CC-BY-SA) |
| **Repository** | https://gitlab.com/librecube |
| **Website** | https://librecube.space |

**What's open:**
- Satellite simulation environment
- Ground station software
- Mission control software
- Educational tutorials for satellite development
- Reference designs for subsystems

**Notes:**
- More of a development methodology than a specific satellite design
- Good documentation for beginners
- Includes test equipment and procedures

### 10.6 Stanford SSI (Space Systems Initiative)

| Attribute | Detail |
|-----------|--------|
| **Type** | Academic satellite development lab |
| **Openness** | ★★☆ Mostly open |
| **Repository** | https://github.com/stanford-ssi |
| **Website** | https://ssi.stanford.edu |

**What's open:**
- Several CubeSat design repositories
- Reference PCB designs
- Software for satellite operations
- Documentation for student-built satellites

**Notes:**
- Stanford has launched many CubeSats; some designs are publicly shared
- Check individual repos for exact licensing
- PyCubed originated from this group

### 10.7 HSFL (Hawaii Space Flight Laboratory)

| Attribute | Detail |
|-----------|--------|
| **Type** | Academic satellite lab |
| **Openness** | ★★☆ Mostly open |
| **Repository** | https://github.com/hsfl |
| **Website** | https://hsfl.hawaii.edu |

**What's open:**
- Various CubeSat design files
- Software for ground operations
- Documentation from past missions

**Notes:**
- Builds on previous NASA and university experience
- Not as well catalogued as other projects

### 10.8 Build a CubeSat — Codeberg Project

| Attribute | Detail |
|-----------|--------|
| **Type** | Complete beginner-to-orbit guide with open designs |
| **Openness** | ★★★ Fully open |
| **Repository** | https://codeberg.org/buildacubesat-project |
| **Website** | https://codeberg.org/buildacubesat-project/bac-docs |

**What's open:**
- BAC-OBC: OBC design (KiCad)
- BAC-EPS: EPS design (KiCad)
- BAC-COMMS: Radio board design
- BAC-STR: Structure CAD (FreeCAD)
- BAC-GROUND: Ground station design
- BAC-DOCS: Full build documentation
- Comprehensive BOM and parts sourcing

**Notes:**
- Aimed at absolute beginners
- Low-cost design philosophy
- Good for prototyping before scaling to 6U/8U/12U

### 10.9 Artemis CubeSat Kit — University of Hawaii

| Attribute | Detail |
|-----------|--------|
| **Type** | Educational CubeSat kit |
| **Openness** | ★★☆ Mostly open |
| **Website** | https://sites.google.com/hawaii.edu/artemiscubesatkit |

**What's open:**
- Curriculum and teaching materials
- Kit design documentation (some parts)
- Software for the educational kit

**Notes:**
- Educational focus, not flight-ready
- Good as a learning tool before building a real satellite

### 10.10 CubeSat Resources — Community Wiki

| Attribute | Detail |
|-----------|--------|
| **Type** | Curated links to CubeSat resources |
| **Openness** | ★☆☆ Reference |
| **Website** | https://cubesat-resources.space |

**Notes:**
- Aggregated links to open-source and commercial resources
- Not a project itself but a valuable index
- Covers parts, design tools, testing facilities, launch providers

---

## 11. Open Protocols & Standards

### 11.1 CubeSat Design Specification (CDS)

| Attribute | Detail |
|-----------|--------|
| **Type** | Mechanical/electrical interface standard |
| **License** | Free to use (not open-source in the software sense) |
| **Document** | https://www.cubesat.org/s/CDS-REV14_1-2022-02-09.pdf |

**What's covered:**
- Mechanical dimensions for 1U–12U
- Deployer rail specifications
- Separation switch requirements
- Electrical interface (deployer power, kill switch)
- Environmental test requirements
- Mass properties

### 11.2 P-POD Interface

| Attribute | Detail |
|-----------|--------|
| **Type** | Deployer interface standard |
| **Document** | https://www.cubesat.org/s/P-POD_MkIIIRevE_UserGuide_CP-PPODUG-10-1_Rev1.pdf |

### 11.3 SIDLOC — Libre Space Foundation

| Attribute | Detail |
|-----------|--------|
| **Type** | Spread-spectrum beacon / positioning protocol |
| **Openness** | ★★★ Fully open |
| **License** | CERN-OHL |
| **Repository** | https://gitlab.com/librespacefoundation/sidloc |
| **Website** | https://sidloc.space |

**What's open:**
- Protocol specification
- Reference implementation (FPGA Verilog)
- Beacon transmitter hardware design
- Ground receiver design
- Demo and testing tools

**Notes:**
- Designed for locating and identifying small satellites
- Can work with very weak signals (below noise floor)
- Useful for satellite identification after deployment
- Open-source from the ground up

### 11.4 PICOBUS — Libre Space Foundation

| Attribute | Detail |
|-----------|--------|
| **Type** | Intra-satellite CAN bus protocol |
| **Openness** | ★★★ Fully open |
| **License** | CERN-OHL |
| **Repository** | https://gitlab.com/librespacefoundation/picobus |

**What's open:**
- Protocol specification
- Reference hardware design (CAN transceiver)
- Library implementation
- Test harness

**Notes:**
- Based on CAN bus (common in automotive / industrial)
- Designed by Libre Space Foundation (creators of SatNOGS, UPSat)
- Simple, well-documented protocol for satellite internal communication
- Compatible with OreSat architecture (uses CAN bus too)

### 11.5 CSP (CubeSat Space Protocol) — Libre Space Foundation

| Attribute | Detail |
|-----------|--------|
| **Type** | Network protocol for CubeSat internal and ground-link communication |
| **Openness** | ★★★ Fully open |
| **License** | GPL v3 / Apache 2.0 |
| **Repository** | https://gitlab.com/librespacefoundation/csp |
| **Website** | https://libre.space/projects/csp/ |

**What's open:**
- Protocol specification
- C library implementation
- Support for CAN, I2C, UART, KISS, ZMQ
- Encryption support (ChaCha20-Poly1305)
- Routing, fragmentation, HMAC authentication

**Notes:**
- Developed specifically for CubeSat use
- Used by QB50, UPSat, and many other CubeSats
- Very lightweight (suitable for 8-bit MCUs through to Linux)
- Active maintenance

### 11.6 KISS Protocol

| Attribute | Detail |
|-----------|--------|
| **Type** | Simple serial framing for TNC/radio links |
| **Openness** | ★★★ Fully open |
| **Standard** | http://www.ka9q.net/papers/kiss.html |

**Notes:**
- Trivially simple framing (FEND byte, command byte, data, FEND)
- Used by virtually all amateur satellite ground stations
- Supported by gr-satellites, SatNOGS, and all major TNC software

### 11.7 AX.25 Protocol

| Attribute | Detail |
|-----------|--------|
| **Type** | Amateur satellite data link layer |
| **Openness** | ★★★ Fully open |
| **Standard** | https://en.wikipedia.org/wiki/AX.25 |

**Notes:**
- The de facto standard for amateur satellite communications
- Supported by virtually all amateur radio modems
- Low overhead, simple implementation
- Well-understood with many reference implementations

### 11.8 CCSDS Standards

| Attribute | Detail |
|-----------|--------|
| **Type** | Professional satellite communication standards |
| **Openness** | ★☆☆ Reference (standards are not free software) |
| **Website** | https://public.ccsds.org |

**Notes:**
- The gold standard for professional satellite communications
- Complex but extremely capable
- Implemented by NASA cFS, FSFW, and some COSMOS modules
- Many standards are free to download

### 11.9 CIFP (CubeSat Interface & Fit-Check Procedures)

| Attribute | Detail |
|-----------|--------|
| **Type** | Fit-check and integration procedure standard |
| **Document** | https://www.cubesat.org/s/CP-CIFP-20W-Public-Version.pdf |
| **Related** | CACs (CubeSat Acceptance Checklists): https://www.cubesat.org/s/CACs-for-CIFP-March-2020.pdf |

---

## 12. Cross-Reference Table

### By Openness

| Project | HW Open | SW Open | Docs Open | License (HW) | License (SW) | Form Factor |
|---------|---------|---------|-----------|-------------|-------------|-------------|
| **OreSat** | ★★★ | ★★★ | ★★★ | CERN-OHL-S | GPL v3 | 1U–3U |
| **PROVES Kit** | ★★★ | ★★★ | ★★★ | CERN-OHL-P | MIT | 1U–3U |
| **PyCubed** | ★★★ | ★★★ | ★★★ | Various | MIT | 1U–3U |
| **UPSat** | ★★★ | ★★★ | ★★★ | CERN-OHL | GPL v3 | 2U |
| **FossaSat** | ★★★ | ★★★ | ★★★ | CERN-OHL | GPL v3 | PocketQube |
| **CuteSat** | ★★★ | ★★★ | ★★☆ | MIT | MIT | 1U |
| **Build a CubeSat** | ★★★ | ★★★ | ★★★ | Various | Various | 1U–3U |
| **SatNOGS** | ★★★ | ★★★ | ★★★ | CERN-OHL | AGPL v3 | Ground |
| **FSFW** | N/A | ★★★ | ★★★ | N/A | GPL v3 | All |
| **KubOS** | N/A | ★★★ | ★★★ | N/A | Apache 2.0 | All (Linux) |
| **NASA cFS** | N/A | ★★★ | ★★★ | N/A | NASA OSA | All |
| **COSMOS** | N/A | ★★★ | ★★★ | N/A | BSD-3 | Ground |
| **SIDLOC** | ★★★ | ★★★ | ★★★ | CERN-OHL | GPL v3 | Beacon |
| **PICOBUS** | ★★★ | ★★★ | ★★★ | CERN-OHL | GPL v3 | Internal |
| **CSP** | N/A | ★★★ | ★★★ | N/A | Apache 2.0 | All |
| **openLST** | ★★★ | ★★★ | ★★★ | Apache 2.0 | Apache 2.0 | Radio |
| **gr-satellites** | N/A | ★★★ | ★★★ | N/A | GPL v3 | Ground |
| **GNU Radio** | N/A | ★★★ | ★★★ | N/A | GPL v3 | Ground |
| **PhoneSat** | ★★☆ | ★★☆ | ★★☆ | NASA OS | NASA OS | 1U–3U |
| **BIRDS** | ★☆☆ | ★★☆ | ★★★ | Various | Various | 1U–3U |
| **Sapling (Stanford SSI)** | ★★☆ | ★☆☆ | ★★★ | Various | Various | 1U |

### By Form Factor Suitability for 6U/8U/12U

| Project | Direct 6U/8U/12U Support | Scalar? | Notes |
|---------|-------------------------|---------|-------|
| **OreSat** | No (1U–3U) | Yes | Distributed CAN architecture scales linearly |
| **PROVES Kit** | No (1U–3U) | Yes | Modular board stack can be extended |
| **PyCubed** | No (1U–3U) | Partial | Single-board design limits scalability |
| **UPSat** | No (2U) | Yes | CAN bus architecture, modular boards |
| **CDS** | Yes (up to 12U) | N/A | The defining standard for any form factor |
| **FSFW** | N/A | Yes | Framework scales to any size; used on ESA missions |
| **KubOS** | N/A | Yes | Linux-based, suitable for any Linux-capable OBC |
| **NASA cFS** | N/A | Yes | Used on large satellites and CubeSats alike |

### By Subsystem

| Need | Best Open Option | Alternative |
|------|-----------------|-------------|
| OBC (Linux) | OreSat C3 | KubOS + BeagleBone |
| OBC (bare-metal) | PyCubed or CuteSat | PROVES Flight Controller |
| EPS | OreSat EPS or PyCubed | Build a CubeSat EPS |
| Radio (UHF) | OpenLST or DIY LoRa | Upgrade to NanoCom AX100 |
| Radio (S-band) | LimeSDR (COTS) | PlutoSDR |
| ADCS (basic) | OreSat magnetorquers | DIY H-bridge |
| ADCS (fine) | OreSat star tracker + reaction wheels | OpenStartracker |
| Structure | Build a CubeSat or OreSat CAD | Custom from CDS drawings |
| Flight Software | FSFW or PyCubed firmware | KubOS or cFS |
| Ground Station | SatNOGS | COSMOS |
| Beacon | SIDLOC | DIY CW beacon |
| Internal bus | PICOBUS or CSP | Custom CAN protocol |

---

## 13. Appendix: All Sources

### From sources.txt

1. NASA CubeSat 101: https://www.nasa.gov/wp-content/uploads/2017/03/nasa_csli_cubesat_101_508.pdf
2. OreSat GitHub: https://github.com/oresat
3. PROVES Kit GitHub: https://github.com/proveskit
4. Stanford SSI GitHub: https://github.com/stanford-ssi
5. HSFL GitHub: https://github.com/hsfl
6. Artemis CubeSat Kit: https://sites.google.com/hawaii.edu/artemiscubesatkit
7. UPSat GitLab: https://gitlab.com/librespacefoundation/upsat
8. QUBIK GitLab: https://gitlab.com/librespacefoundation/qubik
9. SIDLOC GitLab: https://gitlab.com/librespacefoundation/sidloc
10. Libre Space Projects: https://www.libre.space/projects/
11. PICOBUS GitLab: https://gitlab.com/librespacefoundation/picobus
12. Build a CubeSat: https://codeberg.org/buildacubesat-project/
13. LibreCube GitLab: https://gitlab.com/librecube
14. CubeSat Resources: https://cubesat-resources.space/
15. CDS Rev 14.1: https://static1.squarespace.com/static/5418c831e4b0fa4ecac1bacd/t/62193b7fc9e72e0053f00910/1645820809779/CDS+REV14_1+2022-02-09.pdf
16. CDS Rev 14.1 (mirror): (same as #15)
17. CIFP public version: https://static1.squarespace.com/static/5418c831e4b0fa4ecac1bacd/t/61427114e437672c6d7ae677/1631744277134/CP-CIFP-2.0W+%28Public+Version%29.pdf
18. CACs for CIFP: https://static1.squarespace.com/static/5418c831e4b0fa4ecac1bacd/t/6219419bce2d58468482f692/1645822364544/CACs+for+CIFP+March+2020.pdf

### Open-source projects discovered via research

| # | Project | URL | Category |
|---|---------|-----|----------|
| 19 | SatNOGS | https://satnogs.org | Ground Segment |
| 20 | GNU Radio | https://gnuradio.org | Ground Segment |
| 21 | gr-satellites | https://github.com/daniestevez/gr-satellites | Ground Segment |
| 22 | FSFW (ESA) | https://github.com/ESA-ACT/fsfw | Flight Software |
| 23 | KubOS | https://github.com/kubos/kubos | Flight Software |
| 24 | NASA cFS | https://github.com/nasa/cfs | Flight Software |
| 25 | COSMOS (Ball) | https://github.com/BallAerospace/COSMOS | Ground Segment |
| 26 | PyCubed | https://github.com/pycubed | Platform |
| 27 | openLST (Google) | https://github.com/google/open-lst | Communications |
| 28 | CSP (Libre Space) | https://gitlab.com/librespacefoundation/csp | Protocol |
| 29 | FossaSat | https://gitlab.com/fossasystems | Platform |
| 30 | PhoneSat (NASA) | https://github.com/nasa/phonesat | Platform |
| 31 | BIRDS Project | https://birds-project.com | Educational |
| 32 | QB50 | https://www.qb50.eu | Educational |
| 33 | CubeSatSim | https://github.com/cubesatsim/cubesatsim | Educational |
| 34 | CuteSat | https://github.com/famesy/CuteSat | OBC |
| 35 | CACTUS Open | https://github.com/sandyfreelance/cactus-open | Reference |
| 36 | OSSAT-1 | https://github.com/ossat | Platform |
| 37 | OpenStartracker | https://github.com/oresat/openstartracker | ADCS |
| 38 | Nanosat Mission Framework (BU) | https://github.com/BostonUniversityAI4Space/Nanosat-Mission-Framework | Flight Software |
| 39 | PolySat CW (Cal Poly) | https://github.com/PolySat | Flight Software |
| 40 | BoardRepo (cubesat tag) | https://boardrepo.com/tag/cubesat | Index |
| 41 | PULP Platform | https://pulp-platform.org | Experimental |
| 42 | OpenTitan | https://opentitan.org | Experimental |
| 43 | SHAKTI (IIT Madras) | https://shaktiproject.org | Experimental |
| 44 | Chipyard (UC Berkeley) | https://chipyard.readthedocs.io | Experimental |
| 45 | OpenSatNav | https://github.com/opensatnav/opensatnav | ADCS |
| 46 | Artemis CubeSat Kit | https://sites.google.com/hawaii.edu/artemiscubesatkit | Educational |
| 47 | CubeSat Resources | https://cubesat-resources.space | Index |
| 48 | LibreCube | https://gitlab.com/librecube | Methodology |
| 49 | Libre Space QUBIK | https://gitlab.com/librespacefoundation/qubik | EPS |
| 50 | ARDUSAT | https://github.com/ardusat | Communications |
| 51 | KISS Protocol | http://www.ka9q.net/papers/kiss.html | Protocol |
| 52 | AX.25 | https://en.wikipedia.org/wiki/AX.25 | Protocol |
| 53 | CCSDS | https://public.ccsds.org | Protocol |
| 54 | CDS + CIFP + CAC | https://www.cubesat.org | Standard |
| 55 | Sapling (Stanford SSI) | https://github.com/stanford-ssi/sapling | Platform |


---

*This document is a living catalog. If you know of an open-source satellite project that should be listed here, open an issue or PR on the repository.*
