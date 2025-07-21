# Software Setup

This section provides a step-by-step guide to the software setup required for operating the Ball-on-Beam platform. It covers all essential tools, configuration steps, and calibration procedures needed to get the system running using Simulink and the Arduino-based hardware.

The platform is designed for model-based development and real-time control using MATLAB/Simulink in combination with a custom Arduino shield. All control logic is implemented via Simulink blocks and deployed directly to the microcontroller.

---

## Structure

The software setup is divided into the following subchapters:

- **Required Tools**  
  Installation of MATLAB, Simulink and the necessary toolboxes, such as the Simulink Support Package.

- **Simulink Environment**  
  Loading the custom Simulink block library developed specifically for the Ball-on-Beam platform. This includes sensor input blocks, actuator output blocks, and user interface elements such as the pushbutton, rotary knob, and NeoPixels.

- **Uploading to Arduino**  
  Generating and deploying code using Simulink's Embedded Coder.

- **Calibration**  
  Adjusting sensor and servo parameters for accurate system behavior.

- **Testing and Troubleshooting**  
  Verifying the setup, running initial tests, and diagnosing common issues.

---

## System Overview Diagram

The figure below shows the overall software architecture of the Ball-on-Beam platform, including key components such as Simulink models, calibration inputs, and real-time I/O.

![System Software Architecture (Diagram)](images/software_architecture_diagram.png)

<center>System Software Architecture (simplified overview)</center>

---

## Required Hardware Interfaces

The following components must be connected before starting the software setup:

- Arduino Due + custom shield
- SoftPot linear sensor
- Servo motor
- Rotary knob and pushbutton
- NeoPixel modules

Ensure that all components are mounted and wired as described in the assembly chapters.