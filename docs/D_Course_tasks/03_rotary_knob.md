# III. Move the Beam Manually

In this task, you will use the rotary knob as an analog input to manually control the beam angle. This setup allows you to interactively test the system and observe how the beam responds to different user inputs without automatic feedback. The difficulty of manually balancing the ball will become apparent — reinforcing the motivation for feedback control.

---

## 1. Connect and Initialize

- The rotary knob (analog potentiometer) is connected to the `POTI` Grove connector input on the shield.
- In Simulink, drag the block `Rotary_Pot` from the custom library into your model.
- Connect the output of the `Rotary_Pot` block directly to the input of the `Servo_Position_Controller` block.

> This configuration creates a direct, manual control loop where the servo angle follows the knob position.

![Manual control setup](images/manual_rotary_connection.png)
<center>Manual mode: Rotary knob directly drives the servo</center>

---

## 2. Understand the Signal Mapping

- The `Rotary_Manual` block maps the analog input to a beam angle in **radians**.
- The mapping range is:  
  `0 V` → `-0.07 rad` (beam tilted left)  
  `3.3 V` → `+0.07 rad` (beam tilted right)


---

## 3. Deploy and Test

- Deploy the model using `Monitor & Tune`.
- Rotate the knob slowly and observe how the beam reacts in real time.

> This test verifies that the full analog input range is usable and that the actuator responds as expected.

![Manual control test](images/manual_mode_live_test.png)
<center>Manual beam control using the rotary input</center>

---

## 4. Summary

| Step             | Action                                                             |
|------------------|--------------------------------------------------------------------|
| Hardware         | Rotary knob connected to `Rotary` Molex input                      |
| Simulink Blocks  | `Rotary_Manual` block connected to `Servo_Position_Controller`     |
| Signal Range     | Manual input mapped to ±0.07 rad beam angle                         |
| Testing          | Observe real-time control and beam response during knob rotation   |

Once you are confident with the manual control, you can proceed to implement and test automatically generated setpoints.
