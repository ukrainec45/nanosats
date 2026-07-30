# How to Build a Flight-Ready Satellite (6U / 8U / 12U)

> A comprehensive, step-by-step guide for individuals and small teams who want to build a flight-ready satellite from scratch — without relying on a specialized aerospace company as the prime contractor.
>
> Covers **6U**, **8U**, and **12U** CubeSat form factors.
>
> **Last updated**: July 2026

---

## Table of Contents

1. [Understanding the CubeSat Standard](#1-understanding-the-cubesat-standard)
2. [Core Subsystems — What You Need to Build](#2-core-subsystems--what-you-need-to-build)
3. [Open-Source Projects to Build Upon](#3-open-source-projects-to-build-upon)
4. [Step-by-Step Build Process](#4-step-by-step-build-process)
5. [Kits (If You Want a Head Start)](#5-kits-if-you-want-a-head-start)
6. [Detailed Component Shopping List](#6-detailed-component-shopping-list)
7. [Budget Breakdown](#7-budget-breakdown)
8. [Timeline (Gantt-Style)](#8-timeline)
9. [Learning Path & Resources](#9-learning-path--resources)
10. [Appendix A: Acronyms](#appendix-a-acronyms)
11. [Appendix B: Example Power Budgets by Form Factor](#appendix-b-example-power-budgets-by-form-factor)
12. [Appendix C: Example Link Budget (UHF 437 MHz)](#appendix-c-example-link-budget-uhf-437-mhz)
13. [Appendix D: Deployer Compatibility Checklist](#appendix-d-deployer-compatibility-checklist)
14. [Appendix E: Recommended First Steps](#appendix-e-recommended-first-steps)

---

## 1. Understanding the CubeSat Standard

CubeSats are a standardized class of nanosatellites. The basic unit (1U) is a 10×10×10 cm cube. Your 8U satellite must conform to the **CubeSat Design Specification (CDS)** to fit into a standard deployer.

### Standard Form Factors

| Size | Dimensions | Typical Mass | Typical Use Case |
|------|-----------|-------------|-----------------|
| 1U | 100 × 100 × 100 mm | ≤1.33 kg | Education, tech demo |
| 2U | 100 × 100 × 200 mm | ≤2.66 kg | Simple payloads |
| 3U | 100 × 100 × 300 mm | ≤4.00 kg | Earth observation |
| 6U | 100 × 226.3 × 300 mm or 200 × 200 × 200 mm | ≤8.00 kg | Advanced missions |
| **8U** | **100 × 226.3 × 454 mm** | **≤10-12 kg** | **Multi-payload, propulsion** |
| 12U | 226.3 × 226.3 × 366 mm | ≤24 kg | Constellation, high-capability |
| 16U | 226.3 × 226.3 × 454 mm | ≤29 kg | Complex missions |

### Key Specification Documents

- **CubeSat Design Specification Rev 14.1** (Cal Poly, 2022) — The definitive mechanical and electrical interface standard for 1U–12U CubeSats
  - Direct PDF: https://www.cubesat.org/s/CDS-REV14_1-2022-02-09.pdf
  - Mirror: https://static1.squarespace.com/static/5418c831e4b0fa4ecac1bacd/t/62193b7fc9e72e0053f00910/1645820809779/CDS%2BREV14_1%2B2022-02-09.pdf
- **ISO 17770:2017** — Space systems — Cube satellites (CubeSats):
  - https://www.iso.org/standard/60496.html
- **CubeSat Interface and Fit-Check Procedures (CIFP)**:
  - https://www.cubesat.org/s/CP-CIFP-20W-Public-Version.pdf
- **CubeSat Acceptance Checklists (CAC)**:
  - https://www.cubesat.org/s/CACs-for-CIFP-March-2020.pdf
- **CubeSat Specification Drawings**:
  - https://www.cubesat.org/s/CDS-Rev14_1-Drawings.pdf
- **P-POD User's Guide**:
  - https://www.cubesat.org/s/P-POD_MkIIIRevE_UserGuide_CP-PPODUG-10-1_Rev1.pdf

### 6U-Specific Deployers

6U is one of the most popular CubeSat form factors. The 6U standard has two allowable configurations:
- **6U Type A**: 100 × 226.3 × 300 mm (1×2.3×3 U, most common)
- **6U Type B**: 200 × 200 × 200 mm (2×2×2 U, square profile)

| Deployer | Vendor | Configurations | Link |
|----------|--------|---------------|------|
| **P-POD** | Cal Poly | Up to 6U single (special config) | https://www.cubesat.org/s/P-POD_MkIIIRevE_UserGuide_CP-PPODUG-10-1_Rev1.pdf |
| **DuoPack** | ISISPACE | 2×3U stacking → 6U single | https://satnow.com/products/satellite-deployers/isispace/118-1233-duopack |
| **EXOpod** | Exolaunch | 1×6U, 2×6U, 4×3U | https://exolaunch.com |
| **CSD (Canisterized Satellite Dispenser)** | Rocket Lab | 3U, 6U, 12U | https://rocketlabusa.com |
| **QuadPack** | ISISPACE | 4×3U = 12U, also 2×6U | https://satnow.com/products/satellite-deployers/isispace/118-1233-quadpack |
| **SSIKLOPS** | Sidus Space | 1U–12U flexible | https://satnow.com/products/satellite-deployers/sidus-space/118-1256-ssiklops |
| **NanoSat Deployer (NLAS)** | NASA | 3U, 6U | https://techport.nasa.gov/projects/93929 |

### 6U Structure References

- **EnduroSat 6U Structure**: 100 × 226.3 × 300 mm, hard-anodized aluminum
  - https://www.endurosat.com/products/6u-structure
- **EnduroSat 6U Platform (complete bus)**:
  - https://www.endurosat.com/products/6u-platform
- **ISISPACE 6U Structure**:
  - https://www.isispace.nl/product/6u-cubesat-structure
- **NanoAvionics 6U Bus (M6P)**:
  - https://nanoavionics.com/small-satellite-buses/m6p-nanosatellite-bus
- **Gran Systems 6U Structure**:
  - https://gransystems.com/products/cubesat-structure/6UCubeStructure

### 8U-Specific Deployers

8U is not one of the "round number" sizes (1, 2, 3, 6, 12) but is supported by several deployers:

| Deployer | Vendor | 8U Support | Link |
|----------|--------|-----------|------|
| EXOpod | Exolaunch | 2×8U configuration | https://exolaunch.com |
| CAVE | TRL Space | 2×8U | https://satnow.com/products/satellite-deployers/trl-space/118-1878-cave |
| SSIKLOPS | Sidus Space | 1U–12U | https://satnow.com/products/satellite-deployers/sidus-space/118-1256-ssiklops |

### 8U Structure References

- **EnduroSat 8U Structure**: 100 × 226.3 × 454 mm, 973 g, Aluminum 6082, hard-anodized rails
  - https://www.endurosat.com/products/8u-structure
- **EnduroSat 8U Platform (complete bus)**:
  - https://www.endurosat.com/products/8u-platform
- **Gran Systems 8U Structure**:
  - https://gransystems.com/products/cubesat-structure/8UCubeStructure

### 12U-Specific Deployers

12U is the largest standard CubeSat size in the CDS. It is typically configured as 226.3 × 226.3 × 366 mm (2.3×2.3×3.7 U).

| Deployer | Vendor | Configurations | Link |
|----------|--------|---------------|------|
| **QuadPack** | ISISPACE | 1×12U, 2×6U, 4×3U | https://satnow.com/products/satellite-deployers/isispace/118-1233-quadpack |
| **EXOpod** | Exolaunch | 1×12U, 2×6U, 2×3U+1×6U, 1×16U | https://exolaunch.com |
| **CSD (Canisterized Satellite Dispenser)** | Rocket Lab | 12U, 6U, 3U | https://rocketlabusa.com |
| **RAMI** | UARX Space | 1×12U, 2×6U, 1×6U+2×3U, 4×3U | https://satnow.com/products/satellite-deployers/uarx-space/118-1312-rami |
| **SSIKLOPS** | Sidus Space | 3×12U max (stackable) | https://satnow.com/products/satellite-deployers/sidus-space/118-1256-ssiklops |
| **CAVE** | TRL Space | 1×16U, 2×8U, 1×12U | https://satnow.com/products/satellite-deployers/trl-space/118-1878-cave |

### 12U Structure References

- **EnduroSat 12U XL Structure**: 226.3 × 226.3 × 366 mm, 2.44 kg, Aluminum 6082
  - https://www.endurosat.com/products/12u-structure
- **EnduroSat 12U XL Platform (complete bus)**:
  - https://www.endurosat.com/products/12u-platform
- **Blue Canyon Technologies 12U (XB-12)**: 8U payload volume, 0.002° pointing accuracy
  - https://www.bluecanyontech.com/spacecraft/12u-cubesat
- **NanoAvionics 12U Bus (M12P)**:
  - https://nanoavionics.com/small-satellite-buses/m12p-nanosatellite-bus
- **ISISPACE 12U Structure**:
  - https://www.isispace.nl/product/12u-cubesat-structure

> **Note:** These commercial products are listed as *reference only* — you are building your own. Use their published dimensions to inform your design.

---

## 2. Core Subsystems — What You Need to Build

### 2.1 Structure

The physical frame of your satellite. Must meet CDS mechanical requirements exactly.

**Materials:**

| Material | Pros | Cons | Cost |
|----------|------|------|------|
| Aluminum 6061-T6 | Easy to machine, cheap, good strength | Higher density | $$ |
| Aluminum 7075-T6 | Higher strength, space heritage | More expensive, harder to machine | $$$ |
| Carbon fiber composite | Very stiff, lightweight | Outgassing, conductive debris risk | $$$$ |
| 3D-printed (PEKK/PEEK) | Complex geometries possible | Expensive filament, unproven for 8U | $$$ |

**Design Requirements (per CDS Rev 14.1):**
- 4 deployment rails on ±X faces, hard-anodized (to prevent cold welding in vacuum)
- Rail width: 8.5 mm, Rail flatness: ≤0.1 mm over full length
- Remove-Before-Flight (RBF) pin access
- ≥2 separation/kill switches (depressed inside deployer)
- PC/104-compatible mounting holes for stacking boards
- All protrusions ≤6.5 mm from rails

**Dimensions by Form Factor:**

| Size | External Dimensions | Typical Mass Budget | Rail Length |
|------|-------------------|-------------------|-------------|
| 6U (Type A) | 100 × 226.3 × 300 mm | ~8 kg | ~300 mm |
| 6U (Type B) | 200 × 200 × 200 mm | ~8 kg | ~200 mm |
| 8U | 100 × 226.3 × 454 mm | ~10-12 kg | ~454 mm |
| 12U | 226.3 × 226.3 × 366 mm | ~24 kg | ~366 mm |

**Panel/Board Sizes:**

| Size | Board Envelope (max) | Solar Panel Dimensions |
|------|---------------------|----------------------|
| 6U | 90 × 280 mm (horizontal mounting) | 90 × 290 mm (Type A, 2 side panels + top/bottom) |
| 8U | 90 × 95 mm (PC/104 vertical stacking) | 90 × 200 mm (4 side panels) |
| 12U | 212 × 212 mm (horizontal PCBs) | 215 × 350 mm (2-4 side panels + deployable arrays)

**Open-source reference designs:**
- OreSat structure CAD: https://github.com/oresat (look for mechanical CAD files)
- Build a CubeSat structure files: https://codeberg.org/buildacubesat-project/bac-structure
- PROVES Kit structure: https://github.com/proveskit (solar board dimensions)

**Tools:**
- FreeCAD (free): https://freecad.org
- Onshape (free tier): https://onshape.com
- Fusion 360 (hobbyist license): https://autodesk.com/products/fusion-360

**Manufacturing:**
- Xometry (CNC, 3D printing): https://xometry.com
- SendCutSend (laser/waterjet): https://sendcutsend.com
- PCBWay CNC service: https://pcbway.com
- Local machine shops (search for "CNC machining near me")

### 2.2 Onboard Computer (OBC)

The "brain" of your satellite. Runs flight software, processes data, commands subsystems.

**Microcontroller Options:**

| Chip | Rad Tolerance | Speed | Heritage | Cost |
|------|-------------|-------|----------|------|
| STM32H743 (ARM Cortex-M7) | Moderate with mitigation | 480 MHz | Many CubeSats | ~$15-30 |
| STM32F4 series | Moderate | 180 MHz | Very common | ~$8-20 |
| SAMD51 (ARM Cortex-M4F) | Moderate | 120 MHz | PyCubed uses this | ~$10-15 |
| RP2040 (Raspberry Pi Pico) | Low (shielding needed) | 133 MHz | Grassroots projects | ~$1-4 |
| Raspberry Pi 4/Compute Module | Low (shielding needed) | 1.5 GHz | UNISAT-7 used these | ~$35-75 |

**Radiation Mitigation for COTS MCUs:**
- Software: ECC memory, watchdog timers, triple-redundant voting, periodic reboot
- Hardware: Tantalum shielding, conformal coating for tin whisker prevention
- Reference: https://www.sciencedirect.com/science/article/pii/S0094576523002898
- COTS in space guide: https://passive-components.eu/cots-in-space-the-radiation-barrier
- Radiation hardening strategies: https://cubesat.market/post/how-to-turn-cots-hardware-into-space-grade-rad-hard-in-one-step

**Open-Source OBC Designs:**

| Board | MCU | Features | Link |
|-------|-----|----------|------|
| **PyCubed** | SAMD51 | Flight-proven, CircuitPython, EPS + OBC in one | https://pycubed.org / https://github.com/pycubed |
| **PROVES Flight Controller** | RP2040 → RP2350 | Open source KiCad, CircuitPython | https://github.com/proveskit/flight_controller_board |
| **OreSat C3** | Octavo A8 (ARM) | Linux-capable, CAN bus, star tracker interface | https://github.com/oresat/oresat-c3-hardware |
| **CuteSat** | STM32 | Modular, Hamming ECC, open source | https://github.com/famesy/CuteSat |
| **CACTUS Open** | Various | "CubeSat Cookbook" documentation | https://github.com/sandyfreelance/cactus-open |

**PCB Design Tools:**
- KiCad (free, industry standard): https://kicad.org
- EasyEDA (free, browser-based): https://easyeda.com

**PCB Fabrication:**
- JLCPCB (cheap, 2-4 layer): https://jlcpcb.com
- PCBWay (good for 4-8 layer): https://pcbway.com
- OSH Park (USA, purple boards): https://oshpark.com

**Component Sources:**
- Mouser: https://mouser.com
- DigiKey: https://digikey.com
- LCSC (cheap, Asia): https://lcsc.com
- Adafruit: https://adafruit.com
- SparkFun: https://sparkfun.com

### 2.3 Electrical Power System (EPS)

Generates, stores, and distributes power.

**Solar Panels:**

You cannot efficiently manufacture space-grade solar cells at home. You must buy bare cells and integrate them.

| Cell Type | Efficiency | Cost per cell | Source |
|-----------|-----------|--------------|--------|
| AzurSpace 3G30C (triple-junction GaAs) | ~30% | ~$200-500 | https://azurspace.com |
| Spectrolab UTJ | ~29.5% | ~$200-400 | https://spectrolab.com |
| SolAero Z4J | ~30% | ~$200-500 | https://sg.sol-aero.com |
| CESI CTJ | ~30% | ~$200-500 | https://cesi.net |
| SunPower silicon (COTS) | ~22% | ~$5-20 | https://sunpower.com (less rad-tolerant, shorter orbit life) |

**DIY Solar Panel Assembly:**
- Use bare cells mounted on an aluminum or FR4 substrate
- Cover with CMG (Coverglass with Magnesium Fluoride coating) — protects from radiation
- Bypass diodes per cell string
- Interconnect with silver mesh or kapton-insulated wire
- Reference: https://www.endurosat.com/products/8u-solar-panel (commercial example)
- Reference: https://github.com/proveskit/solar_boards (open-source design)

**Batteries:**

| Type | Energy Density | Heritage | Source |
|------|---------------|----------|--------|
| Panasonic NCR18650B | ~12 Wh | Many CubeSats | https://mouser.com |
| Saft MP 176065 | Space-qualified | ESA heritage | https://saft.com |
| GS Yuasa LVP series | High capacity | JAXA heritage | https://gsyuasa.com |
| LiPo pouch cells (COTS) | High | Balloon/test only | https://hobbyking.com (NOT recommended for flight) |

**EPS Controller — DIY options:**
- Build your own: MPPT charge controller IC (e.g., LT3652, SPV1040), buck converters, LDOs, battery management, current sensing
- Open source reference: PROVES Kit EPS (integrated into flight controller), OreSat power system
- Commercial (reference only): GOMspace PnP EPS, ISISPACE EPS, EnduroSat EPS

**Voltage Rails (typical):**
- 3.3V — MCU, logic
- 5V — radios, cameras
- 12V — ADCS actuators, some payloads
- Battery direct (3.6-4.2V per cell, 7.2-8.4V for 2S) — high-current loads

### 2.4 Communications

The link between your satellite and the ground.

**Frequency Bands:**

| Band | Frequency | Data Rate | License Needed | Use Case |
|------|-----------|-----------|---------------|----------|
| VHF | 144-146 MHz | 1.2-9.6 kbps | Amateur + FCC | Beacon, basic telemetry |
| UHF | 430-440 MHz | 9.6-50 kbps | Amateur + FCC | Primary telemetry/command |
| S-band | 2.0-2.3 GHz | 1-50 Mbps | FCC experimental | High-rate data downlink |
| X-band | 8.0-8.4 GHz | 100+ Mbps | FCC commercial | Large data (imagery) |

**Radio Modules:**

| Module | Band | Power | Interface | Cost | Link |
|--------|------|-------|-----------|------|------|
| LoRa SX1276/SX1262 | UHF | 20 dBm | SPI | ~$10-25 | https://mouser.com |
| HopeRF RFM98W | UHF | 20 dBm | SPI | ~$8-15 | https://hopef.com |
| LiteFEC (GOMspace) | UHF | 30 dBm | UART | ~$800-1,500 | https://gomspace.com |
| ISIS UHF Transceiver | UHF | 30 dBm | CAN | ~$5,000-10,000 | https://isispace.nl |
| NanoCom AX100 | UHF | 30 dBm | UART/I2C | ~$3,000-6,000 | https://gomspace.com |
| LimeSDR | S-band | 10 dBm | USB | ~$300-600 | https://limemicro.com |
| HackRF One | 1 MHz-6 GHz | 10 dBm | USB | ~$300 | https://greatscottgadgets.com/hackrf |
| PlutoSDR | 70 MHz-6 GHz | 10 dBm | USB | ~$200 | https://analog.com |

**Antenna (DIY):**

The most common DIY CubeSat antenna is a **deployable dipole or monopole** made from steel tape measure:

- Material: 0.1-0.2 mm spring steel (from any tape measure) or copper-beryllium strip
- Design references:
  - Deployable dipole design (Hackaday): https://hackaday.io/project/203727-build-a-cubesat
  - OreSat antenna board: https://github.com/oresat
  - PROVES antenna board: https://github.com/proveskit/antenna-board
  - UHF PIFA antenna academic paper: https://techscience.com/cmc/v71n2/45799/html
- Deployment mechanism: Burn wire (nichrome) holding antenna down, melts when current applied
- Test: Measure VSWR with a nanoVNA (https://nanovna.com)

**Protocols:**

| Protocol | Layer | Used For | Notes |
|----------|-------|----------|-------|
| AX.25 | Data link | Amateur satellite standard | https://en.wikipedia.org/wiki/AX.25 |
| KISS | Framing | TNC interface | Simplified AX.25 |
| CCSDS | Full stack | Professional missions | Complex, high overhead |
| LoRaWAN | MAC/PHY | IoT-style links | Easy to implement |
| 9k6 GMSK | Modulation | Common UHF CubeSat rate | Used by many university CubeSats |

### 2.5 Attitude Determination and Control System (ADCS)

Keeps your satellite pointing where it needs to point.

**Approach depends on mission requirements:**

| Requirement | ADCS Complexity | Cost (DIY) | Cost (Commercial) |
|-------------|----------------|-----------|-------------------|
| No pointing (omni antenna) | None | $0 | $0 |
| Coarse (~10° accuracy) | Magnetorquers + sensors | $100-500 | $20,000-50,000 |
| Fine (~1° accuracy) | Reaction wheels + star tracker | $1,000-5,000+ | $50,000-150,000 |
| Precision (~0.01°) | High-end reaction wheels + dual star trackers | Not realistic DIY | $100,000-500,000 |

**Sensors (DIY-able):**

| Sensor | Measures | Example Part | Cost | Link |
|--------|----------|-------------|------|------|
| IMU (6-axis) | Acceleration, rotation | MPU6050 | ~$5 | https://mouser.com |
| Magnetometer | Magnetic field (for detumbling) | MAG3110, HMC5883L | ~$10 | https://adafruit.com |
| Gyroscope | Angular rate | ICM-20948 | ~$15 | https://mouser.com |
| Sun sensor | Sun direction (coarse) | DIY with photodiodes ~4 | ~$20 | Open-source designs |
| GPS | Position, time | u-blox NEO-M9N | ~$40 | https://mouser.com |

**Actuators (DIY-able):**

- **Magnetorquers**: Copper wire coils wrapped around the structure. Current through coil creates magnetic dipole that interacts with Earth's field.
  - Design reference: https://github.com/oresat/oresat-adcs-hardware
  - Wire: AWG 28-32 magnet wire (enameled copper)
  - Driver: H-bridge (DRV8837, L9110S)
  - Cost: ~$20-50 in materials

- **Reaction wheels** (harder DIY):
  - Brushless DC motor + brass/aluminum flywheel
  - PID control loop
  - OreSat reaction wheel design: https://github.com/oresat/oresat-adcs-hardware
  - Cost: ~$100-500 per axis (DIY), $10,000+ per axis (commercial)

**Commercial ADCS (for reference):**

- CubeSpace CubeADCS: https://cubespace.co.za
- Blue Canyon Technologies XACT: https://bluecanyontech.com
- Rocket Lab ADCS: https://rocketlabusa.com
- MAI-100 (Maryland Aerospace): https://mai.aero

**Open-Source ADCS Software:**
- OreSat ADCS software: https://github.com/oresat/oresat-adcs-software
- OreSat star tracker: https://github.com/oresat/oresat-star-tracker-hardware
- OreSat star tracker software: https://github.com/oresat/oresat-star-tracker-software
- OpenStartracker: https://github.com/oresat (based on openstartracker)

### 2.6a Deployable Solar Arrays (12U and Large 8U)

For satellites larger than 6U, **body-mounted solar panels alone may not provide enough power**. Deployable solar arrays (wings that unfold in orbit) can provide 2-10× more power.

**Commercial deployable arrays:**
- EnduroSat 6U Deployable Solar Array: https://www.endurosat.com/products/6u-deployable-solar-array
- ISISPACE Deployable Solar Panels: https://www.isispace.nl/product/deployable-solar-panels
- DHV Technology (custom deployable arrays): https://dhvtechnology.com

**DIY Deployable Array Design Considerations:**
- Deployment mechanism: Spring-loaded hinges + burn wire / paraffin actuator
- Hinge design: Piano hinges with torsion springs, or custom 3D-printed mechanisms
- Panel material: 1 mm aluminum honeycomb or carbon fiber sheet + solar cells
- Inter-panel wiring: Flexible PCBs or kapton-insulated wire with service loops
- Stowing: Panels folded flat against satellite body, held by nichrome burn wire
- Testing: Deploy at least 20× in 1G with gravity compensation (air table or water flotation)
- **Tip**: Watch "Build a CubeSat" YouTube episodes on deployable mechanisms

**Estimated power with deployable arrays:**

| Form Factor | Body Mounted | + Deployable Arrays | Total Peak Power |
|------------|-------------|-------------------|-----------------|
| 6U | 8-18 W | 30-60 W (2 wings × 2 panels) | 38-78 W |
| 8U | 16-24 W | 50-100 W (2 wings × 3 panels) | 66-124 W |
| 12U | 20-40 W | 100-300 W (2 wings × 4-6 panels) | 120-340 W |

### 2.6b Propulsion (For Orbit Changes / Deorbit)

Larger satellites (12U especially) often carry propulsion for orbit adjustments, station-keeping, or deorbiting.

**Propulsion Options:**

| Type | Example | Thrust | Isp | Mass | Cost | Best For |
|------|---------|--------|-----|------|------|----------|
| Cold gas | Custom CO₂ or N₂ tank + nozzle | 10-100 mN | 40-70 s | ~0.5-1 kg | ~$500-2,000 | Small orbit adjustments, deorbit |
| Electric propulsion | BIT-3 (Busek) | 0.5-1 mN | 3,000 s | ~1-2 kg | ~$50k-100k (commercial) | Major orbit changes |
| Green monopropellant | H₂O₂ or LMP-103S | 0.5-5 N | 200-250 s | ~1-3 kg | ~$10k-50k (commercial) | Attitude control + orbit |
| Resistojet | Water vapor or butane | 1-10 mN | 100-150 s | ~0.3-1 kg | ~$1,000-5,000 (DIY) | Station-keeping |
| Solar sail | Reflective Mylar membrane | ~0.001 mN | ∞ | ~0.5 kg | ~$500-2,000 | Attitude control, deorbit (slow) |

**Regulatory note:** If you carry propulsion, you need additional safety approvals from the launch provider and FCC — pressurized vessels and energetic propellants are considered hazardous.

### 2.7 Thermal Control

Space is a thermal nightmare — +100°C in sunlight, -100°C in shadow, cycling every 90 minutes in LEO.

**DIY Thermal Management:**

| Technique | Purpose | Materials | Cost | Source |
|-----------|---------|-----------|------|--------|
| MLI blanket | Insulation | Aluminized Mylar + Kapton/Dacron netting | ~$50-200 | https://mcmaster.com, https://amazon.com |
| Thermal tape | Conduct heat to structure | 3M 8805, Keratherm | ~$20-50 | https://digikey.com |
| White paint | Radiate heat (high emissivity) | Aeroglaze A276, AZ-1 | ~$50-100 | https://mouser.com |
| Black paint | Absorb heat | Aeroglaze Z302 | ~$50-100 | https://mouser.com |
| Kapton heaters | Warm components in eclipse | Polyimide heater film + thermistor | ~$20-50 | https://mcmaster.com |
| Thermal standoffs | Isolate hot components | Nylon/ceramic standoffs | ~$5-20 | https://mcmaster.com |

**Analysis Tools (free):**
- NASA Thermal Desktop (limited free version): https://crtech.com
- ESATAN-TMS (student license): https://www.esa.int
- Simplified hand calculations per SMAD textbook
- Open-source: https://github.com/search?q=thermal+cubesat

### 2.7 Payload

This is WHY you're building the satellite. The payload is your mission.

**Common DIY Payloads:**

| Payload Type | Components | Cost | Complexity |
|-------------|-----------|------|------------|
| Earth imaging camera | Raspberry Pi Camera v3, optics | $50-200 | Low |
| ADS-B receiver (track aircraft) | RTL-SDR + antenna | $30-50 | Low |
| AIS receiver (track ships) | RTL-SDR + antenna | $30-50 | Low |
| GNSS reflectometry | u-blox ZED-F9P | $200-300 | Medium |
| Radiation sensor | Geiger-Muller tube (SBM-20) | $30-100 | Low |
| Magnetometer (science grade) | Fluxgate sensor | $100-500 | Medium |
| IoT LoRa gateway | SX1301 concentrator | $100-300 | Medium |
| Software-defined radio | PlutoSDR / LimeSDR | $200-600 | Medium-High |
| Hyperspectral imager | Custom optics + sensor | $1,000-5,000 | High |

**Radiation Testing for Cameras (critical!):**
- CMOS sensors degrade quickly without shielding
- Reference: UNISAT-7 flew Raspberry Pi cameras successfully with 2 mm aluminum shielding
- Paper: https://www.sciencedirect.com/science/article/pii/S0094576523002898

### 2.8 Ground Station

You need a ground station on Earth to talk to your satellite.

**Minimal Viable Ground Station (~$200-500):**

| Component | Example | Cost | Link |
|-----------|---------|------|------|
| SDR receiver | RTL-SDR Blog V3 | ~$25 | https://rtl-sdr.com |
| Antenna V-dipole (137 MHz) | DIY with tape measure | ~$10 | DIY |
| Antenna Yagi (UHF) | Arrow Antenna 440-5 | ~$100 | https://arrowantennas.com |
| LNA (Low Noise Amplifier) | SAWbird+ HAM | ~$50 | https://nooelec.com |
| Rotator | Yaesu G-450A or DIY | ~$300-1,000 | https://yaesu.com |
| Software | Gpredict + SatDump | Free | See below |

**Software (all free/open source):**

| Tool | Purpose | Link |
|------|---------|------|
| **Gpredict** | Satellite tracking, rotator control | http://gpredict.oz9aec.net |
| **SatDump** | Signal decoding, image processing | https://satdump.org |
| **GNU Radio** | SDR processing framework | https://gnuradio.org |
| **SatNOGS** | Global open ground station network | https://satnogs.org |
| **GPredict + rotator** | Automated antenna pointing | http://gpredict.oz9aec.net |
| **INSPIRE SDR** | Open-source SDR | https://github.com/INSPIRE-SDR |

**Ground Station Guides:**
- Building an amateur ground station: https://aos7.info/article/building-amateur-ground-station-antenna-guide
- Simple CubeSat ground station PDF: http://aiaaocrocketry.org/AIAAOCRocketryDocs/CubeSats/A%20Simple%20and%20Inexpensive%20CubeSat%20Ground%20Station.pdf
- UCI CubeSat ground station: https://github.com/UCI-CubeSat/UCI-CubeSat-Ground-Station
- SatDump beginner guide: https://sdrstore.eu/satdump-v2-rtl-sdr-complete-beginner-setup-guide

---

## 3. Open-Source Projects to Build Upon

These projects publish ALL their files — CAD, PCBs, firmware, software. **Fork them, learn from them, modify them.**

| Project | Scale | Status | What's Available | Link |
|---------|-------|--------|-----------------|------|
| **OreSat** | 1U-2U | ✅ In orbit (OreSat0, OreSat1) | Full KiCad + CAD + software + documentation. The gold standard. | https://oresat.org / https://github.com/oresat |
| **PROVES Kit** | 1U | ✅ Active development | Flight controller, solar boards, antenna board, CircuitPython firmware | https://proveskit.com / https://github.com/proveskit |
| **PyCubed** | 1U-3U | ✅ In orbit (multiple missions) | Single-board satellite computer, CircuitPython, EPS + OBC integrated | https://pycubed.org / https://github.com/pycubed |
| **Build a CubeSat** | 1U | Active (solo dev) | YouTube devlog series (50+ episodes), Codeberg repos, structure + PCBs + software | https://buildacubesat.space / https://codeberg.org/buildacubesat-project / https://youtube.com/@buildacubesat |
| **UPSat** | 1U | ✅ Orbited 2017 | First fully open-source satellite. Files released by Libre Space Foundation | https://upsat.gr / https://libre.space |
| **LibreCube** | 1U-3U | Active (in development) | Open-source CubeSat platform, modular | https://librecube.org |
| **CubeSat Resources** | All | ✅ Curated directory | The single best collection of links, docs, suppliers, standards, papers | https://cubesat-resources.space |
| **CACTUS Open** | 1U | ✅ Documentation | "CubeSat Cookbook" — 4 documents for new teams | https://github.com/sandyfreelance/cactus-open |
| **CuteSat** | 1U | ✅ Design files | STM32-based, Hamming ECC, modular PCBs | https://github.com/famesy/CuteSat |
| **OSSAT OBC** | All | ✅ Hardware design | Open Source Satellite OBC dev board | https://github.com/Open-Source-Satellite/OSSAT_OBC_Dev_Board |
| **BIRDS Project** | 1U | ✅ Multiple launches | Kyushu Institute of Technology's open-source satellite series | https://birdsopensource.github.io |
| **Artemis CubeSat Kit** | 1U-3U | ✅ Active | Hawaii Space Flight Laboratory's open-source kit | https://github.com/hsfl/artemis |
| **NanoAvionics Reference Designs** | 6U-12U | ✅ In orbit | Commercial reference designs (pay for bus, but architecture is public knowledge). M6P (6U), M12P (12U). Valuable for understanding how professional 6U-12U satellites are partitioned | https://nanoavionics.com/small-satellite-buses |
| **EnduroSat Platforms** | 6U-12U | ✅ In orbit | Commercial bus architectures published with payload volume diagrams. Useful design references for understanding 6U/8U/12U internal layout | https://endurosat.com |
| **Blue Canyon XB-12** | 12U | ✅ In orbit | Commercial reference for high-performance 12U architecture. 8U payload volume, 0.002° pointing, deep space capable | https://www.bluecanyontech.com/spacecraft/12u-cubesat |

---

## 4. Step-by-Step Build Process

### Phase 0: Prerequisites (6-12 months)

**Skills you need** (or must learn):

- [ ] **Embedded C/C++ or CircuitPython** — for flight software
- [ ] **PCB design** (KiCad) — for custom boards
- [ ] **CAD** (FreeCAD/Onshape) — for structure
- [ ] **Radio fundamentals** — antenna theory, link budgets, modulation
- [ ] **Ham radio license** — required to transmit to/from orbit

**Study Resources:**
- NASA CubeSat 101 (read this FIRST): https://www.nasa.gov/wp-content/uploads/2017/03/nasa_csli_cubesat_101_508.pdf
- NASA CubeSat Launch Initiative resources: https://www.nasa.gov/kennedy/launch-services-program/cubesat-launch-initiative/cubesat-launch-initiative-resources
- NASA Small Spacecraft Systems Virtual Institute: https://s3vi.ndc.nasa.gov
- S3VI Knowledge Base: https://s3vi.ndc.nasa.gov/ssri-kb
- NASA State of the Art Small Spacecraft Technology report: https://www.nasa.gov/smallsat-institute/sst-soa
- Coursera "Satellite Engineering" (University of Colorado Boulder, free audit): https://coursera.org
- AMSAT (Amateur Radio Satellite org): https://amsat.org
- CubeSat resources: https://cubesat-resources.space/getting-started

**Milestone:** Pass your ham radio technician exam. Study at https://hamstudy.org

### Phase 1: Mission Definition (3-6 months)

Define your mission with a **Concept of Operations (CONOPS)** document.

**Questions to answer:**
1. What does the satellite DO? (Earth imaging, IoT relay, science, tech demo?)
2. What orbit? (LEO ~400-600 km, SSO for Earth obs, ISS orbit?)
3. **What size?** — This is the most consequential decision. Use this guide:
   - **6U (100×226.3×300 mm, ~8 kg)**: Good for single-payload Earth obs, IoT gateway, tech demo. Lower launch cost (~$80k-150k). Simplest to design and test. Sufficient power for most missions.
   - **8U (100×226.3×454 mm, ~12 kg)**: Good for multi-payload missions, propulsion + payload. More internal volume for batteries, larger payloads. Moderate launch cost (~$150k-300k).
   - **12U (226.3×226.3×366 mm, ~24 kg)**: Best for complex missions needing high power (deployable arrays), propulsion, or multiple large instruments. Highest launch cost (~$200k-400k). Requires more complex structural design (card-cage/chassis vs. PC/104 stack).
4. How long should it last? (1 year? 3 years? 5 years?)
5. How does data get to the ground? (UHF beacon? S-band downlink?)
6. Who operates it? (You? A university ground station? SatNOGS network?)

**Deliverables:**
- Mission requirements document (functional + performance requirements)
- System requirements document
- CONOPS document
- Power budget spreadsheet
- Link budget spreadsheet
- Mass budget spreadsheet

**Reference:** NASA CubeSat 101 Chapter 2 covers development process

### Phase 2: Subsystem Design (6-12 months)

Design each subsystem in parallel. Use KiCad for electronics, FreeCAD for structure.

**Design Flow:**
1. **Architecture** — Block diagram of all subsystems, interfaces, data flows
2. **Component selection** — Choose specific MCU, radio module, sensors, batteries
3. **Interface Control Document (ICD)** — Define pinouts, voltage levels, connectors, protocols between boards
4. **Schematic capture** — KiCad Eeschema. Each board gets its own schematic
5. **PCB layout** — KiCad Pcbnew. Follow CDS board size (PC/104 standard)
6. **Structure design** — FreeCAD. Integrate PCB stackup with rails, switches, antennas
7. **Thermal analysis** — Calculate worst-case hot/cold temperatures

**PCB Stackup by Form Factor:**

| Form Factor | Stacking Approach | Board Size | Connector |
|------------|-------------------|-----------|-----------|
| **6U Type A** | Vertical stack (tall and narrow) OR horizontal motherboard+backplane | 90 × 280 mm (vertical) or 90 × 95 mm (horizontal stack) | PC/104 or custom backplane |
| **6U Type B** | Square stack (2×2U cross-section) — 4× the board area of 1U | 190 × 190 mm | PC/104, custom high-density |
| **8U** | Vertical PC/104 stack like 3U but ~50% taller | 90 × 95 mm per board | PC/104 (104-pin) |
| **12U** | Large square boards with card-cage or chassis architecture | 212 × 212 mm | DIN 41612, custom backplane |

**Typical 8U stack** (most common):
- Board-to-board via PC/104 connectors (104-pin ISA bus pinout is common)
- Stack from -Z to +Z: Solar panel, OBC, EPS, Radio, ADCS, Payload, Solar panel
- Each board: 90×95 mm (fits inside 100 mm envelope), 4-6 layers

**Typical 12U layout** (card-cage / chassis):
- Motherboard backplane at bottom with slot-card daughterboards
- Dedicated compartments for battery pack, payload, ADCS, propulsion
- Often uses horizontal panel dividers with thermal management between compartments
- Can accommodate deployable solar arrays (wings) for ~150-300 W power

**Typical 6U layout**:
- Type A: 3U-height boards stacked vertically, or a central OBC card with ribbon cables to peripherals
- Type B: Large square PC/104 boards with 4× the component area per layer

**Component Vendors:**

| Vendor | Specialty | Link |
|--------|-----------|------|
| Mouser | Everything (ICs, passives, connectors) | https://mouser.com |
| DigiKey | Everything | https://digikey.com |
| LCSC | Cheaper for Chinese parts | https://lcsc.com |
| Adafruit | Breakout boards, sensors | https://adafruit.com |
| SparkFun | Breakout boards, GPS | https://sparkfun.com |
| McMaster-Carr | Hardware, fasteners, adhesives | https://mcmaster.com |
| Amazon | Tools, consumables, test equipment | https://amazon.com |

**Testing During Design:**
- Prototype each board as a breakout before committing to the stackup PCB
- Build a flat sat (all boards on bench, connected by wires) as early as possible
- Reference: NASA CubeSat 101 section on FlatSat development (page 24)

### Phase 3: Fabrication (6-12 months)

**Step 1: Fabricate the Structure**
- CNC machine from aluminum billet OR
- Waterjet cut + custom bending OR
- 3D print (PEEK/PEKK) for prototyping (NOT for flight — outgassing concerns)

**Step 2: Manufacture PCBs**
- Order from JLCPCB or PCBWay
- 4-layer boards are standard. 6-layer if you need dense routing and separate ground planes.
- Finish: ENIG (gold) for better reliability than HASL
- Thickness: 1.6 mm standard

**Step 3: Source Components**
- All ICs from Mouser/Digikey
- Connectors: Harwin (space-grade) or Samtec. Avoid cheap Dupont/JST for flight.
- Solar cells: AzurSpace directly (long lead time, order early)

**Step 4: Assemble Boards**
- Option A: Hand solder (doable for 1-2 boards with practice)
- Option B: JLCPCB/PCBWay assembly service (they populate SMD components)
- After assembly: visual inspection, multimeter check for shorts, power-on test with current-limited PSU

**Step 5: Build FlatSat**
- All boards on an anti-static mat, connected with ribbon cables
- Upload flight software
- Test every function: sensor readout, radio TX, power switching, ADCS actuation
- Debug and fix issues here — it's 10x cheaper than fixing in the structure

**Step 6: Integrate into Structure**
- Mount boards with standoffs
- Route wiring with cable ties and strain relief (knots, glue strain relief boots)
- Install separation switches, RBF pin
- Install antennas (folded and held by burn wire)
- Install solar panels (if building your own, bond cells to substrate with space-grade adhesive)
- Close the structure
- Mass measurement — weigh EVERYTHING

**Step 7: Conformal Coating**
- Apply silicone conformal coating (e.g., MG Chemicals 422B) to all PCBs
- Prevents tin whisker shorts, condensation, and conductive contamination
- Cure per manufacturer specs
- Cost: ~$20-50 per can, one can covers many boards

### Phase 4: Testing (6-12 months)

**This is the most critical phase. DO NOT SKIP.**

**Required tests per CubeSat standard:**

| Test | Description | Standard | Cost (rental) | Where |
|------|-------------|----------|--------------|-------|
| Vibration | 8-14 G RMS random, 20-2000 Hz, 3 axes | GEVS (GSFC-STD-7000) | $5,000-20,000 | Aerospace test lab |
| Shock | Half-sine, ~40 G, 6 axes | Mil-STD-810 | $2,000-10,000 | Same |
| Thermal Vacuum (TVAC) | -40°C to +85°C, <1e-5 torr, 3-6 cycles | GEVS | $10,000-30,000 | Vacuum chamber lab |
| Thermal Cycling | -40°C to +85°C at ambient pressure | GEVS | $2,000-10,000 | Thermal chamber |
| RF/EMC | Transmit frequency, power, spurious emissions | FCC Part 25/97 | $2,000-10,000 | Shielded chamber |
| Deployment | Eject from deployer, switch timing, antenna release | CDS + your ICD | $1,000-5,000 | Deployer mockup |

**NASA GEVS Standard:**
- Download: https://standards.nasa.gov/standard/gsfc/gsfc-std-7000

**Testing Guide:**
- NASA CubeSat 101 Chapter 6 covers all certification documentation
- Test as you fly — same configuration, same orientation, same software

**Testing Facilities (USA):**
- NASA Wallops Flight Facility: https://www.nasa.gov/wallops
- Cal Poly CubeSat Lab: https://www.cubesat.org
- University labs (rent: Stanford SSI, CU Boulder, University of Michigan, MIT)
- Commercial: Element Materials (formerly ETS), NTS Labs
- Search for "environmental test lab aerospace" near you

**Self-Testing Options (budget):**

| Test | DIY Approach | Cost |
|------|-------------|------|
| Vibration (sanity) | Subwoofer shaker table — YouTube has DIY plans | $100-500 |
| Thermal cycling | Oven + freezer, manual cycle, datalog temperature | $50-200 |
| Vacuum (partial) | Vacuum chamber from old pressure cooker + vacuum pump | $200-500 |
| RF range test | Walk test: transmit while walking away, measure when signal drops | $0 |
| Deployment test | Spring-loaded jig to simulate deployer ejection | $100-500 |

> **Warning:** DIY testing does NOT qualify you for launch. Launch providers require certified test reports from calibrated equipment. Use DIY tests as development tools.

### Phase 5: Regulatory Compliance (12-18 months — START IMMEDIATELY)

**The regulatory path is not optional and takes longer than the engineering.**

| License/Permit | Issuing Body | Timeline | Cost | Applies If |
|---------------|-------------|----------|------|-----------|
| **Experimental Radio License** | FCC (US) / National Regulator | 6-12 months | $5,000-30,000 | You transmit from orbit |
| **Amateur Radio License** | FCC (US) / National Regulator | 1-4 weeks | ~$15-35 exam fee | Operator needs this |
| **IARU Frequency Coordination** | IARU | 6-9 months | Free (donation suggested) | Using amateur bands |
| **ITU Filing** | ITU | 12+ months | Varies (often handled by regulator) | Non-amateur bands |
| **NOAA Remote Sensing License** | NOAA/US Dept of Commerce | 6-9 months | Free application | Camera/Earth observation |
| **Orbital Debris Assessment Report (ODAR)** | FCC/NASA | 3-6 months | Free (your time) | ALL satellites |
| **Launch Services Agreement** | Launch Provider | 12-24 months before launch | $0-50k paperwork fee | ALL launches |
| **ITAR Compliance** | US State Dept | Ongoing | $1,000-10,000+ | US person/organization |

**Key Links:**

| Resource | Link |
|----------|------|
| FCC Space Bureau | https://fcc.gov/space |
| FCC Small Satellite Licensing Guidance | https://fcc.gov/document/guidance-obtaining-licenses-small-satellites |
| FCC Fact Sheet — Modernizing Spectrum Sharing for Satellites | https://docs.fcc.gov/public/attachments/DOC-420708A1.pdf |
| IARU Satellite Coordination | https://iaru.org/on-the-air/satellites |
| ITU Small Satellite Support | https://itu.int/en/ITU-R/space/support/smallsat |
| ITU Amateur & Amateur-Satellite Handbook (2026) | https://itu.int/pub/R-HDB-52-2026 |
| NOAA Remote Sensing Licensing | https://space.commerce.gov/regulations/commercial-remote-sensing-regulatory-affairs/licensing |
| Space-Track (orbital debris, TLEs) | https://space-track.org |
| NASA Debris Assessment Software (DAS) | https://orbitaldebris.jsc.nasa.gov/mitigation/das.html |

**2026 Regulatory Guides:**
- Astrolytics FCC Guide 2026: https://astrolytics.space/2026/01/02/fcc-regulations-for-cubesat-and-smallsat-operators-the-2026-complete-guide
- Astrolytics FCC Compliance Checklist 2026: https://astrolytics.space/2026/01/02/fcc-compliance-checklist-for-cubesat-and-smallsat-missions-2026-edition
- Blackwing Space Licensing Guide (student-friendly): https://blackwingspace.com/insight/22-fcc-licensing-and-frequency-coordination-for-cubesats-a-student-friendly-guide
- Bright Ascension regulatory overview: https://brightascension.com/can-i-create-my-own-satellite

**Licensing Strategy Recommendations:**
1. Use **amateur bands** (UHF 430-440 MHz) — simpler licensing path for first missions
2. Team must have at least one licensed ham radio operator
3. Start IARU coordination at least 9 months before planned launch
4. Use a launch broker (Exolaunch, Spaceflight Inc.) — they handle much of the regulatory paperwork

### Phase 6: Launch Procurement (12-24 months before launch)

**Launch Providers:**

| Provider | Vehicle | 6U Cost | 8U Cost | 12U Cost | Link |
|----------|---------|---------|---------|----------|------|
| **SpaceX Rideshare** | Falcon 9 Transporter | ~$275k for 50 kg block. 6U ~6 kg → ~$33k | ~$55k-66k (8U ~10-12 kg) | ~$80k-132k (12U ~12-24 kg) | https://spacex.com/rideshare |
| **Rocket Lab** | Electron | ~$80k/kg → ~$480k dedicated | ~$800k-960k dedicated | ~$960k-1.9M dedicated | https://rocketlabusa.com |
| **Exolaunch (broker)** | Falcon 9, various | ~$80k-150k (includes integration) | ~$150k-300k | ~$200k-400k | https://exolaunch.com |
| **NanoRacks** | ISS deployment | ~$90k/U → ~$540k (ISS orbit only) | ~$720k (limited orbit) | ~$1.08M (limits apply) | https://nanoracks.com |
| **Spaceflight Inc.** | Falcon 9, various | ~$80k-150k | ~$150k-300k | ~$200k-400k | https://spaceflight.com |
| **D-Orbit** | Various | ~$60k-120k (quote-based) | ~$100k-200k | ~$150k-300k | https://dorbit.space |
| **ISISPACE** | Various (as broker) | ~$80k-150k | ~$150k-250k | ~$200k-350k | https://isispace.nl |

**NASA CubeSat Launch Initiative (CSLI):**
- Free launch for US educational institutions (highly competitive, ~20% selection rate)
- Application info: https://www.nasa.gov/announcement-of-partnership-opportunity-for-cubesat-launch-initiative
- Resources: https://www.nasa.gov/kennedy/launch-services-program/cubesat-launch-initiative/cubesat-launch-initiative-resources

### Phase 7: Operations

**Before launch:**
- Practice with your ground station daily — track existing satellites, decode their signals
- Document every procedure: power-on sequence, emergency procedures, nominal pass procedure

**Commissioning (first 30 days in orbit):**
1. Wait for the deployer to eject you (this may take hours to days after launch)
2. Satellite should auto-start after separation switch release
3. First task: Deploy antenna (burn wire)
4. First communication: Listen for beacon. You may need to wait for a pass over your ground station.
5. Verify: Power OK, OBC alive, radio working, solar panels charging
6. Upload configuration: Set time, orbit parameters, ADCS parameters
7. Activate payload: Take first image, make first measurement

**Normal Operations:**
- 4-8 passes per day over your ground station (each 5-15 minutes)
- Schedule: Uplink commands → downlink telemetry → downlink payload data
- Monitor: Battery voltage, temperatures, radio signal strength, pointing accuracy

**Software Tools:**

| Tool | Purpose | Link |
|------|---------|------|
| Gpredict | Pass prediction, rotator control | http://gpredict.oz9aec.net |
| SatDump | Signal recording and decoding | https://satdump.org |
| SatNOGS | Networked ground stations | https://satnogs.org |
| GNU Radio | Custom signal processing | https://gnuradio.org |
| GPredict User Guide | Documentation | http://gpredict.oz9aec.net/documentation.php |
| INSPIRE SDR | Open-source SDR for satellites | https://github.com/INSPIRE-SDR |

**Deorbit Planning:**
- Per FCC/NASA rules, your satellite must deorbit within 25 years of mission end
- For LEO <600 km: atmospheric drag will naturally deorbit within ~5-25 years depending on altitude
- For higher orbits: you need a deorbit mechanism (drag sail, propulsion, or tether)
- Document your deorbit plan in the ODAR (Orbital Debris Assessment Report)

---

## 5. Kits (If You Want a Head Start)

These kits are NOT flight-ready (except PROVES and KSF Space), but they teach you the architecture:

| Kit | Price | What You Get | Flight-Capable? | Link |
|-----|-------|-------------|-----------------|------|
| **MySat** | ~$260-1,150 | 1U educational CubeSat model, PCBs, firmware, 3D files, open source | ❌ No (educational) | https://mysatkit.com |
| **E-Cube** | ~$85 | Non-flight nano-sat kit, 30+ experiments, Arduino-based | ❌ No (educational) | https://hackster.io/anta-rikch/e-cube-build-your-own-nano-satellite-439a91 |
| **Hex-Star CubeSat** | ~$47 (₹3,999) | STEM kit, 10×10×10cm, web interface, sensor data | ❌ No (educational) | https://hexstaruniverse.com/product/cubesat-kit |
| **PROVES Kit** | ~$1,000+ | Flight controller, solar boards, antenna, CircuitPython, open source | ✅ Yes (flight-proven design) | https://proveskit.com / https://github.com/proveskit |
| **KSF Space CubeSat Builder** | Contact for pricing | 1U-3U, GEVS tested, NEP certification, cleanroom-ready | ✅ Yes (flight hardware) | https://ksf.space |
| **Build a CubeSat Dev Kit** | TBD (Aug 2026) | Open-source 1U development kit, ongoing YouTube series | ⚠️ In development | https://buildacubesat.space |
| **OreSat** | Free (open source) | All design files, no physical kit. Build it yourself. | ✅ Yes (in orbit) | https://oresat.org / https://github.com/oresat |

---

## 6. Detailed Component Shopping List

### Structure

| Item | Recommendation | 6U Qty | 8U Qty | 12U Qty | Unit Cost | Link |
|------|---------------|--------|--------|---------|-----------|------|
| Aluminum plate 6061-T6, 0.250" thick | For CNC machining rails + panels | 1.5 sq ft | 2 sq ft | 3 sq ft | $50 | https://mcmaster.com |
| Kill switches | SMC/SMT type, per CDS | 4 | 4 | 6 | $15 | https://digikey.com |
| RBF pin assembly | Metal pin + lanyard | 1 | 1 | 1 | $20 | https://mcmaster.com |
| Standoffs, M2.5, hex, various lengths | Board stacking (PC/104 pattern) | 40 | 50 | 60 | $0.50 | https://mcmaster.com |
| Screws, M2.5 x 6mm, pan head, 18-8 SS | Structure assembly | 80 | 100 | 150 | $0.15 | https://mcmaster.com |
| Helicoil inserts | Thread reinforcement in aluminum | 16 | 20 | 30 | $2 | https://mcmaster.com |
| **Structure subtotal (6U)** | | | | | **~$205** | |
| **Structure subtotal (8U)** | | | | | **~$260** | |
| **Structure subtotal (12U)** | | | | | **~$375** | |

### OBC (DIY — design your own board)

| Item | Recommendation | Qty | Unit Cost | Total | Link |
|------|---------------|-----|-----------|-------|------|
| MCU | STM32H743VIT6 | 3 | $25 | $75 | https://mouser.com |
| PCB fabrication (4-layer, ENIG) | 100×95 mm, qty 10 | 10 | $15 | $150 | https://jlcpcb.com |
| PCB assembly (SMD stencil + paste) | Assumption: you hand-solder | 1 | $50 | $50 | https://jlcpcb.com |
| SDRAM (ISSI IS42S16160) | 32 MB for OBC | 5 | $8 | $40 | https://mouser.com |
| Flash (W25Q128) | 16 MB for firmware storage | 5 | $3 | $15 | https://mouser.com |
| Ferrite beads, caps, resistors, LEDs | Passives | 1 kit | $50 | $50 | https://mouser.com |
| PC/104 connector (104-pin) | Board-to-board stacking | 10 | $8 | $80 | https://digikey.com |
| **OBC subtotal** | | | | **~$460** | |

### EPS

| Item | Recommendation | 6U Qty | 8U Qty | 12U Qty | Unit Cost | Link |
|------|---------------|--------|--------|---------|-----------|------|
| Solar cells (bare, triple-junction GaAs) | AzurSpace 3G30C 10×20 mm | 12 cells (2 panels) | 24 cells (4 panels) | 48 cells (6 panels + deployables) | $250 | https://azurspace.com |
| Coverglass for solar cells | CMG, anti-reflective coating | 12 pcs | 24 pcs | 48 pcs | $50 | Custom order |
| Solar panel PCB substrate | Al-clad PCB | 4 | 8 | 12 | $20 | https://pcbway.com |
| Battery Li-ion 18650 | Panasonic NCR18650B (3.7V, 3.4Ah) | 6 | 8 | 16 | $12 | https://mouser.com |
| Battery protection PCB (BMS) | 3S or 4S BMS with balancing | 2 | 2 | 4 | $25 | https://amazon.com |
| MPPT charge controller IC | LT3652 or SPV1040 | 3 | 5 | 8 | $10 | https://mouser.com |
| Buck converter IC | TPS62160 (3.3V), TPS62130 (5V) | 8 | 10 | 16 | $4 | https://mouser.com |
| Current sense IC | INA219 or INA3221 | 3 | 5 | 8 | $5 | https://mouser.com |
| LDO regulator | LP5907 for sensitive analog | 3 | 5 | 8 | $2 | https://mouser.com |
| Diodes, caps, inductors for EPS | Passives kit | 1 | 1 | 2 | $100 | https://mouser.com |
| **EPS subtotal (6U)** | | | | | **~$4,100** | |
| **EPS subtotal (8U)** | | | | | **~$7,731** | |
| **EPS subtotal (12U)** | | | | | **~$15,060** | |

> **Note:** Solar cells are the single most expensive item. Look on ESA or NASA surplus auctions for used cells at discount. Some university teams share/split cell orders. 12U often uses **deployable solar arrays** (wing panels that unfold in orbit) for additional power — these add significant cost and complexity.

### Communications

| Item | Recommendation | 6U Qty | 8U Qty | 12U Qty | Unit Cost | Link |
|------|---------------|--------|--------|---------|-----------|------|
| UHF radio module | HopeRF RFM98W (LoRa, 433 MHz, 20 dBm) | 3 | 5 | 5 | $12 | https://mouser.com |
| Power amplifier (PA) | RF5110G (gives +30 dBm / 1W output) | 2 | 3 | 5 | $8 | https://mouser.com |
| S-band radio module (12U optional upgrade) | LimeSDR or PlutoSDR | — | — | 1 | $300 | https://limemicro.com |
| Antenna deploy mechanism | Nichrome wire (AWG 32) | 1m | 2m | 2m | $5/m | https://mcmaster.com |
| Antenna material | Steel tape measure (0.1mm thick, 6mm wide) | 1 roll | 1 roll | 2 rolls | $10 | https://amazon.com |
| SMA connectors | PCB-mount, edge-mount | 6 | 10 | 12 | $3 | https://digikey.com |
| Coaxial cable | RG-178 (thin, flexible, low loss) | 1m | 2m | 3m | $5/m | https://mouser.com |
| **Comms subtotal (6U, UHF only)** | | | | | **~$102** | |
| **Comms subtotal (8U, UHF only)** | | | | | **~$144** | |
| **Comms subtotal (12U, UHF + S-band)** | | | | | **~$484** | |

### ADCS

| Item | Recommendation | 6U Qty | 8U Qty | 12U Qty | Unit Cost | Link |
|------|---------------|--------|--------|---------|-----------|------|
| IMU | ICM-20948 (9-axis accel/gyro/mag) | 2 | 3 | 3 | $12 | https://mouser.com |
| Magnetometer | RM3100 (better than HMC5883L, I2C) | 2 | 2 | 3 | $25 | https://digikey.com |
| Magnetorquer wire | AWG 28 magnet wire, 1 lb spool | 1 | 1 | 2 | $25 | https://mouser.com |
| H-bridge driver (for magnetorquers) | DRV8837 | 6 | 8 | 12 | $3 | https://mouser.com |
| GPS module | u-blox NEO-M9N (10m accuracy in LEO) | 1 | 2 | 2 | $40 | https://mouser.com |
| Sun sensor (DIY) | Photodiodes (BPW21R) + op-amp (TLV2374) | 4 | 6 | 8 | $5 | https://mouser.com |
| Reaction wheel kit (12U upgrade) | BLDC motor + flywheel + driver (per axis) | — | — | 3 | $200 | https://mouser.com + DIY |
| **ADCS subtotal (6U, coarse)** | | | | | **~$189** | |
| **ADCS subtotal (8U, coarse)** | | | | | **~$245** | |
| **ADCS subtotal (12U, fine)** | | | | | **~$889** | |

### Thermal

| Item | Recommendation | Qty | Unit Cost | Total | Link |
|------|---------------|-----|-----------|-------|------|
| MLI blanket | 20-layer aluminized Mylar + Dacron net | 1 sq m | $100 | $100 | https://amazon.com |
| Thermal tape | 3M 8805 (conductive) | 1 roll | $30 | $30 | https://digikey.com |
| Kapton heater film | Polyimide, 5W, 5V, 20×20mm | 4 | $15 | $60 | https://mcmaster.com |
| Thermistors | 10k NTC, epoxy bead | 10 | $2 | $20 | https://mouser.com |
| MLI fasteners (snaps/buttons) | Sew-on, for MLI blanket assembly | 10 | $2 | $20 | https://amazon.com |
| Temperature sensor IC | DS18B20 (digital, 1-Wire) | 8 | $4 | $32 | https://mouser.com |
| **Thermal subtotal** | | | | **~$262** | |

### Ground Station

| Item | Recommendation | Qty | Unit Cost | Total | Link |
|------|---------------|-----|-----------|-------|------|
| SDR receiver | RTL-SDR Blog V3 (R820T2+RTL2832U) | 1 | $25 | $25 | https://rtl-sdr.com |
| UHF Yagi antenna | Arrow Antenna 440-5 (5-element, 440-450 MHz) | 1 | $100 | $100 | https://arrowantennas.com |
| LNA + filter combo | Nooelec SAWbird+ HAM (UHF band) | 1 | $50 | $50 | https://nooelec.com |
| Coaxial cable | LMR-240, 50 ohm, 50 ft with connectors | 50 ft | $1/ft | $50 | https://mouser.com |
| USB extender | Active USB 3.0, 15m | 1 | $30 | $30 | https://amazon.com |
| Antenna rotator (optional) | Yaesu G-450A or SpiderRotator DIY | 1 | $400 | $400 | https://yaesu.com |
| Transceiver (for uplink) | ICOM IC-9100 or similar (used market) | 1 | $1,500 | $1,500 | https://icomamerica.com |
| TNC (if using AX.25) | Kantronics KPC-9612+ (used) | 1 | $200 | $200 | https://kantronics.com |
| **Ground station subtotal (minimal)** | | | | **~$255** | |
| **Ground station subtotal (full duplex)** | | | | **~$2,355** | |

### Testing

| Item | Note | Cost |
|------|------|------|
| Vibration test rental | Professional lab, 3 axes, full GEVS profile | $10,000-20,000 |
| TVAC test rental | Thermal vacuum chamber, 3-6 cycles | $15,000-30,000 |
| RF test rental | Shielded chamber, spectrum analysis | $3,000-10,000 |
| Shipping to/from test facility | | $1,000-3,000 |
| **Testing subtotal** | | **~$29,000-63,000** |

### Hardware Total Summary by Form Factor

| Subsystem | 6U (DIY) | 8U (DIY) | 12U (DIY) | Notes |
|-----------|---------|---------|----------|-------|
| Structure | ~$205 | ~$260 | ~$375 | More material for larger frames |
| OBC | ~$460 | ~$460 | ~$460 | Same OBC scales to any size |
| EPS (with commercial solar cells) | ~$4,100 | ~$7,731 | ~$15,060 | +deployable arrays for 12U |
| Communications | ~$102 | ~$144 | ~$484 | 12U may add S-band |
| ADCS (coarse, DIY) | ~$189 | ~$245 | ~$889 | 12U may need reaction wheels |
| Thermal | ~$200 | ~$262 | ~$400 | Larger surface area |
| Ground station (minimal) | ~$255 | ~$255 | ~$500 | 12U may need dish for S-band |
| **Hardware total** | **~$5,511** | **~$9,357** | **~$18,168** | |

> **Note:** These hardware totals do NOT include testing ($34k-57k), licensing ($5k-20k), or launch ($80k-400k depending on size).

### Mass Budget Estimate by Form Factor

| Subsystem | 6U (kg) | 8U (kg) | 12U (kg) |
|-----------|---------|---------|----------|
| Structure | 0.6 | 1.0 | 2.5 |
| EPS (solar panels + batteries + boards) | 1.0 | 2.0 | 4.0 |
| OBC + wiring | 0.2 | 0.3 | 0.5 |
| Radio + antenna | 0.2 | 0.3 | 0.6 |
| ADCS | 0.3 | 0.4 | 1.0 |
| Thermal | 0.1 | 0.15 | 0.3 |
| Payload | 1.0-2.0 | 1.0-4.0 | 3.0-12.0 |
| **Total dry mass** | **~3.4-4.4 kg** | **~5.2-8.2 kg** | **~11.9-20.9 kg** |
| **Deployer limit** | **8 kg** | **12 kg** | **24 kg** |

---

## 7. Budget Breakdown

### Full Mission Cost Comparison (6U / 8U / 12U)

| Category | 6U (DIY) | 8U (DIY) | 12U (DIY) | Notes |
|----------|---------|---------|----------|-------|
| **Hardware** | | | | |
| Structure | $800 | $1,000 | $1,500 | More material for larger sizes |
| Solar panels + EPS | $1,500 | $2,000 | $3,000 | 6U: 2-3 panels, 12U: 4-6 panels + deployables |
| OBC | $500 | $500 | $500 | Same OBC can scale |
| Radio | $1,000 | $1,000 | $1,500 | 12U may need S-band |
| ADCS | $500 | $500 | $1,000 | Larger satellites need more torque |
| Antenna | $100 | $100 | $200 | 12U may need higher-gain antenna |
| Payload | $500-2,000 | $500-2,000 | $1,000-5,000 | 12U can carry more/bigger payloads |
| Ground station | $3,000 | $3,000 | $5,000 | Higher data rates need better dishes |
| **Hardware subtotal** | **~$7,900** | **~$8,600** | **~$13,700** | |
| **Testing** | | | | |
| Vibration | $12,000 | $15,000 | $20,000 | Larger mass = more expensive testing |
| TVAC | $15,000 | $20,000 | $25,000 | Larger volume = larger chamber needed |
| RF/EMC | $5,000 | $5,000 | $8,000 | |
| Shipping + logistics | $2,000 | $3,000 | $4,000 | |
| **Testing subtotal** | **~$34,000** | **~$43,000** | **~$57,000** | |
| **Regulatory** | | | | |
| FCC experimental license | $5,000 | $5,000 | $10,000 | Higher power/complexity may cost more |
| IARU coordination | $0 | $0 | $0 | |
| ITU filing | $0-10,000 | $0-10,000 | $0-10,000 | |
| NOAA remote sensing | $0 | $0 | $0 | |
| Orbital debris report | $0 | $0 | $0 | |
| **Regulatory subtotal** | **~$5,000-15,000** | **~$5,000-15,000** | **~$10,000-20,000** | |
| **Launch (rideshare)** | **~$80,000-150,000** | **~$150,000-300,000** | **~$200,000-400,000** | Heavier = more expensive |
| **GRAND TOTAL (DIY)** | **~$127,000-207,000** | **~$207,000-367,000** | **~$281,000-491,000** | |
| **GRAND TOTAL (commercial bus)** | **~$300,000-600,000** | **~$400,000-900,000** | **~$600,000-1,500,000** | Buying instead of building |

### Cost Reduction Strategies

1. **Rideshare, don't buy dedicated** — Saves 50-90% on launch
2. **Build a flat sat first** — Fix bugs before committing to flight hardware
3. **Use amateur bands** — Dramatically simpler licensing than commercial bands
4. **Use existing open-source designs** — Don't reinvent the OBC, fork PyCubed
5. **Balloon test first** — Validate hardware at 30 km for ~$500-2,000 before committing to orbital launch
6. **Partner with a university** — Access to testing facilities, experienced teams, grant funding
7. **Government surplus** — Check GSA Auctions for used test equipment
8. **NASA CSLI** — Free launch if selected (US only, educational)

---

## 8. Timeline

### Gantt-Style Timeline (First-Time Solo Builder, 8U)

```
Year 1                Year 2                Year 3                Year 4+
|   Q1  Q2  Q3  Q4  |   Q1  Q2  Q3  Q4  |   Q1  Q2  Q3  Q4  |   Q1  Q2  Q3  Q4  |
|---------------------|---------------------|---------------------|---------------------|
[Learn: CubeSat 101, ham license, KiCad, CAD]
[Define mission, write requirements]
[Design subsystems: OBC, EPS, comms, ADCS]
[Design structure and stackup]
[Prototype — breadboard → flat sat]
[Design v2 based on flat sat lessons]
[Fabricate flight boards + structure]
[Assemble engineering unit]
[TESTING: vibration, TVAC, RF, deployment]
[Apply fixes from testing]
[Assemble flight unit]
[FCC / IARU / regulatory — START DAY 1]
[                                                                    ]
[Secure launch (12-24 months before flight)]
[                                                                          ]
[Deliver to launch integrator]
[Launch]
[Commissioning + operations]
```

### Milestone Summary

| # | Milestone | Duration | Est. End |
|---|-----------|----------|----------|
| 1 | Learn fundamentals + get ham license | 6-12 months | End Year 1 |
| 2 | Mission definition + requirements | 3-6 months | Mid Year 1 |
| 3 | Subsystem design (KiCad, CAD) | 6-12 months | End Year 1 |
| 4 | Flat sat prototype + software | 6 months | Mid Year 2 |
| 5 | Design iteration + flight boards | 6 months | End Year 2 |
| 6 | Structure fabrication | 3 months | End Year 2 |
| 7 | Assembly + integration | 3-6 months | Mid Year 3 |
| 8 | Environmental testing (vibe/TVAC/RF) | 6 months | End Year 3 |
| 9 | Regulatory approvals (continues throughout) | 18+ months | End Year 3 |
| 10 | Launch contract + delivery | 12-24 months | Year 3-4 |
| 11 | Launch | — | Year 4+ |
| 12 | Commissioning + operations | 30+ days | After launch |

---

## 9. Learning Path & Resources

### Essential Reading (in order)

| Resource | Type | Time | Link |
|----------|------|------|------|
| **NASA CubeSat 101** | Free PDF | 2-3 days | https://www.nasa.gov/wp-content/uploads/2017/03/nasa_csli_cubesat_101_508.pdf |
| **CubeSat Design Specification Rev 14.1** | Free PDF | 1 day | https://www.cubesat.org/s/CDS-REV14_1-2022-02-09.pdf |
| **CubeSat Resources** | Website | Ongoing | https://cubesat-resources.space |
| **DIY Satellite Platforms** (Sandy Antunes) | Book (~$25) | 1-2 weeks | https://amazon.com/DIY-Satellite-Platforms-Space-Ready-Picosatellite/dp/1449310605 |
| **CubeSat Handbook** (Cappelletti et al.) | Book (~$120) | 2-4 weeks | https://amazon.com |
| **Space Mission Analysis and Design (SMAD)** | Book (~$150) | Reference | https://amazon.com |

### Free Online Courses

| Course | Platform | Content | Link |
|--------|----------|---------|------|
| Satellite Engineering | Coursera (CU Boulder) | Free audit. Orbits, comms, AOCS, structures | https://coursera.org |
| Introduction to CubeSats | NASA (self-paced) | Videos, lesson plans | https://nasa.gov |
| CubeSat 101 (video series) | NASA S3VI | Short videos covering basics | https://youtube.com |
| Ham radio technician license | HamStudy.org | Study for your exam | https://hamstudy.org |

### YouTube Channels

| Channel | Creator | Content | Link |
|---------|---------|---------|------|
| **Build a CubeSat** | Manuel Imboden | Full devlog series: KiCad, CAD, firmware, testing. 50+ episodes. | https://youtube.com/@buildacubesat |
| **Pocket Science** | Various | Space engineering tutorials | https://youtube.com |
| **NASA SmallSat** | NASA | CubeSat missions and education | https://youtube.com/@NASA |
| **Spaceflight** | Spaceflight Inc. | Launch videos, industry updates | https://youtube.com |
| **GreatScott!** | GreatScott | Electronics and PCB design tutorials | https://youtube.com |
| **EEVblog** | Dave Jones | Electronics engineering fundamentals | https://youtube.com |

### Communities

| Community | Platform | Purpose | Link |
|-----------|----------|---------|------|
| r/cubesat | Reddit | CubeSat Q&A and discussion | https://reddit.com/r/cubesat |
| r/amateurradio | Reddit | Ham radio license help, radio questions | https://reddit.com/r/amateurradio |
| r/satellites | Reddit | General satellite discussion | https://reddit.com/r/satellites |
| r/space | Reddit | Space news and discussion | https://reddit.com/r/space |
| CubeSat Discord | Discord | Build a CubeSat community chat | https://discord.gg/yeusgM75ys |
| AMSAT | Organization | Amateur satellite community | https://amsat.org |
| Libre Space Foundation | Organization | Open-source space projects | https://libre.space |
| SatNOGS Community | Web | Global open ground station network | https://satnogs.org |

### Conferences

| Conference | When | Where | Cost | Link |
|-----------|------|-------|------|------|
| **SmallSat Conference** | August | Logan, Utah, USA | ~$500-1,000 | https://smallsat.org |
| **CubeSat Developers Workshop** | April | San Luis Obispo, CA, USA | ~$400-800 | https://cubesatdw.org |
| **Space Symposium** | April | Colorado Springs, CO, USA | ~$1,500+ | https://spacesymposium.org |
| **IAC (International Astronautical Congress)** | October | Rotating locations | ~$800-2,000 | https://iafastro.org |

### Key Standards Documents

| Standard | Contents | Link |
|----------|----------|------|
| GEVS GSFC-STD-7000 | General Environmental Verification Standard (testing) | https://standards.nasa.gov/standard/gsfc/gsfc-std-7000 |
| CubeSat Design Specification Rev 14.1 | Mechanical/electrical interface | https://www.cubesat.org/s/CDS-REV14_1-2022-02-09.pdf |
| NASA STD-8719.14 | Orbital debris mitigation | https://orbitaldebris.jsc.nasa.gov |
| Mil-STD-810 | Environmental testing methods | https://everyspec.com |
| FCC Part 97 | Amateur radio service rules | https://ecfr.gov |
| FCC Part 25 | Satellite communications | https://ecfr.gov |

### Tools (all free or low-cost)

| Tool | Use | Cost | Link |
|------|-----|------|------|
| KiCad | PCB design | Free | https://kicad.org |
| FreeCAD | 3D mechanical design | Free | https://freecad.org |
| Onshape | Cloud-based CAD | Free (hobbyist) | https://onshape.com |
| GNU Radio | SDR signal processing | Free | https://gnuradio.org |
| Gpredict | Satellite pass prediction | Free | http://gpredict.oz9aec.net |
| SatDump | Satellite signal decoding | Free | https://satdump.org |
| GMAT (NASA) | Orbit simulation | Free | https://gmat.nasa.gov |
| STK (AGI) | Professional orbit analysis | Free (educational) | https://agi.com |
| MATLAB/Simulink | Simulation and modeling | $149 (student) | https://mathworks.com |
| QGIS | Mapping / Earth obs data processing | Free | https://qgis.org |
| Audacity | Audio/Digital signal analysis | Free | https://audacityteam.org |
| Arduino IDE | MCU programming | Free | https://arduino.cc |
| PlatformIO | Embedded dev environment | Free | https://platformio.org |

---

## Appendix A: Acronyms

| Acronym | Meaning |
|---------|---------|
| ADCS | Attitude Determination and Control System |
| CDS | CubeSat Design Specification |
| CONOPS | Concept of Operations |
| COTS | Commercial Off-The-Shelf |
| CSLI | CubeSat Launch Initiative (NASA) |
| EPS | Electrical Power System |
| FCC | Federal Communications Commission |
| GEVS | General Environmental Verification Standard |
| GNC | Guidance, Navigation, and Control |
| ICD | Interface Control Document |
| IARU | International Amateur Radio Union |
| ITU | International Telecommunication Union |
| LEO | Low Earth Orbit |
| MLI | Multi-Layer Insulation |
| MPPT | Maximum Power Point Tracking |
| OBC | On-Board Computer |
| ODAR | Orbital Debris Assessment Report |
| P-POD | Poly Picosatellite Orbital Deployer |
| RBF | Remove Before Flight |
| SDR | Software-Defined Radio |
| SSO | Sun-Synchronous Orbit |
| TID | Total Ionizing Dose (radiation) |
| TLE | Two-Line Element (orbit data) |
| TVAC | Thermal Vacuum |
| UHF | Ultra High Frequency |
| VHF | Very High Frequency |

---

## Appendix B: Example Power Budgets by Form Factor

### 6U Power Budget

| Subsystem | Idle (mW) | Active (mW) | Duty Cycle | Avg. Power (mW) |
|-----------|----------|------------|------------|-----------------|
| OBC (STM32H7) | 200 | 800 | 100% | 800 |
| EPS (quiescent) | 50 | 200 | 100% | 200 |
| UHF radio (Rx) | 100 | 300 | 50% | 200 |
| UHF radio (Tx) | 100 | 1,500 | 5% | 170 |
| ADCS sensors | 100 | 300 | 100% | 300 |
| ADCS magnetorquers | 0 | 500 | 10% | 50 |
| Payload (camera) | 0 | 2,000 | 1% | 20 |
| Thermal (heaters) | 0 | 3,000 | 10% (eclipse) | 300 |
| **Total avg. power** | | | | **~2,040 mW** |

**Solar generation (6U, 2-3 panels):**
- Panel area: ~2 × 90 × 290 mm = 52,200 mm² (Type A, 2 side panels)
- Power per panel: ~4-6 W
- Total 6U array power (peak): ~8-18 W
- Average orbit power: ~5-11 W

**Battery capacity (6U):**
- 6× NCR18650B in 3S2P: ~6.8 Ah at 11.1V = ~75 Wh
- Eclipse consumption: ~1.2 Wh per 35 min eclipse
- Battery provides ~65 hours of eclipse operations

### 8U Power Budget

| Subsystem | Idle (mW) | Active (mW) | Duty Cycle | Avg. Power (mW) |
|-----------|----------|------------|------------|-----------------|
| OBC (STM32H7) | 200 | 800 | 100% | 800 |
| EPS (quiescent) | 50 | 200 | 100% | 200 |
| UHF radio (Rx) | 100 | 300 | 50% | 200 |
| UHF radio (Tx) | 100 | 1,500 | 5% | 170 |
| ADCS sensors | 100 | 300 | 100% | 300 |
| ADCS magnetorquers | 0 | 500 | 10% | 50 |
| Payload (camera) | 0 | 2,000 | 1% | 20 |
| Thermal (heaters) | 0 | 5,000 | 10% (eclipse) | 500 |
| **Total avg. power** | | | | **~2,240 mW** |

**Solar generation (8U, 4 panels):**
- Panel area: ~4 × 90 × 200 mm = 72,000 mm²
- Solar cell efficiency: 30%
- Power per panel (direct sun): ~4-6 W
- Total 8U array power (peak): ~16-24 W
- Average orbit power (60% sun, 40% eclipse): ~10-14 W

**Battery capacity (8U):**
- 8× NCR18650B in 4S2P: ~7.2 Ah at 14.8V = ~107 Wh
- Eclipse consumption: ~1.3 Wh per 35 min eclipse
- Battery provides ~80 hours of eclipse operations

### 12U Power Budget

| Subsystem | Idle (mW) | Active (mW) | Duty Cycle | Avg. Power (mW) |
|-----------|----------|------------|------------|-----------------|
| OBC (STM32H7) | 200 | 800 | 100% | 800 |
| EPS (quiescent) | 100 | 400 | 100% | 400 |
| UHF radio (Rx) | 100 | 300 | 30% | 160 |
| UHF radio (Tx) | 100 | 1,500 | 5% | 170 |
| S-band radio (Tx) | 1,000 | 5,000 | 5% | 1,200 |
| ADCS sensors | 200 | 500 | 100% | 500 |
| ADCS reaction wheels | 500 | 5,000 | 10% | 1,000 |
| Payload (higher capability) | 100 | 5,000 | 2% | 200 |
| Thermal (heaters) | 0 | 10,000 | 10% (eclipse) | 1,000 |
| **Total avg. power** | | | | **~5,430 mW** |

**Solar generation (12U, body-mounted + deployable arrays):**
- Body-mounted: ~4 × 215 × 350 mm = 301,000 mm²
- Deployable solar arrays (optional): 2 wings × 3 panels each × 200 × 300 mm = 360,000 mm²
- Total panel area: up to 0.66 m²
- Power per m²: ~300 W/m²
- Total 12U array power (peak): ~50-200 W (with deployable wings)
- Average orbit power: ~30-120 W

**Battery capacity (12U):**
- 16× NCR18650B in 4S4P: ~14.4 Ah at 14.8V = ~213 Wh
- Eclipse consumption: ~3.2 Wh per 35 min eclipse
- Battery provides ~65 hours of eclipse operations

---

## Appendix C: Example Link Budget (UHF 437 MHz)

| Parameter | Value | Units |
|-----------|-------|-------|
| Frequency | 437 | MHz |
| TX Power (satellite) | 30 | dBm (1W) |
| TX Antenna Gain | 2 | dBi |
| TX Line Loss | 0.5 | dB |
| EIRP | 31.5 | dBm |
| Distance (500 km, 10° elevation) | 1,500 | km |
| Free Space Path Loss | 148.9 | dB |
| Atmospheric Loss | 0.5 | dB |
| RX Antenna Gain (ground Yagi) | 10 | dBi |
| RX Line Loss | 1 | dB |
| RX LNA Noise Figure | 0.5 | dB |
| RX Noise Temperature | 290 | K |
| Required SNR (for 9.6 kbps) | 10 | dB |
| **Link Margin** | **~5-10 dB** | ✅ Feasible |

---

## Appendix D: Deployer Compatibility Checklist

Before designing your structure, verify against your target deployer:

**Checklist by Form Factor:**

| Check | 6U (Type A) | 6U (Type B) | 8U | 12U |
|-------|------------|------------|-----|-----|
| External dimensions | 100×226.3×300 mm | 200×200×200 mm | 100×226.3×454 mm | 226.3×226.3×366 mm |
| Max mass | 8 kg | 8 kg | 12 kg | 24 kg |
| Rail length | 300 mm | 200 mm | 454 mm | 366 mm |
| Deployer examples | P-POD, DuoPack, EXOpod | SSIKLOPS, custom | EXOpod, CAVE | QuadPack, EXOpod, CSD, RAMI |

**Common Checklist (all form factors):**

- [ ] External dimensions match deployer envelope (see table above)
- [ ] Rail width: 8.5 mm ±0.1 mm
- [ ] Rail surface finish: hard anodized
- [ ] Rail flatness: ≤0.1 mm over full length
- [ ] All protrusions ≤6.5 mm from rail surface
- [ ] Separation switches: ≥2, depressed ≥6.5 mm when in deployer
- [ ] RBF pin accessible with deployer door closed
- [ ] Mass ≤ deployer limit (see table above)
- [ ] Center of gravity within ±20 mm of geometric center (±10 mm for some deployers)
- [ ] No sharp edges that could catch on deployer
- [ ] Deployable antennas fully constrained until separation
- [ ] Timeline: antenna deploy ≥30 seconds after separation switch release
- [ ] No hazardous materials (no pressurized vessels, no explosives without special approval)

---

## Appendix E: Recommended First Steps

### Week 1
1. Read NASA CubeSat 101: https://www.nasa.gov/wp-content/uploads/2017/03/nasa_csli_cubesat_101_508.pdf
2. Download and read CDS Rev 14.1: https://www.cubesat.org/s/CDS-REV14_1-2022-02-09.pdf
3. **Decide on form factor (6U, 8U, or 12U)** — this drives every other design decision. Pick based on:
   - **6U**: Lower cost (~$127k-207k total), popular form factor, many compatible deployers, sufficient for most Earth observation and IoT missions
   - **8U**: Good balance of volume and cost (~$207k-367k total), supports multi-payload missions with moderate propulsion
   - **12U**: Maximum capability (~$281k-491k total), supports complex payloads, higher power budgets, deployable solar arrays, propulsion systems for orbit changes
4. Sign up for ham study: https://hamstudy.org

### Week 2
4. Install KiCad: https://kicad.org
5. Install FreeCAD: https://freecad.org
6. Fork OreSat GitHub: https://github.com/oresat
7. Start watching Build a CubeSat YouTube series: https://youtube.com/@buildacubesat

### Month 1
8. Pass ham radio technician exam
9. Buy RTL-SDR and listen to a satellite pass: https://rtl-sdr.com
10. Design a simple breakout board in KiCad, order from JLCPCB
11. Join the CubeSat Discord: https://discord.gg/yeusgM75ys

### Month 2-3
12. Build a flat sat with an ESP32 + LoRa module + sensors on a breadboard
13. Receive data from an existing satellite (NOAA APT, Meteor LRPT, or ISS)
14. Build a 137 MHz V-dipole antenna and decode weather satellite images with SatDump
15. Define your mission objective and write requirements

### Month 4-6
16. Design your first version of OBC in KiCad
17. Design structure in FreeCAD (even just a simple panel layout)
18. Start FCC licensing research — read the Astrolytics guide
19. Contact a launch broker (Exolaunch or Spaceflight Inc.) for a preliminary quote

---

*This document is a living guide. The open-source satellite community is active and evolving. Always check the latest resources before making design decisions. Good luck — space is hard, but it belongs to everyone.*
