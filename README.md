# 🪭  Smart Fan Control Using Image Processing System

This project demonstrates how to control the speed of a DC motor (fan) using **hand gestures**, detected using **Python, OpenCV, and MediaPipe**, and then sent to an **Arduino** via serial communication.
The Arduino processes the gesture signals and adjusts the fan’s speed accordingly.



## 📌 Table of Contents

* Overview
* Hardware Requirements
* Software Requirements
* Features
* How It Works
* Wiring Diagram
* Connection Setup
* Arduino Code
* Python Code
* Installation
* Usage
* Expected Output
* Additional Notes
* Project Structure



## 🔍 Overview

A webcam detects different hand gestures and sends the gesture commands to the Arduino over serial communication.
The Arduino controls the fan motor through an L298N motor driver.


### Supported Hand Gestures

| Gesture | Meaning                  |
| ------- | ------------------------ |
| 🤟      | Fan ON at constant speed |
| 🤚      | Fan OFF                  |
| 👎      | Decrease fan speed       |
| 👍      | Increase fan speed       |
| 👌      | Set specific fan speed   |
| ✊       | Mode / signal change     |


## 🔧 Hardware Requirements

* Arduino Uno
* L298N Motor Driver
* DC Motor / Fan Motor
* Webcam
* Jumper Wires & Breadboard
* 9V/12V Motor Power Supply


## 💻 Software Requirements

* Python 3.x
* OpenCV
* MediaPipe
* PySerial
* Arduino IDE


## ⭐ Features

* Real-time hand gesture detection via webcam
* Controls fan ON/OFF
* Adjusts fan speed (increase/decrease)
* Uses Python → Arduino communication
* Smooth PWM motor control


## ⚙️ How It Works

### 1. Gesture Detection (Python)

* Python uses **OpenCV + MediaPipe** to detect hand landmarks.
* Each gesture is classified into a command (ON, OFF, Speed Up, Speed Down).

### 2. Serial Communication

* Python sends commands like `"0"`, `"1"`, `"2"`, `"3"`, or speed values to Arduino.

### 3. Motor Control (Arduino)

* Arduino receives the gesture signal
* Arduino uses PWM on ENA pin to control the fan speed
* L298N driver powers the DC motor


## 🔌 Wiring Diagram

Arduino Pin 6  → L298N ENA  
Arduino Pin 3  → L298N IN1  
Arduino Pin 5  → L298N IN2  
Arduino GND    → L298N GND  
Arduino 5V     → L298N 5V  
12V Supply     → L298N 12V  
Motor          → L298N OUT1 / OUT2


## 🔗 Connection Setup

1. Connect the DC motor to L298N motor driver (OUT1, OUT2)
2. Connect L298N to Arduino:

   * ENA → Pin 6
   * IN1 → Pin 3
   * IN2 → Pin 5
3. Connect L298N GND to Arduino GND
4. L298N 5V → Arduino 5V
5. L298N 12V → External Power Supply (9V/12V)

## 📥 Installation

### 1. Python Setup

Install required libraries:

```
pip install opencv-python mediapipe pyserial
```

### 2. Arduino Setup

* Install Arduino IDE
* Upload the provided Arduino code to Arduino Uno


## ▶️ Usage

Run the Python script:

```
python hand_gesture_control.py
```

Make sure the correct COM port is used in your Python code.

### Use these gestures:

| Gesture | Action           |
| ------- | ---------------- |
| 🤟      | Fan ON           |
| 🤚      | Fan OFF          |
| 👎      | Fan Speed ↓      |
| 👍      | Fan Speed ↑      |
| 👌      | Set custom speed |
| ✊       | Mode change      |


## 📊 Expected Output

* **🤟** → Motor starts at a constant ON speed
* **🤚** → Motor stops
* **👎** → Motor speed decreases
* **👍** → Motor speed increases
* **👌** → Sets a specific speed (0–255 PWM)
* **✊** → Changes signal mode


## 📝 Additional Notes

* Ensure correct **COM port** is selected in Python
* PWM speed values must be **0–255**
* Use external power supply for the motor
* Arduino must remain connected during operation


## 📁 Project Structure

Hand-Gesture-Fan-Control/
│── Arduino/
│   └── motor_control.ino
│── Python/
│   └── hand_gesture_control.py
└── README.md
