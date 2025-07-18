### Task1 (﻿﻿﻿make a latching power switch circuit with auto power off and on.)
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
View Circuit Image
 • 💻 Arduino Code File:
Download Code
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
