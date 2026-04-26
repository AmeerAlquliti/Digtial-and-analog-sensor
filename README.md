# Arduino Motion Detection System (PIR + Potentiometer)

## 📌 Overview

This project demonstrates a motion detection system using a PIR (Passive Infrared) sensor with an Arduino Uno. The system detects motion and activates an LED as an indicator.

A potentiometer is used as an **independent analog input** to control system behavior, such as adjusting the delay time.

---

## 🎯 Objectives

* Detect motion using a PIR sensor
* Control an LED based on motion detection
* Use a potentiometer for adjustable system response

---

## 🧰 Components Used

* Arduino Uno
* PIR Motion Sensor
* LED
* Resistor (220Ω)
* Potentiometer
* Breadboard
* Jumper wires

---

## 🔌 Wiring Connections

### ⚡ Power Distribution

* Arduino **5V** → Breadboard **+ rail**
* Arduino **GND** → Breadboard **– rail**

---

### 🟢 PIR Sensor (Motion Input)

* VCC → 5V
* GND → GND
* OUT → Digital Pin **2**

---

### 🔵 Potentiometer (Analog Input)

* One side → 5V
* Other side → GND
* Middle pin (Wiper) → Analog Pin **A0**

---

### 🔴 LED (Output Indicator)

* Anode (long leg) → Digital Pin **13**
* Cathode (short leg) → 220Ω resistor → GND

---

## 🧭 Connection Summary

| Component      | Arduino Pin |
| -------------- | ----------- |
| PIR Sensor OUT | D2          |
| Potentiometer  | A0          |
| LED            | D9          |

---

## ⚙️ System Operation

1. The PIR sensor initializes (about 30–60 seconds).
2. It continuously monitors motion.
3. When motion is detected:

   * A HIGH signal is sent to the Arduino.
   * The LED turns ON.
4. The potentiometer value is read:

   * It controls the delay duration.
5. When no motion is detected:

   * The LED turns OFF.

---

## 💻 Arduino Code

```cpp id="7a2f6c"
int pirPin = 2;
int ledPin = 13;
int potPin = A0;

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int motion = digitalRead(pirPin);
  int potValue = analogRead(potPin);

  if (motion == HIGH) {
    digitalWrite(ledPin, HIGH);
    Serial.print("Motion detected | Pot value: ");
    Serial.println(potValue);

    delay(potValue); // Potentiometer controls delay time
  } else {
    digitalWrite(ledPin, LOW);
  }
}
```



---

## 📊 Applications

* Motion-based security systems
* Smart lighting
* Energy-saving automation
* IoT projects

---

## ⚠️ Important Notes

* The PIR sensor requires an initialization time (~30–60 seconds).
* Avoid placing the sensor near heat sources for accurate readings.
* Ensure all components share a common ground (GND).
* Many PIR sensors include onboard controls for sensitivity and delay.

---

## 🚀 Future Improvements

* Use PWM to control LED brightness
* Add a buzzer for sound alerts
* Integrate WiFi (ESP8266 / ESP32) for notifications

---


