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

## 📷 Gallery
| Front View | Top View |
|------------|----------|
| ![Front](Images/front_view.jpg) | ![Top](Images/top_view.jpg) |


# Testing Summary
- Obstacle detection accurate from 2 cm to 100 cm
- Response time: < 0.5 seconds
- Successfully avoids obstacles in structured environments
- Limitations in detecting narrow gaps (documented in report)

# Future Enhancements
- Use of LiDAR for better accuracy
- Integration with cloud for data logging
- Machine learning-based predictive pathfinding

