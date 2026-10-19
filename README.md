# picoloader — hardware

Open-hardware design files for **picoloader**, an RP2040 based board and its companion
flex PCB. The main board carries a USB-C receptacle, a QSPI flash device and a 30-pin
0.5 mm FFC connector; the flex plugs into that FFC and, on the other end, taps the game
console's DVD-drive flex connector (footprint symbol `GamecubeConnectors:DVDFlexCN`).

All projects are **KiCad 10** (PCB format `20260206`, schematic format `20260306`).

## Hardware revisions

| Folder | Revision | Board size | Footprints | QSPI flash | Notes |
| --- | --- | --- | --- | --- | --- |
| [`hw/v1.1/`](hw/v1.1) | v1.1 | 27.21 × 36.04 mm | 37 | ZD25WQ16CEIGR (2 MB) / W25Q256JVEIQ (32 MB), USON-8 3×2 mm | All footprints drawn in the project's own `Library.pretty` |
| [`hw/v1.1A/`](hw/v1.1A) | v1.1A | 27.21 × 36.04 mm | 39 | ZD25WQ128CEIGR (16 MB) / W25Q256JVEIQ (32 MB), USON-8 3×2 mm | Footprints migrated to standard KiCad libraries, silkscreen artwork added |
| [`hw/v1.2A/`](hw/v1.2A) | v1.2A | 27.21 × 36.04 mm | 39 | ZD25WQ128CEIGR (16 MB) / W25Q256JVEIQ (32 MB), WSON-8 6×5 mm P1.27 | Flash package enlarged to WSON-8 6×5 mm |
| [`hw/flex/`](hw/flex) | flex | 98.46 × 61.01 mm | 2 | — | Shared 30-pin FFC flex, `DVDFlexCN` pads on the console side |

## Component summary (main board)

| Designator | Part | Package |
| --- | --- | --- |
| U3 | RP2040 | QFN-56 7×7 mm P0.4 mm |
| FLASH1 | ZD25WQ128CEIGR / W25Q256JVEIQ | USON-8 3×2 mm (v1.1, v1.1A), WSON-8 6×5 mm (v1.2A) |
| U1 | AP2112K-3.3TRG1 LDO | SOT-23-5 |
| Y1 | 12 MHz crystal | SMD 3225 |
| J1 | 30-pin 0.5 mm FFC | Hirose FH12-30S-0.5SH-1 |
| USB2 | USB-C receptacle | HRO TYPE-C-31-M-12 |
| J2, RSW1 | Tactile switch | Panasonic TSA343G00-250J2 |
| D1, D3 | 1N5819WS Schottky | SOD-323 |
| D2 | Indicator LED | 0603 |
| TP3–TP5 | Test points | 1.0 mm pad |

Power is taken from the USB-C connector through the LDO; the board also has 23 discrete
resistors and capacitors (0402/0603).

## Repository layout

```
.
├── LICENSE                  CERN-OHL-P-2.0
├── hw/
│   ├── v1.1/                picoloader.kicad_{pro,sch,pcb}
│   │   ├── fp-lib-table     project footprint table (${KIPRJMOD})
│   │   ├── sym-lib-table    project symbol table (${KIPRJMOD})
│   │   ├── Library.pretty   project footprints
│   │   └── packages3D/      3D models referenced by the PCB
│   ├── v1.1A/               same structure
│   ├── v1.2A/               same structure
│   └── flex/                Flex.kicad_{pro,sch,pcb}
│       ├── fp-lib-table
│       ├── sym-lib-table
│       ├── GamecubeConnectors.kicad_sym
│       └── Library.pretty
```

Every project folder is **self-contained**: `fp-lib-table` and `sym-lib-table` resolve
through `${KIPRJMOD}`, and `packages3D/` only contains the models the PCB actually
references. Clone the repository and open the `.kicad_pro` file of the revision you want;
no extra library installation is needed.

## Working with the projects

* Open the `.kicad_pro` file directly in KiCad 10.0 or newer. Older KiCad versions will
  refuse to open the schematic and PCB because of the file format version.
* Footprints from `Library.pretty` are embedded in the PCB files as well, so the boards
  render even if the library is not loaded; the library tables are provided so that
  "update footprint from library" works.
* Symbol libraries `MCU_RaspberryPi_RP2040`, `Type-C` and `W25Q256JVEIQ_TR` are third-party
  libraries and are **not redistributed** here. Each `.kicad_sch` carries a full
  `lib_symbols` cache, so the schematics display and plot correctly; only
  "update symbol from library" will report the missing libraries.
* `Library.kicad_sym` in the board projects is intentionally an empty stub — it only keeps
  the project symbol table consistent with the original design environment.
* Fabrication outputs (Gerber, drill, BOM, pick-and-place) are not tracked. Generate them
  from the projects with KiCad's own fabrication output or with your preferred plugin.

## Third-party assets

`packages3D/` contains vendor STEP models (HRO, Hirose, Winbond, Panasonic, RP2040 QFN and
generic passive footprints). They are included purely for mechanical reference and remain
the property of their respective manufacturers.

## License

This hardware design is released under the **CERN Open Hardware Licence Version 2 –
Permissive (CERN-OHL-P-2.0)**. See [LICENSE](LICENSE) for the full text.

You may use, study, modify, manufacture and distribute the design, including commercially,
provided you keep the notices and pass the licence on. The design is provided **as is**,
without any warranty; building and using it is at your own risk.
