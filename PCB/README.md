# PCB Manufacturing & Design Files

This directory contains the production and design files for the High-Performance Powerbank 4-layer PCB.

## EasyEDA Project Link
- **EasyEDA / OSHWLab Project**: [Add your EasyEDA project share URL here]

## PCB Specifications

- **Layers**: 4 Layers
- **Dimensions**: Compact custom form factor to fit the enclosure
- **Material**: FR-4 (TG150 or higher recommended for high-wattage thermal stability)
- **Copper Weight**: 1 oz outer layers, 1 oz inner planes (or 2 oz outer if ordering for peak wattage)
- **Minimum Trace / Space**: 6 mil / 6 mil (High-current paths widened to >40 mil / copper pours)
- **Surface Finish**: ENIG (Electroless Nickel Immersion Gold) or Lead-Free HASL
- **Silkscreen**: White on custom soldermask (e.g. Black / Matte Black)

## Layer Stackup

| Layer | Type | Copper Weight | Content |
| :--- | :--- | :--- | :--- |
| **Top Layer** | Signal / Power | 1 oz (35 µm) | Component footprints, MOSFET switching nodes, LEDs, Button |
| **Inner Layer 1** | Ground Plane | 1 oz (35 µm) | Solid GND plane for low-impedance return paths & shielding |
| **Inner Layer 2** | Power Plane | 1 oz (35 µm) | Split VBUS and VBAT power planes |
| **Bottom Layer** | Signal / Shield | 1 oz (35 µm) | Auxiliary routing and bottom ground pour |

## Subdirectories

- [`gerber/`](gerber/): Gerber RS-274X and Excellon NC drill files ready for fabrication (JLCPCB, PCBWay, etc.).
- [`schematic/`](schematic/): Schematic export files (PDF, EasyEDA JSON, SVG).
