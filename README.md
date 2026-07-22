# 4-Servo-Motor-Sweep-using-Arduino-Uno
An Arduino-based project designed using **Tinkercad Circuits** to control and synchronize four SG90 micro servo motors simultaneously. The project demonstrates sweep motion sequencing and centered positioning during startup setup.

---

### Features
* **Synchronized Motion:** Smoothly sweeps all 4 servo motors together from **0° to 180°** and back to **0°**.
* **Auto-Centering:** Sets all motors to their default neutral position (**90°**) upon initialization.
* **Efficient Code Structure:** Utilizes arrays and loop iterations for scalable code.

---

##  Hardware Requirements

| Component | Quantity | Notes / Connection |
| :--- | :---: | :--- |
| **Arduino Uno R3** | 1 | Microcontroller Board |
| **Micro Servo Motors (SG90)** | 4 | PWM Signal Pins: `9, 10, 11, 12` |
| **Breadboard** | 1 | For power distribution |
| **Jumper Wires** | Varies | Red (5V), Black (GND), Signal (Color-coded) |

---

## Circuit Schematic & Wiring

### Pin Configuration
* **Power Connections:**
  * Arduino `5V` $\rightarrow$ Breadboard Positive (+) Rail
  * Arduino `GND` $\rightarrow$ Breadboard Negative (-) Rail
  * All Servo `VCC` (Red Wires) $\rightarrow$ Breadboard Positive (+) Rail
  * All Servo `GND` (Black Wires) $\rightarrow$ Breadboard Negative (-) Rail

* **Signal Connections:**
  * Servo 1 Signal (Yellow Wire) $\rightarrow$ Arduino Pin `9`
  * Servo 2 Signal (Yellow Wire) $\rightarrow$ Arduino Pin `10`
  * Servo 3 Signal (Yellow Wire) $\rightarrow$ Arduino Pin `11`
  * Servo 4 Signal (Yellow Wire) $\rightarrow$ Arduino Pin `12`


<img width="1243" height="743" alt="Screenshot 2026-07-20 195025" src="https://github.com/user-attachments/assets/67fbe043-62d1-4ae3-846b-e8b3c96a60a2" />


---

##  Source Code

```cpp
#include <Servo.h>

// Create an array of 4 Servo objects
Servo servos[4];

// Array containing the signal output digital pins
int pins[] = {9, 10, 11, 12};

void setup() {
  // Attach each servo pin to its corresponding object
  for (int i = 0; i < 4; i++) {
    servos[i].attach(pins[i]);
  }

  // Sweep forward: 0 degrees to 180 degrees
  for (int pos = 0; pos <= 180; pos += 2) {
    for (int i = 0; i < 4; i++) servos[i].write(pos);
    delay(10);
  }

  // Sweep backward: 180 degrees to 0 degrees
  for (int pos = 180; pos >= 0; pos -= 2) {
    for (int i = 0; i < 4; i++) servos[i].write(pos);
    delay(10);
  }

  // Reset all servos to 90 degrees (Neutral Position)
  for (int i = 0; i < 4; i++) {
    servos[i].write(90);
  }
}
```
------

## The Result 
### [watch video](https://drive.google.com/file/d/1HaDu2ApBkuxWnW32JZnTHpwRk-GZMx2z/view?usp=drive_link)

