# Custom Retractable Landing Gear

This landing gear was designed to be practical to build, easy to 3D print, and robust. It features a custom suspension system utilizing a steel spring sourced from AliExpress.

## Design Goals
- **Ground Clearance:** Designed for RC airplanes requiring at least **15cm** of clearance from the ground to accommodate rear propellers.
- **Modularity:** The main body consists of two parts to allow for movement and suspension travel.
- **Resourcefulness:** Modeled to utilize spare parts I already had from the airframe build.

## Bill of Materials (BOM)
Here are the non-printed parts required for assembly:

| Component | Specs | Usage |
| :--- | :--- | :--- |
| **Steel Spring** | 1.5mm wire Ø / 25mm external Ø | Provides the suspension tension. (Total Spring Min length: ~30mm, i cut in 3 parts of 80mm for each landing gear) |
| **Carbon Fiber Rod** | 2mm Ø | Acts as the hinge pin connecting Part 1 and Part 2. (Reused from airframe reinforcement) |
| **Push Rod** | Standard size | Cut to size for the central strut mechanism. |
| **Adhesives** | CA Glue (Super Glue) & Hot Glue | Used for general assembly and fixation. |

##  How it Works

### Suspension
The two-part printed body is hinged with the 2mm Carbon Fiber rod. The spring absorbs the impact during landing, protecting the fuselage.

### Retraction Mechanism
The retraction is actuated by a standard **9g Servo**.
* **Mechanism:** The servo rotates 90 degrees to release a tension thread, allowing the landing gear to deploy via the gear with the other servo.
* **Radio Setup:** On the RadioMaster Pocket, I configured two separate channels:
    1.  **Release Channel:** Controls the servo that releases the thread.
    2.  **Steering/Lock Channel:** Controls the gear direction (if steerable) or the secondary locking mechanism.

> **Note:** I currently do not have a video of the retractable assembly process, only a picture that i took when i made the first time.

I think there are a lot of things to improve in the project. One thing would be that you need at least 5 servo's.
