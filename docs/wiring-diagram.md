# Wiring Diagram & Hardware Interface

This document specifies the electrical connections, PCB layer architecture, and hardware interface for the High-Performance Powerbank based on the Injoinic IP2368 bidirectional buck-boost controller.

## System Block Diagram

```
[ USB Type-C Receptacle ]
   │  ▲ (VBUS 5V - 20V Bidirectional)
   ▼  │
[ Input Filter & TVS Protection ]
   │
   ▼
[ Synchronous Buck-Boost H-Bridge ] ── (L1 Power Inductor)
   │  ▲
   │  │ (Bidirectional Power Flow)
   ▼  │
[ 2S Li-ion Battery (7.4V Nom / 8.4V Max) ]
   ▲
   │
[ IP2368 Central Controller ]
   ├── Key Button (GPIO / Pin KEY)
   ├── 4x Status LEDs (Pins LED1, LED2, LED3, LED4)
   ├── Current Sensing (VBUS Sense & Battery Sense)
   └── NTC Thermistor / Battery Temp Monitoring
```

---

## Pin Connections & Hardware Mapping

### 1. USB Type-C Connector (USBC1)
Handles both high-wattage USB Power Delivery (PD) power sink (charging the battery pack) and power source (discharging to external devices):

| USB-C Pin | Function | Connection on Board |
| :--- | :--- | :--- |
| **VBUS** (A4, A9, B4, B9) | High-Voltage DC Bus (5V - 20V) | VBUS Copper Pour & Input Filter Network |
| **GND** (A1, A12, B1, B12) | Power Return | Main Ground Plane (Layer 2) |
| **CC1** (A5) | Configuration Channel 1 | IP2368 CC1 Pin (5.1kΩ pull-down / PD signaling) |
| **CC2** (B5) | Configuration Channel 2 | IP2368 CC2 Pin (5.1kΩ pull-down / PD signaling) |
| **D+ / D-** (A6, A7) | Fast Charge Data Lines | IP2368 DP/DM Pins (QC / AFC / FCP negotiation) |
| **Shield / Shell** | Chassis Ground | Outer Shell ground pads with multiple stitching vias |

### 2. 2S Battery Connection (BATT)
The battery pack is configured as a standard 2S (two cells in series) lithium-ion battery:
- **Nominal Voltage**: 7.4 V (3.7 V per cell)
- **Maximum Charge Voltage**: 8.4 V (4.2 V per cell)
- **Minimum Cutoff Voltage**: 6.0 V (3.0 V per cell)
- **Total Capacity**: 10,000 mAh

```
Connection Pad → Battery Terminal
------------------------------------
VBAT+          → Battery Positive (+)
VBAT-          → Battery Negative (-)
(Heavy gauge silicone wire soldered directly to reinforced high-current PCB pads)
```

> **Design Note**: Standard 2.0 mm / 2.54 mm JST headers are not rated for high-wattage current draw. Direct solder pads with thermal relief and teardrop traces are utilized to prevent excessive resistive heating and voltage drops.

### 3. User Interface (LEDs & Power Button)

#### 4-LED Fuel Gauge Indicator:
Four low-current SMD LEDs indicate charge level and charging status:
```
LED Pin (IP2368) → Anode/Cathode → Ground/Supply
------------------------------------------------
LED1             → 25% State of Charge (SoC)
LED2             → 50% State of Charge (SoC)
LED3             → 75% State of Charge (SoC)
LED4             → 100% State of Charge (SoC) / Fast-Charge Active
```

#### Push Button (KEY):
```
Tactile Switch   → Controller Pin
---------------------------------
Pin 1            → IP2368 KEY input pin
Pin 2            → Ground (GND)
(Press triggers battery status display; double-press/long-press toggles standby/output)
```

---

## 4-Layer PCB Stackup Architecture

To ensure electromagnetic compatibility (EMI) compliance and thermal dissipation under high wattage, a 4-layer stackup is implemented:

```
┌────────────────────────────────────────────────────────┐ Layer 1: Top Signal
│ Components, Buck-Boost MOSFETs, Wide Switching Traces   │ 1 oz Copper
├────────────────────────────────────────────────────────┤ Core / Prepreg
│ Continuous Solid Ground Plane (GND)                     │ Layer 2: Inner GND
├────────────────────────────────────────────────────────┤ Core
│ Dedicated VBUS & VBAT Power Planes                      │ Layer 3: Inner Power
├────────────────────────────────────────────────────────┤ Core / Prepreg
│ Bottom Routing & Ground Copper Shielding               │ Layer 4: Bottom Signal
└────────────────────────────────────────────────────────┘ 1 oz Copper
```

### Routing Best Practices Followed
1. **High-Power Loop Minimization**: The loop formed by the switching MOSFETs, power inductor, and high-frequency decoupling capacitors is kept as compact as possible.
2. **Thermal Vias**: An array of thermal vias is placed beneath the IP2368 thermal pad and switching MOSFET drains into the inner ground plane.
3. **Current Sense Kelvin Connections**: Current-sensing traces to shunt resistors utilize true 4-wire Kelvin routing to preserve measurement accuracy under high currents.
