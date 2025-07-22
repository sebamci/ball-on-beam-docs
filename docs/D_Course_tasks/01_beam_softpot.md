# I. Read Ball Position

This task introduces the SoftPot linear position sensor as the primary input for detecting the ball’s position on the beam. You will learn how to connect it, read its analog values in Simulink, calibrate its range, and visualize the measurement.

---

## 1. Connect and Initialize

- The Beam SoftPot sensor is connected to the `Beam` Molex KK input of the Arduino shield via the provided cable.
- In Simulink, open your model and drag the `Calib_Beam_SoftPot` block from the custom library into your diagram.
- Connect the output of the `Calib_Beam_SoftPot` block to a `Scope` block or a `Display` block to monitor the raw analog values.

> Make sure the sensor is properly fixed on the beam and aligned with the ball path.

![SoftPot Block Connection](images/softpot_block_connection.png)
<center>Calib_SoftPot block connected to Scope for live signal monitoring</center>

---

## 2. Calibration

- Move the ball to the **far left** of the beam and note the raw ADC value shown in the Scope.
- Then move the ball to the **far right** and record that value as well.
- These two values define the sensor's minimum and maximum.
- Drag the `Read_Ball_Position` block from the custom library into your model.
- Double click the `Read_Ball_Position` block to set and apply these values as calibration parameters.
- Connect the output of the `Read_Ball_Position` block to a `Scope`.

> The output of the calibration block is now a normalized position signal in millimeters.

![Calibration Setup](images/softpot_calibration_scope.png)
<center>Calibrated SoftPot block</center>

---

## 3. Run Your First BoB Model

Now that the SoftPot is calibrated and integrated into your model, it's time to run your first simulation on the hardware.

Follow these steps:

1. Ensure that the Arduino Due is connected via the **programming USB port**.
2. Verify that the model is correctly configured for hardware deployment (see the previous setup chapters).
3. Click on `Monitor & Tune` in the Simulink `HARDWARE` tab.
4. After successful deployment, observe the Scope or Display block output while manually moving the ball across the beam.

> This test confirms that Simulink is communicating correctly with the hardware and that the SoftPot is providing meaningful, real-time data.

![Minimal Simulink test model for SoftPot](images/softpot_minimal_test_model.png)
<center>Minimal Simulink test model for the calibrated SoftPot</center>


---

## 4. Test and Validate

- Move the ball slowly across the beam and verify that the Scope signal reacts smoothly and proportionally.
- The full range should approximately match the physical length of the beam (0 mm to 189 mm).
- Look out for:
    - Non-linearity
    - Jumps or noise

---

## 5. Summary

| Step             | Action                                                     |
|------------------|------------------------------------------------------------|
| Hardware         | Control SoftPot must be connected via RLU 3-pin cable      |
| Calibration      | Use `Calib_Beam_SoftPot` block from custom library              |
| Simulink Block   | Use `Read_Ball_Position` block from custom library                    |
| Visualization    | Scope block or display block for real-time feedback        |

Once this task is complete, you have a reliable analog input for ball position and can proceed with servo integration in the next task.
