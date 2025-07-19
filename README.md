### Task1 (﻿make a latching power switch circuit with auto power off and on.)
## 🔌 Latching Power Switch with Auto On/Off using PIR & Push Button (Arduino)

This project demonstrates how to build a latching power switch system using an Arduino Uno, a PIR motion sensor, and a push button. The system turns on an LED when motion is detected or when the button is pressed, and automatically turns it off after 10 seconds of inactivity.

---

### 📷 Project Components:
- Arduino Uno  
- PIR Motion Sensor  
- Push Button  
- LED  
- Resistor (220Ω for LED)  
- Breadboard + Jumper Wires  

---

### 💡 Project Functionality:

- 🔘 Manual Activation: Pressing the push button turns the system ON (LED lights up).
- 🕵️‍♂️ Motion Detection: If motion is detected by the PIR sensor, the system turns ON.
- ⏳ Auto Turn Off: If no motion or button press occurs for 10 seconds, the system automatically turns OFF.

---
### 🔗 Useful Links
 ### • 🔧 Tinkercad Circuit Image:
![Latching Power Switch Circuit](https://github.com/JawaherMQ5/Task1-week4/blob/main/T1-PIR.png)
 ### • ▶️ Demo Video:
https://drive.google.com/file/d/1CmkTs7jXkRkQkdUNyvlPnspf83YovzcU/view?usp=drive_link

---
### 🔄 Logic Overview (Based on the Code):

```cpp
const int pirPin = 2;
const int ledPin = 13;
const int buttonPin = 4;

bool systemOn = false;
unsigned long lastMotionTime = 0;
unsigned long timeout = 10000; // 10 seconds

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  if (digitalRead(buttonPin) == LOW) {
    systemOn = true;
    lastMotionTime = millis();
    digitalWrite(ledPin, HIGH);
  }

  if (digitalRead(pirPin) == HIGH) {
    systemOn = true;
    lastMotionTime = millis();
    digitalWrite(ledPin, HIGH);
  }

  if (systemOn && millis() - lastMotionTime > timeout) {
    systemOn = false;
    digitalWrite(ledPin, LOW);
  }
}
```
---
### Task2:A (design and programming of digital sensor).
# 🔧 Design and Programming of Digital IR Sensor with Arduino

## 📌 Project Overview

This project demonstrates the use of a digital IR (infrared) sensor to detect nearby objects.  
When the IR sensor detects something (like a hand), an LED lights up as a response.

The IR sensor works digitally — it sends HIGH or LOW based on object detection.  
This setup is ideal for simple automation like obstacle sensing, motion alerts, or touchless control.

---

## 🧠 How It Works

- The IR sensor emits infrared light.
- When an object reflects the IR light back to the sensor, the OUT pin goes HIGH.
- Arduino receives the signal via pin D2 and turns ON the LED on pin 13.
- When there's no object, the signal goes LOW and the LED turns OFF.

---

## ⚙️ Components Used

- ✅ Arduino Uno  
- ✅ IR sensor module (digital output)  
- ✅ LED  
- ✅ 220Ω resistor  
- ✅ Breadboard & jumper wires  

---

## 🔌 Circuit Diagram
![IR Sensor Arduino Circuit](https://github.com/JawaherMQ5/Task1-week4/blob/main/Digital%20sensor.png) 
---
## 📎 Tinkercad Link
https://www.tinkercad.com/things/1BFGI3Ufllk-digital-sensor/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard
---
## 🧾 Arduino Code

```cpp
const int irPin = 2;      // IR sensor output
const int ledPin = 13;    // LED or fan
unsigned long lastDetectTime = 0;
unsigned long timeout = 5000; // 5 ثواني

bool systemOn = false;

void setup() {
  pinMode(irPin, INPUT);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  if (digitalRead(irPin) == HIGH) {
    systemOn = true;
    lastDetectTime = millis();
    digitalWrite(ledPin, HIGH);
  }

  if (systemOn && (millis() - lastDetectTime > timeout)) {
    systemOn = false;
    digitalWrite(ledPin, LOW);
  }
}
```

