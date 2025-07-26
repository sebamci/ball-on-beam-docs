# SoftPot Accuracy Test

This page documents a manual accuracy test of the SoftPot linear sensor, with 1% accuracy, connected to a ADS1115 16bit ADC, used for ball position tracking on the Ball-on-Beam platform. The goal is to evaluate how closely the sensor's output matches the true physical position of the ball.

---

## 1. Test Setup

To measure the absolute accuracy of the SoftPot sensor:

- A caliper was used to place a steel ball at defined distances along the beam
- At each position, the corresponding SoftPot reading was recorded via Simulink
- The measurement was repeated over the entire length of the beam in 10 mm steps

> The beam was kept level and static during measurement to ensure repeatability.

---

## 2. Raw Measurement vs. Reference

The following plot compares the measured values from the SoftPot sensor (x-axis) to the actual ball position (y-axis) in millimeters.

![SoftPot linearity test](images/Ballposition Genauigkeitstest.png)  
<center>Reference vs. Measured Position — ideal linearity is confirmed</center>

> The graph confirms that the calibrated SoftPot output closely follows a linear behavior over the entire sensing range.

---

## 3. Error Analysis

The absolute deviation between measurement and ground truth is shown below:

![SoftPot measurement deviation](images/Abweichung Ballposition.png)  
<center>Deviation between reference position and SoftPot reading</center>

Key observations:

- Most deviations are below ±0.6 mm
- One outlier (~0.8 mm) occurred
- The error is not strongly biased to one side, indicating symmetrical response.

---

## 4. Interpretation

The results confirm that:

- The SoftPot sensor offers sufficient resolution and repeatability for this application.
- Calibration using two edge points (min/max) is adequate.
- Additional filtering or averaging is not necessary for typical PID control.

> A measurement uncertainty below ±1 mm over a 190 mm beam length corresponds to an error margin of ~0.5%, which is acceptable for educational mechatronic systems.

---

## 5. Summary

| Parameter                  | Value                     |
|----------------------------|---------------------------|
| Beam Length                | 190 mm                    |
| Measurement Step Size      | 10 mm                     |
| Max Deviation (abs)        | ~0.9 mm                   |
| Typical Deviation Range    | ±0.6 mm                   |
| Conclusion                 | Sufficiently accurate     |

---

This analysis validates the use of the SoftPot sensor as a reliable position input for the Ball-on-Beam control system.
