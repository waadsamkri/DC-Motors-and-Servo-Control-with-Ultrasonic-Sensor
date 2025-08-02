# 🤖 DC Motors and Servo Control with Ultrasonic Sensor

## 📋 Description
This project uses an Ultrasonic Distance Sensor to measure the distance in front of the device. Based on the distance, it controls four DC motors and a servo motor to steer and rotate the device:

- 🚗 If the distance is greater than 60 inches (152 cm), the servo gradually rotates right and the motors turn the device right.
- 🚙 If the distance is less than or equal to 60 inches, the servo gradually rotates left and the motors turn the device left.
- ⏸️ If no valid distance is detected, the motors stop and the servo returns to the center.

---

## 🔧 Components Required
- Arduino board (e.g., Arduino Uno)  
- 4 DC motors with motor driver (e.g., L293D or L298N)  
- Ultrasonic distance sensor (HC-SR04)  
- Servo motor  
- Jumper wires  
- Power supply for motors and servo  

---

## 📌 Pin Configuration

| Component            | Pin in Code            | Description                 |
| -------------------- | ---------------------- | --------------------------- |
| Motor1 (Front Right)  | 9 (PWM), 8 (Digital)   | Speed control and direction |
| Motor2 (Front Left)   | 11 (PWM), 10 (Digital) | Speed control and direction |
| Motor3 (Rear Right)   | 6 (PWM), 4 (Digital)   | Speed control and direction |
| Motor4 (Rear Left)    | 3 (PWM), 2 (Digital)   | Speed control and direction |
| Servo Motor           | 14 (PWM Digital)       | Servo control               |
| Ultrasonic Trigger    | 12                     | Trigger pin for sensor      |
| Ultrasonic Echo       | 13                     | Echo pin for sensor         |

---

## ⚙️ Code Explanation
- 📏 **Distance Measurement:** Uses `readUltrasonicDistance()` to get distance from the sensor.  
- 🎛️ **Servo Control:** Rotates servo gradually left or right depending on the distance.  
- 🔄 **Motor Control:** Motors rotate the device left or right by activating PWM and direction pins accordingly.  
- ⏲️ **Delay:** A small delay (`delay(50)`) ensures smooth servo and motor updates.  

---

## 🚀 How to Use
1. Connect all components according to the pin configuration.  
2. Upload the code to the Arduino board using the Arduino IDE.  
3. Power up the device.  
4. Place an object in front of the ultrasonic sensor and observe servo and motor behavior based on the distance.  

---

## 🔧 Notes
- You can adjust `thresholdDistanceCm` to set the distance threshold.  
- Adjust `motorSpeed` (0-255) to control motor speed.  
- Make sure to use a proper power supply to safely run the motors and servo.  

---

## 📤 Expected Output Behavior:
1. When an object is detected farther than 60 inches (152 cm):  
   - The servo rotates right gradually by 1 degree every 50 ms until it reaches 0°.  
   - The motors rotate the device to the right at full speed (PWM 255).  

2. When an object is detected at 60 inches or closer:  
   - The servo rotates left gradually by 1 degree every 50 ms until it reaches 180°.  
   - The motors rotate the device to the left at full speed (PWM 255).  

3. If no valid distance is detected:  
   - All motors stop.  
   - Servo resets to center position (90°).  
   - The servo and motors update smoothly every 50 milliseconds for gradual turning.  
