# Course Tasks

This section provides a structured overview of the course tasks for the Ball-on-Beam project, guiding you step by step through development, calibration, and testing phases.

---

## Structure

The course is divided into the following tasks:

1. **Read Ball Position**  
   Read analog position data from the beam SoftPot and calibrate it using Simulink.

2. **Control the Beam**  
   Control the beam angle using PWM output and calibrate the neutral position.

3. **Move the Beam Manually**  
   Use the analog rotary sensor to directly control the servo motor without feedback. This allows intuitive testing and manual balancing of the ball.

4. **Generate Setpoints**  
   Implement constant and dynamic target values (e.g. sine, step) to test controller behavior.

5. **Add Setpoints with Control SoftPot**  
   Use a second SoftPot sensor to define the dynamic target position (setpoint) of the ball in real-time.

6. **Implement Basic PID Control**  
   Test a basic PID controller using your setpoint and beam position data.

7. **Tune the PID Controller**  
   Analyze system behavior with tuned PID parameters and optimize for stability and response.

8. **Track Ball with SoftPot**
   Implement a control loop that uses the SoftPot to track the ball position dynamically, adjusting the beam angle accordingly.

9. **Add User Interface**  
   Switch between control modes using a pushbutton and indicate system states with NeoPixel LEDs.

10. **Show Mode**  
   Integrate all functions into a final demonstration-ready setup combining real-time control and user interface.

> Each task builds upon the previous one, make sure to complete them in order and always work in the same Simulink model and expand it as you progress.

---

## Navigation

The course tasks are structured to allow easy navigation between different sections. Each task builds upon the previous one, ensuring a smooth and logical progression.  
Use the navigation menu on the left side of the page to quickly access each chapter.
