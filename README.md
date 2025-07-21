# Current Mirror Implementation in Cadence Virtuoso

## Overview

This project demonstrates the implementation and simulation of a **PMOS-based current mirror** using **Cadence Virtuoso**. The design consists of a reference current source and a mirrored output across matched PMOS transistors. The schematic is analyzed using **Spectre Simulator** and annotated for key parameters including drain current (`Id`), gate-source voltage (`Vgs`), drain-source voltage (`Vds`), and transconductance (`gm`).

## Schematic Components

- **PMOS Transistors**:
  - `PM3`: Reference transistor
  - `PM0`, `PM8`: Mirroring transistors
- **NMOS Transistors**:
  - `NM0`, `NM1`: Used for current sinking and biasing
- **Resistor `R0`**: Sets the reference current
- **Voltage Sources**:
  - `Vdd`: Power supply (1.8 V)
  - `V1`: Input source for reference current
  - `V0`: Bias for NMOS (0 V shown in schematic)
<img width="1920" height="1080" alt="Screenshot from 2025-04-08 15-37-10" src="https://github.com/user-attachments/assets/1a242b7a-28ae-4a1d-a791-1d675cf1e1fa" />

## Simulation Details

- **Tool Used**: Cadence Virtuoso with Spectre simulator
- **Simulation Type**: DC Operating Point Analysis
- **Measured Parameters**:
  - `Id`, `Vgs`, `Vds`, `gm`, `Vth` for all transistors
- **Expected Outcome**: 
  - Mirrored current in `PM0` and `PM8` close to `PM3`'s current (~497 µA)
  - Matching `Vgs` of PMOS devices ensures current mirroring

## How to Run

1. **Open Virtuoso** and load the project library containing the `current_mirror` schematic.
2. Launch **ADE L/XL/Explorer**.
3. Set up the **DC analysis**.
4. Add output expressions: `Id(PM0)`, `Id(PM8)`, `Vgs(PM0)`, etc.
5. Run simulation.
6. Use **Annotate > DC Operating Point** to view results in the schematic.

## Results

From the annotated schematic:
- `Id(PM3)` ≈ 497.126 µA
- `Id(PM0)` ≈ 517.204 µA
- `Id(PM8)` ≈ 517.204 µA

This confirms proper current mirroring with minor mismatches due to loading or transistor sizing differences.
