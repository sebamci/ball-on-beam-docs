# VII. Tune the PID Controller

This task focuses on improving the performance of your PID controller by adjusting the individual parameters for proportional (P), integral (I), and derivative (D) action. Fine-tuning is essential for achieving fast, stable, and precise ball control.

---

## 1. Observe the Current Behavior

Before making any changes, carefully analyze how your system responds with the initial parameters:

- Is the response too slow or too aggressive?
- Does the ball overshoot the target position?
- Are there oscillations or noise in the output?

> Use the Scope to display both the setpoint and the actual ball position for direct comparison.

---

## 2. Adjust PID Parameters

Tune each parameter one at a time while keeping the others constant:

| Parameter | Effect                                                                  |
|-----------|-------------------------------------------------------------------------|
| **P**     | Increases responsiveness; too high may cause oscillations               |
| **I**     | Eliminates steady-state error; too high can cause slow oscillation      |
| **D**     | Dampens fast changes; reduces overshoot, but sensitive to noise         |
| **N**     | Filter for derivative action; helps reduce noise in the derivative term (higher N, less filtering) |

Start with only proportional gain and set I and D to zero:

- Try values like `P = 0.05`, `I = 0`, `D = 0`
- Gradually increase `I` to reduce offset
- Carefully add `D` if you observe overshoot or instability
- Use `N` to filter the derivative term if necessary

---

## 3. Use Live Tuning

- You can also tune your `PID Controller` while the model is running. Just double-click the block and adjust the parameters in real-time.

> Live tuning avoids repeated downloads and accelerates controller design.

---

## 4. Evaluate Performance

After tuning, test your controller with different setpoint profiles:

- Step inputs (sudden changes)
- Sine waves (periodic following)
- Manual changes via Control SoftPot

> The ideal response is fast, smooth, and without overshoot or steady-state error.

![Tuned PID response](images/pid_tuned_response.png)
<center>Setpoint tracking after PID tuning</center>

---

## 6. Summary

| Step             | Action                                                                  |
|------------------|-------------------------------------------------------------------------|
| Tuning Strategy  | Tune one parameter at a time, observe effect                            |
| Key Focus        | Balance responsiveness and stability                                    |
| Tools            | Use live tuning with model variables (Kp, Ki, Kd)                       |
| Goal             | Achieve smooth, fast, and accurate ball control                         |

With your tuned PID controller, you're ready to add the user interface and mode switching in the next task.
