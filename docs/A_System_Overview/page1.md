# System Overview

The Ball-on-Beam platform is a classical benchmark system in control engineering, widely used in education and research to demonstrate real-time feedback control principles. This documentation presents a low-cost and modular version of the platform, developed as part of a bachelor's thesis at the Management Center Innsbruck (MCI).

The system consists of a beam actuated by a servo motor and a ball whose position is to be stabilized by feedback control. Due to its inherent instability and nonlinear dynamics, it is ideal for teaching model-based control methods, real-time implementation, and system identification.

<center>IMG 3D Model</center>

## Objectives

This project aims to:

- Improve the mechanical stability and modularity of the platform,
- Enhance sensor precision and reduce electrical noise through ADC upgrades,
- Implement a Simulink-based control framework for real-time operation,
- Provide full documentation for assembly, calibration, and software setup.
- Facilitate hands-on learning of control engineering concepts through practical exercises.


## Key Features

- **Mechanical Design**: Improved support structure, laser-cut modular parts, and optimized ball guidance.
- **Electronics**: High-resolution analog signal acquisition, clean wiring concept, and external user interface elements.
- **Software Stack**: Model-based control using Simulink and custom S-Functions, with support for real-time execution on Arduino Due.
- **User Interaction**: Integrated manual control mode, system status via NeoPixel indicators, and serial debugging support.

## Educational Value

The platform is specifically designed for students to:

- Gain hands-on experience with sensors, actuators, and embedded systems,
- Understand the design and tuning of PID and lead controllers,
- Experiment with physical modeling and linearization in Simulink,
- Perform real-time control tasks and analyze system responses.

---

This overview serves as the foundation for the remaining documentation, which guides you step-by-step through setup, calibration, simulation, and control design.
