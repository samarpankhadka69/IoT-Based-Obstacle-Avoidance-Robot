# IoT-Based Obstacle Avoidance Robot

An Arduino-based autonomous robot capable of detecting and avoiding obstacles using ultrasonic sensors and servo motors. This project was developed as part of the **CC5068NI - Cloud Computing and Internet of Things** module during Spring Semester 2025 at Islington College.

# Features
- Real-time obstacle detection using HC-SR04 ultrasonic sensor
- Autonomous path adjustment with servo-based scanning
- Controlled by Arduino Uno with L293D Motor Driver Shield
- Low-cost, educational prototype for learning embedded systems and IoT

# Components Used
- Arduino Uno
- L293D Motor Driver Shield
- HC-SR04 Ultrasonic Sensor
- Servo Motor
- 4 × Gear Motors with Wheels
- Lithium-Ion Battery & Holder
- Jumper Wires
- Breadboard/Chassis

# How It Works
The ultrasonic sensor scans the surroundings using a servo motor. If an obstacle is detected within a threshold distance, the Arduino processes the data and commands the motors to change direction accordingly. The robot operates fully autonomously without user input.

# Project Structure

## Gallery
<img width="625" height="728" alt="image" src="https://github.com/user-attachments/assets/fe5860a0-d16e-42e9-abf9-4796823264f4" />
<img width="269" height="360" alt="image" src="https://github.com/user-attachments/assets/9bf1b143-a50c-41c7-8b14-7c5ee304989c" />



# Code 
#include <Servo.h>
#include <AFMotor.h>

// Pin definitions
#define Echo A0
#define Trig A1
#define ServoPin 10
#define Speed 170
#define ServoCenter 103

// Motor setup
AF_DCMotor M1(1);
AF_DCMotor M2(2);
AF_DCMotor M3(3);
AF_DCMotor M4(4);

// Global variables
Servo servo;
char value;
int distance, Left, Right;

void setup() {
  Serial.begin(9600);
  pinMode(Trig, OUTPUT);
  pinMode(Echo, INPUT);
  servo.attach(ServoPin);

  M1.setSpeed(Speed);
  M2.setSpeed(Speed);
  M3.setSpeed(Speed);
  M4.setSpeed(Speed);
}

void loop() {
  // Uncomment one of the following as needed
  ObstacleAvoidance();
  // BluetoothControl();
  // VoiceControl();
}

// --- Obstacle Avoidance Logic ---
void ObstacleAvoidance() {
  distance = ultrasonic();

  if (distance <= 25) {
    Stop();
    backward();
    delay(100);
    Stop();

    Left = scanLeft();
    Right = scanRight();

    servo.write(ServoCenter);
    delay(800);

    if (Left > Right) {
      left();
    } else {
      right();
    }
    delay(500);
    Stop();
  } else {
    forward();
  }
}

// --- Bluetooth Control ---
void BluetoothControl() {
  if (Serial.available() > 0) {
    value = Serial.read();
    Serial.println(value);
  }


# Testing Summary
- Obstacle detection accurate from 2 cm to 100 cm
- Response time: < 0.5 seconds
- Successfully avoids obstacles in structured environments
- Limitations in detecting narrow gaps (documented in report)

# Future Enhancements
- Use of LiDAR for better accuracy
- Integration with cloud for data logging
- Machine learning-based predictive pathfinding

