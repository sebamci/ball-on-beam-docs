# IX. Add User Interface

In this task, you will integrate the hardware user interface elements into your control system. These include a pushbutton to switch between control modes and NeoPixel LEDs to provide visual feedback. This allows a more intuitive and robust interaction with the Ball-on-Beam system.

---

## 1. System Overview

The user interface enables switching between different operating modes of the Ball-on-Beam system:

- **Simulink Mode** – The setpoint and control loop is modeled in Simulink.
- **Rotary Knob Mode** – The user directly controls the beam angle manually, the setpoint is still defined in Simulink.
- **Control SoftPot Mode** – The user defines the setpoint by placing a second ball on the Control SoftPot sensor. The system then drives the beam to bring the main ball to that target.

> Each mode is automatically selected via the pushbutton logic and displayed via NeoPixel LEDs.

---

## 2. Add UI Blocks to the Model

Extend your current Simulink model:

- Drag the following blocks from the custom library:
    - `PushButton_ModeSelector`
    - `NeoPixel_Controller`
- Route the active mode signal to both:
    - A `Switch Case` block that selects between manual and automatic control signals
    - The `NeoPixel_Controller` block for visual feedback

![UI control logic in Simulink](images/ui_mode_selector_block.png)
<center>Mode control logic integrated into the control system</center>

---

## 3. Connect the Hardware

- The pushbutton is connected to the `MODE` Grove connector input on the shield.
- The NeoPixel chain is connected to the `LED` JST-SH 3-pin digital output.

> Each press advances to the next mode (e.g. Simulink → Manual → Softpot → Simulink …)

---

## 4. Deploy and Test

- Deploy the model using `Monitor & Tune`.
- Press the pushbutton to cycle through the modes and observe the LED feedback:
    - **Green**: e.g. Rotary Knob Mode (manual control)
    - **Red**: e.g. Simulink Mode (PID control)
    - **Blue**: e.g. Control SoftPot Mode (dynamic setpoint)
- In addition, the NeoPixel LED should light up in the corresponding area and color of the selected mode.

## 5. Summary

| Element           | Function                                   |
|-------------------|--------------------------------------------|
| Pushbutton        | Cycles through control modes               |
| Mode Logic        | Selects between PID and manual signals     |
| NeoPixel LEDs     | Visual feedback of current mode            |
| Output Switching  | Uses multiplexer to forward active signal  |

With this setup, your system becomes user-friendly and robust.  
You're now ready to finalize your project and prepare it for demonstration.
