# VIII. Track Ball with SoftPot

In this task, you will build a dedicated subsystem that uses the Control SoftPot as a dynamic reference input. The goal is to regulate the main ball on the beam to the same position as a second ball placed on the Control SoftPot. This demonstrates real-time multi-sensor feedback using your tuned PID controller.

---

## 1. Objective

You will create a **modular subsystem** that contains all components required to:

- Read the Control SoftPot (reference ball position)
- Read the Beam SoftPot (actual ball position)
- Calculate the position error
- Apply PID control
- Command the beam angle via the servo

> This structure prepares your system for advanced tracking and improves reusability and readability.

---

## 2. Build the Subsystem

Inside your Simulink model:

1. Create a new **Subsystem** and name it `SoftPot_Tracking`
2. Insert the following blocks into the subsystem:
    - `Control_SoftPot` – reads the setpoint position
    - `Read_Ball_Position` – reads the actual ball position
    - `Sum` block – computes error: (setpoint − position)
    - `PID_Controller_Tuned` – your tuned PID block
    - Output: connect to `Servo_Position_Controller`
 
![SoftPot tracking subsystem](images/subsystem_softpot_tracking.png)
<center>Dedicated subsystem for tracking a second ball using Control SoftPot</center>

---

## 3. Connect the Subsystem

- Place the new subsystem into your **main model**
- Feed the output of `SoftPot_Tracking` directly into the `Servo_Position_Controller` block
- Connect Scopes at the outputs of:
    - `Control_SoftPot` (setpoint)
    - `Read_Ball_Position` (actual position)
    - `PID_Controller_Tuned` (control signal)

> Make sure the analog values from both SoftPots are correctly calibrated and mapped to millimeters.

---

## 4. Run and Test

1. Deploy the model using `Monitor & Tune`
2. Place the **main ball** on the beam
3. Place the **reference ball** on the Control SoftPot
4. Observe how the system regulates the main ball to match the second ball's position

> Try moving the reference ball and observe how the beam adjusts to follow it.

![Ball tracking second ball](images/dual_ball_tracking_demo.png)
<center>System tracks the reference ball in real time using PID control</center>

---

## 5. Summary

| Block/Subsystem          | Function                                         |
|--------------------------|--------------------------------------------------|
| `Control_SoftPot`        | Reads dynamic target position                    |
| `Read_Ball_Position`     | Measures actual ball position                    |
| `PID_Controller_Tuned`   | Computes correction based on position error      |
| `SoftPot_Tracking`       | Self-contained subsystem for dual-ball tracking  |

With this modular control structure, you’ve created a reusable component for real-time reference tracking. This forms the basis for later integration into a complete system.