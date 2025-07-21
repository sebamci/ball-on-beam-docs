# Test & Troubleshooting

Before starting with the implementation tasks, it's important to verify that your hardware and software setup are working correctly. This section guides you through basic tests to ensure sensor readings, actuator response, and communication between Simulink and the Arduino are functioning properly.

---

## 1. Verify USB Connection

- Connect the Arduino Due to your computer using the **native USB port**.
- In MATLAB, use the following command to list available serial devices:

```matlab
serialportlist("all")
```

> Your Arduino Due should appear as a serial device (e.g. `COM4` or `/dev/ttyACM0`).

---

## 2. Run a Minimal Simulink Test

- Create a simple Simulink model that:
  - Reads an analog input (e.g. from the Beam SoftPot).
  - Sends the value to a `Scope` block.
- Use the **Custom Library** blocks to do this.
- Deploy the model using the "Deploy to Hardware" button or `Ctrl+B`.

![Minimal Simulink test setup](images/minimal_simulink_test.png)
<center>Minimal model for testing sensor input and visualization</center>

---


## 6. Common Issues

| Problem                           | Possible Cause                                    | Suggested Fix                            |
|-----------------------------------|---------------------------------------------------|------------------------------------------|
| No response from Arduino          | Wrong USB port, driver missing                    | Use native USB and check `serialportlist` |
| Upload error                      | Board not detected or incorrect model settings    | Recheck "Hardware Implementation" tab    |

---

If everything works as expected, you're now ready to begin the practical implementation tasks in this course.
