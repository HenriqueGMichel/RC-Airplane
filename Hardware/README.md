#  Hardware Bill of Materials (BOM)

This project combines custom-built structural elements with off-the-shelf RC electronics. Below is the complete list of components used in the build.

##  Airframe & Structure
The fuselage and wings were scratch-built using lightweight foam sheets.

| Component | Specifications | Notes |
| :--- | :--- | :--- |
| **Fuselage Material** | Depron 4mm | Lightweight extruded polystyrene foam. |
| **Reinforcement** | Carbon Fiber Rods and Fiberglass | Used in the wings and tail for structural rigidity. |
| **Adhesives** | Hot Glue / Epoxy | Used for joining Depron sheets and mounting the motor firewall. |
| **Push Rods** | Steel Wire | Custom cut for control surface linkages. |

##  Propulsion System (Pusher Configuration)
The aircraft utilizes a rear-mounted motor setup.

| Component | Model | Configuration |
| :--- | :--- | :--- |
| **Motor** | D3536 Brushless | Rear-mounted, facing the tail. |
| **ESC** | Hobbywing Skywalker 50A V2 | 50Hz PWM, 5V/5A BEC. |
| **Propeller** | 10x6 | Mounted with numbers facing flight direction. |
| **Battery** | Li-Ion 4S (16.8V) | Custom pack for extended flight times. |

##  Electronics & Control
Based on the RadioMaster and ExpressLRS ecosystem.

| Component | Model | Role |
| :--- | :--- | :--- |
| **Transmitter (TX)** | RadioMaster Pocket | EdgeTX Operating System. |
| **Receiver (RX)** | RadioMaster ER8 | 2.4GHz ELRS PWM Receiver. |
| **Servos** | 9g Micro Servos (x4) | 1x Aileron R, 1x Aileron L, 1x Elevator R, 1x Elevator L. |

##  3D Printed Parts
Custom parts modeled to fit specific needs (STLs available in `3d_models/`).

* **Retractable Landing Gear:** Custom design with spring suspension.
* **Cockpit Canopy:** Aerodynamic profile fitted to the fuselage void.
* **Motor Mount:** Firewall adapter for the D3536 motor.
