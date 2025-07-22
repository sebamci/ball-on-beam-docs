# Test & Troubleshooting

Before starting with the implementation tasks, it's important to verify that your hardware and software setup are working correctly. This section guides you through a basic test to ensure communication between Simulink and the Arduino are functioning properly.

---

## 1. Run a Minimal Simulink Test

- Create a simple Simulink model that:
    - Lights up the onboard LED of the Arduino Due.
    - Therefore use the `Digital Output` block from the `Simulink Support Package for Arduino Hardware` library and set the pin to `13`.
    - Connect the block to a `Constant` block set to `1` (to turn on the LED).

- Run the model using the `Monitor & Tune` in the Hardware tab in Simulink.

- If the onboard LED lights up, your Simulink setup is correctly communicating with the Arduino Due.
- You can now set the `Constant` block to `0` to turn off the LED.

![Minimal Simulink test model](images/minimal_example_due.png)
<center>Minimal Simulink test model to verify Arduino communication</center>

![Minimal Simulink test setup](images/run_on_hardware.png)
<center>Run your model on the Arduino Due</center>

---

## 2. Verify USB Connection

- If the LED does not respond, check the USB connection:
    - Ensure you are using the **programming USB port** on the Arduino Due.
    - The board should be recognized by your computer.
- Connect the Arduino Due to your computer using the **programming USB port**.
- In MATLAB, use the following command to list available serial devices:

```matlab
serialportlist("all")
```

> Your Arduino Due should appear as a serial device (e.g. `COM4` or `/dev/ttyACM0`).

---


## 6. Common Issues

| Problem                           | Possible Cause                                    | Suggested Fix                            |
|-----------------------------------|---------------------------------------------------|------------------------------------------|
| No response from Arduino          | Wrong USB port, driver missing                    | Use programming USB and check `serialportlist` |
| Upload error                      | Board not detected or incorrect model settings    | Recheck "Hardware Implementation" tab    |

---

If everything works as expected, you're now ready to begin the practical implementation tasks in this course.