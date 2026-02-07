##  Configuration Challenges & Solutions

During the setup of the RadioMaster Pocket (EdgeTX) with the ER8 Receiver (ExpressLRS), several technical constraints were encountered. Below is a summary of the issues and the logic used to solve them.

### 1. ELRS Channel 5 Limitation (The "Stuck Servo" Issue)
* **Problem:** The servo connected to Channel 5 (intended for the second Aileron) was behaving erratically—locking to one side or not responding to proportional input.
* **Root Cause:** In the ExpressLRS protocol, Channel 5 is strictly reserved for the "Arming" state. It operates as a 1-bit switch (High/Low) and lacks the resolution required for PWM servo control.
* **Solution:** * Physically moved the second Aileron servo to **Channel 6**.
    * Updated the **EdgeTX Mixes**: Assigned `CH6` to source `Ail`.
    * Updated the **ER8 Output Mapping**: Ensured Pin 6 was mapped to Input 6.

### 2. Dual Elevator Synchronization
* **Problem:** The aircraft uses two independent servos for the elevator (tail). Initially, one surface moved up while the other moved down (acting like ailerons instead of elevators).
* **Root Cause:** The servos are physically mounted in a mirrored position, causing inverted mechanical movement for the same signal input.
* **Solution:** * Created a Mix on **CH4** sourcing from `Ele` (Elevator stick).
    * Used the **EdgeTX Outputs** tab to strictly **Invert (INV)** the signal of only one channel (CH4) to synchronize movement.
    * Adjusted the direction of both channels to ensure pulling the stick "back" resulted in "up" movement for pitch authority.

### 3. ESC Signal Frequency (Motor Beeping)
* **Problem:** The Skywalker 50A V2 ESC would not arm and kept beeping, despite the receiver being bound and showing telemetry.
* **Root Cause:** The modern ER8 receiver outputs high-frequency signals (100Hz/333Hz) by default, while the standard ESC expects a traditional **50Hz PWM** signal.
* **Solution:** * Accessed the ExpressLRS Lua Script -> `Other Devices` -> `RM ER8`.
    * Changed the **Output Mode** for Channel 3 (Throttle) to **50Hz**.

### 4. Input/Output Mapping Mismatch
* **Problem:** Control inputs were affecting the wrong surfaces (e.g., Throttle stick moving a servo).
* **Root Cause:** The internal mapping of the ER8 receiver was misaligned (Input 3 was routed to Physical Pin 4).
* **Solution:** * Audited the **Output Mapping** in the ELRS Lua Script.
    * Realigned all ports 1:1 (Input CH1 -> Output 1, Input CH2 -> Output 2, etc.) to match the EdgeTX Mixer standard.
