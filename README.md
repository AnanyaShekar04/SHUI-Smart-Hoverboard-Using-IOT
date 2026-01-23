# 🛹 SHUI: Smart Hoverboard Using IoT

![Status](https://img.shields.io/badge/Status-Prototype_Completed-success) ![Hardware](https://img.shields.io/badge/Hardware-Arduino_UNO-blue) ![Focus](https://img.shields.io/badge/Focus-Assistive_Tech-orange)

**SHUI (Smart Hoverboard Using IoT)** is an autonomous mobility prototype designed to assist visually impaired individuals. Unlike standard hoverboards that require physical balancing, SHUI utilizes an **Ultrasonic-based Obstacle Avoidance System** to navigate environments independently, acting as a motorized alternative to smart blind sticks.

## 📖 Overview
The project aims to revolutionize personal transportation for the blind by integrating **IoT sensors** and **embedded logic** into a four-wheeled vehicle frame. The system continuously scans its surroundings to detect obstacles and intelligently decides the safest path, ensuring a collision-free commute.

## 🚀 Key Features
* **👁️ Autonomous Navigation:** Uses an HC-SR04 Ultrasonic Sensor to detect obstacles within **40 cm**.
* **🧠 Intelligent Path Planning:** When an obstacle is detected, the system pauses and scans Left (0°) and Right (180°) to calculate the optimal route.
* **⚙️ Differential Drive:** Controls four high-torque DC geared motors independently using an L293D driver to execute sharp turns.
* **🔋 Regulated Power System:** Features a custom 12V-to-9V power module to safely distribute power between the motors and the microcontroller.

## 🛠️ Hardware Stack
* **Microcontroller:** Arduino UNO (ATmega328P)
* **Motor Driver:** L293D Shield (Dual H-Bridge Configuration)
* **Sensors:** HC-SR04 Ultrasonic Sensor (Time-of-Flight)
* **Actuators:**
    * 4x 12V DC Geared Motors (30 RPM) for high-torque movement.
    * SG-90 Servo Motor for 180-degree sensor scanning.
* **Power:** 12V Li-Ion Battery / Adapter.

## 🤖 Navigation Logic (The Algorithm)
The system operates on a continuous feedback loop defined in the firmware:

1.  **Forward Scan:** The hoverboard moves forward while measuring distance `F`.
2.  **Threshold Check:** If `F < 40cm`, the motors stop immediately.
3.  **Surveillance Routine:**
    * Servo rotates **Left** $\rightarrow$ Records `Distance_L`.
    * Servo rotates **Right** $\rightarrow$ Records `Distance_R`.
4.  **Decision Matrix:**
    * If `Distance_L > Distance_R` $\rightarrow$ **Turn Left** (Right motors Forward, Left motors Backward).
    * If `Distance_R > Distance_L` $\rightarrow$ **Turn Right** (Left motors Forward, Right motors Backward).
    * If Distances are Equal $\rightarrow$ **Reverse**.

## 📂 Repository Structure
* **`firmware/`**: Arduino C++ sketches for motor control and sensor logic.
* **`schematics/`**: Circuit diagrams and wiring photos of the prototype.
* **`docs/`**:
    * **Presentation 1** - Introduction to the project concept.
    * **Project Synopsis** - Abstract and problem statement.
    * **Final Presentation** - Design defense and results.
    * **Technical Report** - Detailed documentation and error analysis.
