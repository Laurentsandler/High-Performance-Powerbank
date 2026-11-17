# High-Performance Powerbank

A high-wattage, bidirectional USB-C fast charging powerbank powered by the IP2368 controller and a 2S Li-ion battery pack.

## Description

This project is a compact, high-efficiency powerbank engineered for high-wattage charging and discharging over a single USB-C port. Built around the Injoinic IP2368 bidirectional buck-boost controller, the powerbank is configured for a 2-series (2S) lithium-ion battery array totaling 10,000 mAh (nominal 7.4 V, peak 8.4 V).

To reliably handle high wattage and transient currents, the system utilizes a custom 4-layer PCB with dedicated internal power and ground planes. The board integrates four battery level status LEDs, a physical power/wake button, and robust power routing. The entire assembly is housed in a custom 3D-printed enclosure designed in Onshape, fastened with M3 machine screws and a press-fit button lid mechanism.

## My Motivation

Off-the-shelf high-wattage powerbanks capable of charging laptops and high-draw USB-PD devices are typically bulky, expensive, and opaque in their design. I wanted to design an open, compact, high-performance powerbank tailored for daily carry that pairs high-current capability with a clean 4-layer board layout and a durable custom enclosure.

## Hardware Design

The custom PCB was designed in EasyEDA with a 4-layer stackup specifically optimized for high-power switching:

- **Layer 1 (Top)**: Component placement, high-current switching nodes, and signal lines.
- **Layer 2 (Inner 1)**: Continuous ground plane (GND) for low-impedance return paths and noise reduction.
- **Layer 3 (Inner 2)**: Dedicated power copper pours for VBUS and VBAT.
- **Layer 4 (Bottom)**: Control traces and ground shielding.

### Layout & Thermal Strategy

- **Component Segregation**: The layout separates high-power switching circuitry (MOSFETs, main inductor, high-current battery and VBUS paths) on the right side of the PCB, while sensitive control lines and the IP2368 controller reside on the left side with their respective decoupling capacitors and timing resistors.
- **Heavy Traces**: Power switching paths were significantly widened in iteration 2 to support high-amperage transfer with minimal I²R thermal losses.
- **Direct Battery Terminals**: Due to the high current requirements of high-wattage operation, high-gauge wiring and reinforced solder pads are used in place of standard low-current JST connectors.
- **Silkscreen Graphics**: Custom silk graphics and clear component identification marking.

EasyEDA project link:
[https://oshwlab.com/laurentsandler/high-performance-powerbank](https://oshwlab.com/) *(Add your project link here)*

### PCB Layout & 3D Renders

<img width="800" alt="PCB 3D Top Render" src="images/pcb_top_render.png" />
<!-- Replace src with your uploaded image link or local path -->

<img width="800" alt="PCB 3D Bottom Render" src="images/pcb_bottom_render.png" />
<!-- Replace src with your uploaded image link or local path -->

<img width="800" alt="PCB 4-Layer Routing" src="images/pcb_layout.png" />
<!-- Replace src with your uploaded image link or local path -->

### Case

The enclosure was modeled in Onshape to deliver a compact protective shell with internal mounting posts and accessibility cutouts:

- **M3 Machine Screws**: Secure the PCB internally to avoid mechanical stress on the USB-C connector during mating cycles.
- **Press-Fit Button**: Top lid snaps onto the bottom enclosure using a dedicated press-fit button design without requiring glue.
- **Interface Ports**: Precision cutouts for the USB-C port, 4-LED fuel gauge status array, and tactile power button.

<img width="800" alt="Case Assembly Render" src="images/case_assembly.png" />
<!-- Replace src with your uploaded image link or local path -->

<img width="800" alt="Case Open Internal View" src="images/case_internals.png" />
<!-- Replace src with your uploaded image link or local path -->

Onshape project link:
[https://cad.onshape.com/](https://cad.onshape.com/) *(Add your Onshape document link here)*

### 3D Mockups

<img width="800" alt="Exploded Assembly View" src="images/mockup_exploded.png" />
<!-- Replace src with your uploaded image link or local path -->

<img width="800" alt="Powerbank in Hand" src="images/mockup_perspective.png" />
<!-- Replace src with your uploaded image link or local path -->

## Features

- **Bidirectional Fast Charging**: Single USB-C port supporting high-wattage USB-PD input and output managed by the IP2368 controller.
- **2S 10,000 mAh Battery Architecture**: Dual 3.7 V Li-ion cells in series (7.4 V nominal, 8.4 V peak) offering balanced capacity and voltage efficiency.
- **4-Layer PCB**: Internal solid ground plane and split VBUS/VBAT power planes for optimal thermal and electrical performance.
- **4-Stage LED Fuel Gauge**: Real-time visual readout for battery capacity and charging activity.
- **Push Button Interface**: Dedicated key switch for manual wake-up and state interrogation.
- **Robust 3D-Printed Enclosure**: M3 screw standoffs paired with a press-fit button retention lid.

## System Architecture

```
                 ┌──────────────────────────────────────────────────────────┐
                 │                       IP2368 IC                          │
                 │   Bidirectional Synchronous Buck-Boost Controller        │
                 └──────────────┬────────────────────────────┬──────────────┘
                                │                            │
                 ┌──────────────▼──────────────┐             │
                 │     Buck-Boost H-Bridge     │             │
                 │ 4x MOSFETs + Power Inductor │             │
                 └──────┬──────────────┬───────┘             │
                        │              │                     │
          ┌─────────────▼────┐    ┌────▼─────────────┐       │
          │   USB-C Port     │    │  2S Battery Pack │       │
          │ Bidirectional PD │    │ 7.4V / 10,000mAh │       │
          └──────────────────┘    └──────────────────┘       │
                                                             │
                  ┌──────────────────────────────────────────┴─────┐
                  │ Peripherals:                                   │
                  │  • 4x State of Charge LEDs (LED1 - LED4)       │
                  │  • 1x Wake / Power Key Tactile Button          │
                  └────────────────────────────────────────────────┘
```

## Specifications

| Parameter | Specification |
| :--- | :--- |
| **Main Controller** | Injoinic IP2368 Buck-Boost PMIC |
| **Battery Configuration** | 2S Li-ion (7.4 V nominal / 8.4 V peak) |
| **Battery Capacity** | 10,000 mAh total |
| **Port Interface** | 1x Bidirectional USB Type-C |
| **Indicators** | 4x Surface-Mount LEDs (25% / 50% / 75% / 100%) |
| **Controls** | 1x Momentary tactile key button |
| **PCB Stackup** | 4 Layers (Signal / GND / Power / Signal) |
| **Fastening** | M3 machine screws into heat-set inserts / standoffs |
| **Lid Attachment** | Press-fit mechanical retention button |

## Bill of Materials

The full Bill of Materials with supplier part numbers is available in [BOM.csv](BOM.csv).

| Item | Reference | Description | Footprint | Qty |
| :--- | :--- | :--- | :--- | :--- |
| 1 | U1 | IP2368 Buck-Boost Controller IC | QFN-48 | 1 |
| 2 | Q1-Q4 | N-Channel Power MOSFETs (H-Bridge) | DFN5x6 / SOP-8 | 4 |
| 3 | L1 | Shielded High-Current Power Inductor | SMD (10x10 or 12x12) | 1 |
| 4 | C_IN, C_OUT | Low-ESR Decoupling / Filter Capacitors | 0805 / 1206 / Polymer | 8 |
| 5 | R_SENSE | Precision Current Sense Shunt Resistors | 2512 | 2 |
| 6 | J1 | High-Current 16/24-Pin USB-C Receptacle | USB-C SMD/Hybrid | 1 |
| 7 | BATT | 2S Li-ion Battery Pack 10,000 mAh | Custom / 2x Cells | 1 |
| 8 | LED1-LED4 | Battery Level Indicator LEDs | 0603 SMD | 4 |
| 9 | SW1 | Momentary Tactile Power/Wake Button | SMD Push Button | 1 |
| 10 | HW1 | M3 Machine Screws | M3 x 6 mm | 4 |
| 11 | CASE | 3D Printed Case & Press-Fit Lid | Custom (Onshape) | 1 |

## Project Timeline & Journal

A development log with 16.0 hours logged is tracked in [JOURNAL.md](JOURNAL.md).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
