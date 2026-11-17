# CAD & Mechanical Enclosure

This folder contains the 3D models and manufacturing files for the High-Performance Powerbank enclosure, designed in Onshape.

## Onshape Model Link
- **CAD Project Link**: [Add your public Onshape share URL here]

## Files in this Directory

| File | Description | Format |
| :--- | :--- | :--- |
| `Case_Bottom.stl` | Main lower enclosure housing the 2S battery pack and PCB | STL (3D Print) |
| `Case_Top_Lid.stl` | Upper lid with cutouts for LEDs and USB-C port | STL (3D Print) |
| `Press_Fit_Button.stl` | Retention button mechanism for securing the lid | STL (3D Print) |
| `Case_Assembly.step` | Full 3D assembly containing hardware, PCB, and enclosure | STEP (CAD Exchange) |

## 3D Printing Recommendations

- **Material**: PETG or ABS recommended for thermal endurance during high-wattage charging/discharging (PLA may deform if internal battery/MOSFET temperatures exceed 50°C).
- **Layer Height**: 0.20 mm (0.16 mm recommended for the press-fit button).
- **Infill**: 25% – 40% (Gyroid or Rectilinear for structural rigidity).
- **Perimeters / Walls**: 4 perimeters minimum.
- **Supports**: None required if oriented flat on the build plate.

## Assembly Instructions

1. Thread four M3 brass heat-set inserts into the mounting bosses in `Case_Bottom.stl` (or use direct self-tapping into printed bosses).
2. Solder the battery leads and routing to the PCB.
3. Seat the assembled PCB onto the standoffs and secure using 4x M3 machine screws.
4. Place the 2S battery pack into the battery bay (using thin battery foam/tape for vibration damping).
5. Align the `Case_Top_Lid.stl` and engage the `Press_Fit_Button.stl` until it clicks securely into place.
