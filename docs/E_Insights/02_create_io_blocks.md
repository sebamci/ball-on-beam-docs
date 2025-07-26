# Create Custom I/O Builder Blocks

This tutorial explains how to use the Simulink I/O Builder to create custom hardware interface blocks that integrate with your Arduino-based platform. These blocks allow you to directly access sensors, actuators, and other peripherals using your own C++ code, while keeping your model clean and modular.

---

## 1. Requirements

Before you begin, make sure you have:

- MATLAB and Simulink installed
- The **Arduino Support Package** (installable via Add-On Explorer)
- A **working Arduino sketch** in the Arduino IDE that verifies your code and logic (e.g. sensor reading or servo control)

> The working sketch serves as a reference for implementing the same logic inside the Simulink block.

---

## 2. Open the I/O Builder

To create a new custom block:

1. Open Simulink.
2. Go to **Embedded Coder > I/O Builder**.
3. A new I/O Builder window will open where you can manage your blocks and source files.

---

## 3. Add a New Block

- Click on **Add Custom Block** and give it a meaningful name (e.g. `Beam_SoftPot`, `ServoPositionController`).
- This will open the block configuration panel where you define code files, ports, and parameters.

---

## 4. Include Source Files and Library

- You will be prompted to provide:
  - The **folder** containing your source code.
  - The **individual source code files** (e.g. `.cpp`, `.h`).

> If your block only depends on code from the Arduino library, you can create a **dummy library folder**:
> 
> - Create an empty folder and add a `dummy.cpp` file (this file may be empty).
> - Select this folder and file during setup. This tricks the I/O Builder into generating the block correctly, even without additional libraries.

---

## 5. Define Ports and Parameters

- Add inputs and outputs:
  - Data types can be: `int8`, `int16`, `int32`, `uint8`, `double`, etc.
- You can also define parameters and mark them as **Tunable**, so they can be changed during runtime (e.g. calibration values).

---

## 6. Implement the Logic

In your `.cpp` file, define the logic for:

- **Setup Function**: Initialize your hardware (e.g. pinMode, Servo.attach).
- **Step Function**: Read sensor values or write outputs each control loop cycle.

Example:

```cpp
void setupFunctionXYZ() {
    pinMode(A0, INPUT);
}

void stepFunctionXYZ(double* output) {
    output[0] = analogRead(A0);
}
```

> These functions are mapped by name inside the I/O Builder GUI. Don't forget to include necessary headers (e.g. `#include <Arduino.h>`, `#include <Servo.h>`).
> Don't change the function names or variables unless you also update them in the .hpp file and .m - file.

---

## 7. Optional: Customize the Block Mask

You can edit the block’s icon and labels via `Mask > Edit Mask`.

This is useful for:

- Adding your own block symbol / image
- Providing a description of the block's functionality
- Naming ports clearly
- Hiding/showing advanced settings

---

## 8. Save and Use the Block

- Save your model in the same folder as your C++ files, or use MATLAB’s project structure to manage dependencies.
- The generated block can now be used like any Simulink block and deployed to Arduino hardware using **Monitor & Tune**.

> Note: You can also copy the generated .m file to your project and use the `Matlab System` block to call your custom functions directly. But don't change the folder structure or file names, as the I/O Builder relies on specific naming conventions.

---

## 9. Troubleshooting

Common issues include:
- **Folder Structure with invalid characters**: Ensure your folder names do not contain spaces or special characters (e.g. `C:\My Folder` should be `C:\My_Folder`).
- **Multiple I/O Builder Blocks not working together**: If you have multiple custom blocks, ensure they do not share the same function names or variable names in your C++ code. Each block should have unique identifiers to avoid conflicts. Another option to fix this issue is to change the first lines of the .h file to a unique name. Every block should have its own unique header guard to prevent conflicts.

```cpp
#ifndef EXAMPLE_H
#define EXAMPLE_H

to

#ifndef BEAM_SOFTPOT_H
#define BEAM_SOFTPOT_H
```

---

## Summary

| Step                  | Description                                              |
|-----------------------|----------------------------------------------------------|
| I/O Builder           | Tool to create Simulink blocks with custom C++ code      |
| Source Integration    | Add your `.cpp`, `.h`, or dummy files as needed          |
| Port Definition       | Define inputs, outputs, and tunable parameters           |
| Hardware Logic        | Setup and step functions for Arduino interaction         |
| Reusability           | Create modular and reusable components                   |

This approach gives you full flexibility to extend your Simulink-based control system with custom hardware functionality.