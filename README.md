# 🎛️ Arduino Potentiometer LED Control

## 📌 Project Idea
This project controls the brightness of an LED using a potentiometer.

- Rotate the potentiometer → LED brightness changes  
- Low value → dim light  
- High value → bright light  

---

## ⚙️ Components
- Arduino Uno  
- LED  
- 220Ω Resistor  
- Potentiometer  
- Breadboard  
- Jumper Wires  

---

## 🔌 Circuit Connection
- LED:
  - Pin 9 → LED → Resistor → GND 

- Potentiometer:
  - One side → 5V  
  - Other side → GND  
  - Middle pin → A0  

---

## 📷 Project Preview
<img width="667" height="509" alt="image" src="https://github.com/user-attachments/assets/1a33bd72-3f5f-450a-ba86-5ed2428a063c" />

---

## 💻 Code
```cpp
int potPin = A0;
int ledPin = 9;

int potValue = 0;
int brightness = 0;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  potValue = analogRead(potPin); // read potentiometer
  brightness = map(potValue, 0, 1023, 0, 255); // convert to PWM

  analogWrite(ledPin, brightness); // control LED brightness

  Serial.print("Pot: ");
  Serial.print(potValue);
  Serial.print(" | Brightness: ");
  Serial.println(brightness);

  delay(100);
}
