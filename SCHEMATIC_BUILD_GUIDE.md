# EasyEDA Step-by-Step Schematic Building Guide
## High-Performance Power Bank with IP2368_BZ_VGLIP (2S Battery Setup)

---

## TABLE OF CONTENTS
1. [Component List with Prefixes](#component-list)
2. [EasyEDA Setup Instructions](#easyeda-setup)
3. [Step-by-Step Connection Guide](#step-by-step-connections)
4. [Final Verification Checklist](#final-verification)

---

## <a name="component-list"></a>PART 1: COMPONENT LIST WITH STANDARD PREFIXES

### **Standard Electronics Naming Prefixes:**
- **U** = Integrated Circuit (IC Chip)
- **C** = Capacitor
- **R** = Resistor
- **D** = Diode
- **L** = Inductor
- **J** = Connector
- **LED** = Light-Emitting Diode
- **BATT** = Battery

### **Your Complete Component List:**

| Reference | Component Name | EasyEDA Part# | Quantity | Purpose |
|-----------|----------------|---------------|----------|---------|
| U1 | IP2368_BZ Power Bank IC | C14301 | 1 | Main controller chip |
| BATT1, BATT2 | 18650 Lithium Battery Cell | C93792 | 2 | Battery cells (2S series) |
| J1 | USB Type-C Connector | C165948 | 1 | Input/Output charging port |
| J2 | Battery Connector (JST PH 2.0) | C172416 | 1 | Battery connection |
| L1 | Inductor 10µH | C5833 | 1 | Output power filtering |
| L2 | Inductor 10µH | C5833 | 1 | Input power filtering |
| C1 | Capacitor 47µF/10V | C14691 | 1 | VBAT power supply stabilization |
| C2 | Capacitor 47µF/10V | C14691 | 1 | VIN power supply stabilization |
| C3 | Capacitor 47µF/10V | C14691 | 1 | VOUT power supply stabilization |
| C4 | Capacitor 1µF | C14855 | 1 | VBAT noise filter |
| C5 | Capacitor 1µF | C14855 | 1 | VIN noise filter |
| C6 | Capacitor 1µF | C14855 | 1 | VOUT noise filter |
| C7 | Capacitor 100nF (0.1µF) | C14816 | 1 | SDA/SCL line filtering |
| R1 | Resistor 10kΩ | C12562 | 1 | SDA pull-down resistor |
| R2 | Resistor 10kΩ | C12562 | 1 | SCL pull-down resistor |
| R3 | Resistor 1kΩ | C12587 | 1 | LED current limiting resistor |
| D1 | Schottky Diode (MBRA140T) | C159222 | 1 | Reverse current protection on input |
| LED1 | Red LED 3mm | C2286 | 1 | Power indicator light |
| U2 | PCM Protection Module 2S | C94538 | 1 | Battery protection circuit |

---

## <a name="easyeda-setup"></a>PART 2: EASYEDA SETUP INSTRUCTIONS

### **Step 1: Create Your New Schematic**
1. Go to **easyeda.com** and log in to your account
2. Click the **"New Project"** button (top left)
3. Enter project name: `PowerBank_IP2368_2S`
4. Click **"Create"**
5. Select **"New Schematic"** from the menu
6. You now have a blank schematic canvas

### **Step 2: Configure Your Schematic Settings**
1. Click **"Edit"** menu → **"Schematic Preferences"**
2. Set **Grid**: 0.1 inch (for better component alignment)
3. Check the box for **"Show grid"** (helps with alignment)
4. Click **"OK"**

### **Step 3: Create Page Title Block**
1. Click **"Edit"** → **"Edit Page"**
2. Title: `High-Performance Power Bank`
3. Company: `DIY Electronics`
4. Date: Insert current date
5. Click **"OK"**

---

## <a name="step-by-step-connections"></a>PART 3: STEP-BY-STEP CONNECTION GUIDE

### **SECTION A: PLACE ALL COMPONENTS ON SCHEMATIC**

#### **Step A1: Add the Main Control Chip (U1)**
1. Click **"Library"** on the left sidebar
2. In the search box, type: `IP2368`
3. Find and select **IP2368_BZ_VGLIP**
4. Click to add it to your schematic
5. Click on the schematic canvas at approximately **X: 50mm, Y: 50mm** (center-left area)
6. Right-click on the component and select **"Rotate"** if needed to make pins face outward

#### **Step A2: Add All Capacitors**
1. Click **"Library"** → Search: `47µF capacitor`
2. Select **Capacitor 47µF/10V**
3. Click to place **C1** at X: 20mm, Y: 80mm (above U1)
4. Click to place **C2** at X: 20mm, Y: 100mm (above C1)
5. Click to place **C3** at X: 20mm, Y: 120mm (above C2)
6. Search for **1µF capacitor**
7. Select **Capacitor 1µF**
8. Click to place **C4** at X: 40mm, Y: 80mm
9. Click to place **C5** at X: 40mm, Y: 100mm
10. Click to place **C6** at X: 40mm, Y: 120mm
11. Search for **100nF capacitor** (same as 0.1µF)
12. Place **C7** at X: 60mm, Y: 80mm

#### **Step A3: Add All Resistors**
1. Click **"Library"** → Search: `10k resistor`
2. Select **Resistor 10kΩ**
3. Click to place **R1** at X: 80mm, Y: 90mm
4. Click to place **R2** at X: 80mm, Y: 110mm
5. Search for **1k resistor**
6. Select **Resistor 1kΩ**
7. Click to place **R3** at X: 100mm, Y: 130mm

#### **Step A4: Add Inductors**
1. Click **"Library"** → Search: `10uH inductor`
2. Select **Inductor 10µH**
3. Click to place **L1** at X: 110mm, Y: 50mm (right side, upper)
4. Click to place **L2** at X: 110mm, Y: 70mm (right side, below L1)

#### **Step A5: Add Diodes**
1. Click **"Library"** → Search: `MBRA140T`
2. Select **Schottky Diode MBRA140T**
3. Click to place **D1** at X: 90mm, Y: 70mm

#### **Step A6: Add LED**
1. Click **"Library"** → Search: `LED red`
2. Select **Red LED 3mm**
3. Click to place **LED1** at X: 100mm, Y: 100mm

#### **Step A7: Add Connectors**
1. Click **"Library"** → Search: `USB Type-C`
2. Select **USB Type-C Connector**
3. Click to place **J1** at X: 130mm, Y: 90mm (right edge)
4. Search for **JST PH 2.0**
5. Select **Battery Connector JST PH 2.0**
6. Click to place **J2** at X: 10mm, Y: 40mm (left edge, top)

#### **Step A8: Add Battery Cells and Protection Module**
1. Search for **18650 battery** (or use generic battery symbol)
2. Click to place **BATT1** at X: 10mm, Y: 20mm
3. Click to place **BATT2** at X: 10mm, Y: 10mm
4. Search for **PCM 2S** or **protection module**
5. Click to place **U2** at X: 35mm, Y: 15mm

---

### **SECTION B: DRAW ALL CONNECTION WIRES**

**Important:** When clicking on pins, always click on the small circle/dot at the end of the pin. A yellow dot means the wire is properly connected.

#### **Step B1: Battery Section Connections**

**Connection 1: BATT1 to BATT2 (Series Connection)**
1. Click **"Wire"** tool from left toolbar (pencil icon)
2. Click on the **POSITIVE pin of BATT1**
3. Drag to the **NEGATIVE pin of BATT2**
4. Click to finish the wire
5. A label should appear - this is your **Battery Series Connection**

**Connection 2: BATT1 Negative to PCM Negative Input**
1. Use **Wire** tool again
2. Click on the **NEGATIVE pin of BATT1**
3. Drag to the **B- (negative input) of U2 (PCM)**
4. Click to finish

**Connection 3: Series Connection Point to PCM Positive Input**
1. Click on the junction point between BATT1 positive and BATT2 negative
2. Drag a wire to **B+ (positive input) of U2**
3. Click to finish

#### **Step B2: Create Ground Rail (GND)**

**Connection 4: Establish Main Ground Point**
1. Right-click on any empty area of the schematic
2. Select **"Add Connector"** or **"Add Power/GND"**
3. Select **GND** (ground symbol)
4. Place it at X: 15mm, Y: 130mm (bottom-left area)
5. Click on this GND symbol - this is your **main ground reference**

**Connection 5: Connect PCM Negative Output to GND**
1. Use **Wire** tool
2. Click on **B- (negative output) of U2**
3. Drag to the **main GND symbol**
4. Click to finish

**Connection 6: Connect U1 Ground Pin (Pin 9) to GND**
1. Find pin labeled **GND** or **VSS** on U1 (usually bottom or left)
2. Click on it
3. Drag to the **main GND symbol**
4. Click to finish

#### **Step B3: Battery Power Supply to U1**

**Connection 7: PCM Positive Output to C1 (47µF Capacitor)**
1. Use **Wire** tool
2. Click on **B+ (positive output) of U2**
3. Drag to one terminal of **C1**
4. Click to finish

**Connection 8: C1 Other Terminal to GND**
1. Click on the other terminal of **C1**
2. Drag to the **main GND symbol**
3. Click to finish

**Connection 9: C1 to U1 VBAT Pin**
1. Click on the junction between U1 and C1 positive side
2. Or create a wire from **VBAT pin (pin 1) of U1**
3. Drag to the positive side of **C1** (or junction point)
4. Click to finish
   - **This is your Battery Power Supply Line (7.2-8.4V)**

**Connection 10: Add C4 (1µF) Across VBAT and GND**
1. Click on the **VBAT line** (where it connects to U1 pin 1)
2. Drag one terminal of **C4** here
3. Drag the other terminal of **C4** to **GND**
4. Click to finish
   - **This stabilizes the voltage for U1**

#### **Step B4: USB Input (VIN) Power Path**

**Connection 11: USB-C VBUS to Diode Input**
1. Click on the **VBUS pin of J1 (USB Type-C)**
   - The 5V input pin (usually center or marked VBUS)
2. Drag a wire to the **Anode (input side) of D1**
3. Click to finish

**Connection 12: Diode Output to VIN Connection**
1. Click on the **Cathode (output side) of D1**
   - This is the direction the current flows
2. Drag a wire to **VIN pin (pin 2 or 3) of U1**
3. Click to finish
   - **The diode prevents the battery from draining through USB input**

**Connection 13: Add C2 (47µF) to VIN Power Supply**
1. Click on the **VIN connection point** (between D1 and U1)
2. Drag one terminal of **C2** here
3. Drag the other terminal of **C2** to **GND**
4. Click to finish

**Connection 14: Add C5 (1µF) to VIN Line**
1. Click on the **VIN line**
2. Drag one terminal of **C5** here
3. Drag the other terminal to **GND**
4. Click to finish

**Connection 15: USB-C GND to Main GND**
1. Click on the **GND pin of J1 (USB Type-C)**
2. Drag a wire to the **main GND symbol**
3. Click to finish

#### **Step B5: USB Output (VOUT) Power Path**

**Connection 16: Add L1 (Inductor) to Output**
1. Click on **VOUT pin (pin 4 or 5) of U1**
2. Drag a wire to one terminal of **L1**
3. Click to finish

**Connection 17: Inductor to C3 (47µF Output Capacitor)**
1. Click on the other terminal of **L1**
2. Drag a wire to one terminal of **C3**
3. Click to finish
   - **L1 and C3 form an LC filter for clean 5V output**

**Connection 18: Add C6 (1µF) Across Output**
1. Click on the **VOUT output line** (between L1 and C3)
2. Drag one terminal of **C6** here
3. Drag the other terminal to **GND**
4. Click to finish

**Connection 19: Output to USB-C VBUS**
1. Click on the positive terminal of **C3**
2. Drag a wire to the **VBUS pin of J1 (USB output)**
3. Click to finish

**Connection 20: Connect VOUT GND**
1. Click on the negative terminals of **C3 and C6** (connected together)
2. Drag a wire to the **main GND symbol**
3. Click to finish

#### **Step B6: Communication Lines (SDA/SCL)**

**Connection 21: USB-C D+ to Pull-Down Resistor R1**
1. Click on the **D+ pin of J1 (USB Type-C)**
   - Usually the second pin from the side
2. Drag a wire to one terminal of **R1 (10kΩ)**
3. Click to finish

**Connection 22: R1 Other Terminal to SDA**
1. Click on the other terminal of **R1**
2. Drag a wire to **SDA pin (pin 6 or 7) of U1**
3. Click to finish
   - **This is the Serial Data line**

**Connection 23: Add C7 (100nF) on SDA Line**
1. Click on the **SDA connection point** (between R1 and U1)
2. Drag one terminal of **C7** here
3. Drag the other terminal to **GND**
4. Click to finish

**Connection 24: USB-C D- to Pull-Down Resistor R2**
1. Click on the **D- pin of J1 (USB Type-C)**
   - Usually the third pin from the side
2. Drag a wire to one terminal of **R2 (10kΩ)**
3. Click to finish

**Connection 25: R2 Other Terminal to SCL**
1. Click on the other terminal of **R2**
2. Drag a wire to **SCL pin (pin 8 or 9) of U1**
3. Click to finish
   - **This is the Serial Clock line**

#### **Step B7: LED Indicator Connection**

**Connection 26: VOUT to LED Through Current Limiting Resistor**
1. Click on the **VOUT line** (after L1 filter)
2. Drag a wire to one terminal of **R3 (1kΩ)**
3. Click to finish

**Connection 27: R3 to LED Positive**
1. Click on the other terminal of **R3**
2. Drag a wire to the **positive (longer leg) of LED1**
3. Click to finish
   - **This limits current to safe LED levels (~5mA)**

**Connection 28: LED Negative to GND**
1. Click on the **negative (shorter leg) of LED1**
2. Drag a wire to the **main GND symbol**
3. Click to finish
   - **The LED lights up when the power bank is delivering power**

#### **Step B8: Battery Connector (Optional External Connection)**

**Connection 29: J2 Positive to Battery B+**
1. Click on the **positive pin of J2 (Battery JST Connector)**
2. Drag a wire to the **B+ output of U2**
3. Click to finish

**Connection 30: J2 Negative to GND**
1. Click on the **negative pin of J2**
2. Drag a wire to the **main GND symbol**
3. Click to finish
   - **This optional connector allows external battery charging**

---

### **SECTION C: ADD LABELS AND NOTES**

#### **Step C1: Label Critical Points**
1. Click the **"Text"** tool from left toolbar
2. Click near the **VBAT line** and type: `VBAT (7.2-8.4V)`
3. Click near the **VIN line** and type: `VIN (USB 5V)`
4. Click near the **VOUT line** and type: `VOUT (5V Output)`
5. Click near the **battery section** and type: `2S Series Battery (8.4V max)`

#### **Step C2: Add Component Values**
1. Double-click on each component to edit its properties
2. For each resistor, set the value:
   - R1: `10kΩ`
   - R2: `10kΩ`
   - R3: `1kΩ`
3. For each capacitor:
   - C1, C2, C3: `47µF/10V`
   - C4, C5, C6: `1µF`
   - C7: `100nF`
4. For each inductor:
   - L1, L2: `10µH`

#### **Step C3: Add Circuit Description Notes**
1. Click **"Text"** tool
2. In an empty area at the bottom, type:
```
CIRCUIT OPERATION:
- Battery: 2x 18650 in Series = 8.4V max
- Input: USB-C 5V charging input
- Output: USB-C 5V/2A output to devices
- Protection: PCM guards against over/under charge
- Filtering: LC filters ensure clean power output
```

---

## <a name="final-verification"></a>PART 4: FINAL VERIFICATION CHECKLIST

### **Verify All Connections Before PCB Layout**

Use this checklist to ensure every wire is correctly placed:

**Battery Section:**
- [ ] BATT1 positive connects to BATT2 negative
- [ ] BATT1 negative connects to U2 B- input
- [ ] BATT2 positive connects to U2 B+ input
- [ ] U2 B+ output connects to C1 (47µF)
- [ ] C1 other terminal connects to GND
- [ ] U2 B- output connects to main GND rail

**U1 Power Supply:**
- [ ] U1 VBAT (pin 1) connects to VBAT line (after C1)
- [ ] U1 VBAT area has C4 (1µF) bypass capacitor to GND
- [ ] U1 GND (pin 9 or VSS) connects to main GND rail
- [ ] All U1 pins have proper connections (none floating)

**USB Input (Charging):**
- [ ] J1 VBUS connects to D1 Anode (input side)
- [ ] D1 Cathode connects to U1 VIN pin (pin 2/3)
- [ ] D1 Cathode area has C2 (47µF) to GND
- [ ] D1 Cathode area has C5 (1µF) to GND
- [ ] J1 GND connects to main GND rail
- [ ] No shorts between VBUS and GND lines

**USB Output (Phone Charging):**
- [ ] U1 VOUT (pin 4/5) connects to L1 input
- [ ] L1 output connects to C3 (47µF) positive
- [ ] C3 negative connects to GND
- [ ] C6 (1µF) is across C3 and GND
- [ ] C3 positive connects to J1 VBUS output
- [ ] J1 GND (output) connects to main GND

**Data Lines:**
- [ ] J1 D+ connects to R1 one terminal
- [ ] R1 other terminal connects to U1 SDA
- [ ] C7 (100nF) is across SDA and GND
- [ ] J1 D- connects to R2 one terminal
- [ ] R2 other terminal connects to U1 SCL
- [ ] No data line shorts to power lines

**LED Indicator:**
- [ ] VOUT line connects to R3 (1kΩ) one terminal
- [ ] R3 other terminal connects to LED1 positive leg
- [ ] LED1 negative leg connects to GND
- [ ] LED current path is complete

**Ground Rail:**
- [ ] All negative power connections reach main GND symbol
- [ ] All capacitor negative terminals reach GND
- [ ] All IC ground pins reach GND
- [ ] No ground loops (wires crossing properly with airwires)

**Component Labels:**
- [ ] All resistors labeled with values (R1: 10kΩ, etc.)
- [ ] All capacitors labeled with values
- [ ] All ICs labeled (U1, U2)
- [ ] All connectors labeled (J1, J2)
- [ ] All power rails labeled

---

## FINAL TIPS FOR SUCCESS

### **Before Converting to PCB Layout:**
1. **Zoom in** on each connection and verify no wires are floating
2. **Look for electrical errors** - the software may flag these with red warnings
3. **Check that all pins** on U1 are accounted for
4. **Verify polarity** of all diodes and capacitors
5. **Count components** - you should have exactly:
   - 20 resistors/inductors
   - 7 capacitors
   - 2 diodes (D1 and the body diode in U1)
   - 1 LED
   - 2 ICs (U1 and U2)
   - 2 connectors (J1 and J2)
   - 2 batteries

### **Once Verified, Generate PCB Layout:**
1. Right-click on the schematic
2. Select **"Convert to PCB"**
3. EasyEDA will auto-place components on the PCB
4. You can then arrange them for optimal routing

### **Common Mistakes to Avoid:**
- ❌ Forgetting the diode D1 (battery will drain through USB input)
- ❌ Not including bypass capacitors (circuit will be unstable)
- ❌ Incorrect inductor orientation (won't filter properly)
- ❌ LED in backwards (won't light up)
- ❌ Resistors missing on data lines (communication will fail)
- ❌ Wrong battery connection (polarity matters!)

---

## NEXT STEPS

Once your schematic is complete and verified:
1. Generate the **PCB Layout** from EasyEDA
2. Design your **PCB trace routing** (EasyEDA can auto-route)
3. Order your PCB from manufacturers like JLCPCB or PCBWay
4. Order all components from your part list
5. Solder components carefully to your PCB

Your schematic is now ready for manufacturing!
