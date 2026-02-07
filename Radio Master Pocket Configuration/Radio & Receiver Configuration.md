#  Radio & Receiver Configuration

This document outlines the specific logic used to configure the **RadioMaster Pocket (EdgeTX)** and the **ER8 Receiver (ExpressLRS)**. The setup involves a complex mixing scheme to control dual ailerons and dual elevators independently.

##  Control Protocol Standards
* **Radio Firmware:** EdgeTX (Latest Stable)
* **RF Protocol:** ExpressLRS (ELRS) 2.4GHz
* **Channel Order:** AETR (Aileron, Elevator, Throttle, Rudder)

##  Channel Mapping Strategy
Due to the specific requirements of the airframe (Dual Elevator, Dual Aileron) and the ELRS Channel 5 limitation, the channels were mapped as follows:

| Channel | Function | Physical Connection | Logic/Mix Source |
| :--- | :--- | :--- | :--- |
| **CH1** | Aileron Right | ER8 Pin 1 | `Src: Ail` (100% Weight) |
| **CH2** | Elevator Right | ER8 Pin 2 | `Src: Ele` (100% Weight) |
| **CH3** | Throttle (ESC) | ER8 Pin 3 | `Src: Thr` (50Hz Output) |
| **CH4** | Elevator Left | ER8 Pin 4 | `Src: Ele` (Mirrored Mix) |
| **CH5** | **ARMING** | *No Servo* | `Switch: SA` (2-Pos Safety) |
| **CH6** | Aileron Left | ER8 Pin 6 | `Src: Ail` (Mirrored Mix) |

> **Note on CH5:** Channel 5 is strictly reserved for the Arm/Disarm state in ELRS. Therefore, the second Aileron was moved to Channel 6 to ensure proportional control.

##  Critical Settings

### 1. Dual Elevator Synchronization (Outputs)
Since the elevator servos are mounted physically mirrored, they initially moved in opposite directions (rolling the tail).
* **Fix:** In the **Outputs** tab, `CH4` direction was set to **INV** (Inverted).
* **Result:** Both surfaces move UP when the stick is pulled back (Pitch Up).

### 2. ESC Frequency Adjustment (Lua Script)
The **Skywalker 50A V2** ESC requires a standard PWM frequency.
* **Setting:** In the ExpressLRS Lua Script (`Other Devices` -> `ER8`), the **Output Mode** for Pin 3 was manually forced to **50Hz**.
* **Why:** Higher frequencies (100Hz+) caused the ESC to fail initialization (continuous beeping).

### 3. Input/Output Mapping
To ensure the servos on pins 4 and 6 responded to the correct mixes:
* **ER8 Mapping:** Verified via Lua Script that `Output Pin 4` -> `Input 4` and `Output Pin 6` -> `Input 6`.

### 4. Safety Features
* **Throttle Cut:** Configured on Switch `SA` (Up position overrides Throttle to -100%).
* **Failsafe:** Receiver configured to cut throttle (No Pulses/Low) in case of signal loss.
