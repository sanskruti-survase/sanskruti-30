Smart Follower Bot
A Simple Robot That Follows a Line Automatically

 Problem Statement:
In many places like factories, hospitals, and warehouses, there is a need for small robots that can carry materials or items along a fixed path. Manually controlling such robots takes time and effort. A smart robot that can automatically follow a path can make this job easier and save time.
 Proposed Solution:
To solve this problem, we will create a small, low-cost robot that follows a black line drawn on the floor using infrared (IR) sensors. This robot will use an Arduino Uno as its brain, and a motor driver to control the wheels. It will be able to turn left or right based on the position of the black line and stop if it goes off the path.
This kind of robot is ideal for students and beginners to understand real-time embedded systems, sensors, and motor control.
SOFTWARE:


 Components Required:
Component
Quantity
Purpose
Arduino Uno
1
Controls the whole robot
IR Sensors
2
Detects black line and white surface
L298N Motor Driver
1
Controls direction and speed of motors
DC Motors
4
Drives the wheels of the robot
Breadboard
1
For connecting power and signals
Jumper Wires
Many
For connections

 How It Works (Working Principle):
The IR sensors are placed at the front of the robot.
They detect the color of the surface below them:
Black line → sensor gives LOW signal
White surface → sensor gives HIGH signal
The Arduino reads the sensor signals:
If both sensors detect black → Move forward
If left sensor is on black, right is on white → Turn left
If right sensor is on black, left is on white → Turn right
If both sensors are on white → Stop



CODES : 
Line Following Robot
#define LEFT_MOTOR_IN1  8  
#define LEFT_MOTOR_IN2  9  
#define RIGHT_MOTOR_IN3 10 
#define RIGHT_MOTOR_IN4 11

#define LEFT_SENSOR     2  
#define RIGHT_SENSOR    3   

void setup() {
  pinMode(LEFT_MOTOR_IN1, OUTPUT);
  pinMode(LEFT_MOTOR_IN2, OUTPUT);
  pinMode(RIGHT_MOTOR_IN3, OUTPUT);
  pinMode(RIGHT_MOTOR_IN4, OUTPUT);
 
  pinMode(LEFT_SENSOR, INPUT);
  pinMode(RIGHT_SENSOR, INPUT);
}

void loop() {
  int leftSensorValue = digitalRead(LEFT_SENSOR);   
  int rightSensorValue = digitalRead(RIGHT_SENSOR); 

  if (leftSensorValue == 0 && rightSensorValue == 0) {
    moveForward();
  } else if (leftSensorValue == 0 && rightSensorValue == 1) {
    turnLeft();
  } else if (leftSensorValue == 1 && rightSensorValue == 0) {
    turnRight();
  } else {
    stopMotors();
  }
}

void moveForward() {
  digitalWrite(LEFT_MOTOR_IN1, HIGH);
  digitalWrite(LEFT_MOTOR_IN2, LOW);
  digitalWrite(RIGHT_MOTOR_IN3, HIGH);
  digitalWrite(RIGHT_MOTOR_IN4, LOW);
}

void turnLeft() {
  digitalWrite(LEFT_MOTOR_IN1, LOW);
  digitalWrite(LEFT_MOTOR_IN2, HIGH);
  digitalWrite(RIGHT_MOTOR_IN3, HIGH);
  digitalWrite(RIGHT_MOTOR_IN4, LOW);
}

void turnRight() {
  digitalWrite(LEFT_MOTOR_IN1, HIGH);
  digitalWrite(LEFT_MOTOR_IN2, LOW);
  digitalWrite(RIGHT_MOTOR_IN3, LOW);
  digitalWrite(RIGHT_MOTOR_IN4, HIGH);
}

void stopMotors() {
  digitalWrite(LEFT_MOTOR_IN1, LOW);
  digitalWrite(LEFT_MOTOR_IN2, LOW);
  digitalWrite(RIGHT_MOTOR_IN3, LOW);
  digitalWrite(RIGHT_MOTOR_IN4, LOW)

Pin Connections:
Component
Arduino Pin
Function
Left IR Sensor
D2
Reads left line data
Right IR Sensor
D3
Reads right line data
L298N IN1
D8
Left motor direction
L298N IN2
D9
Left motor direction
L298N IN3
D10
Right motor direction
L298N IN4
D11
Right motor direction
Power Lines
5V, GND
Shared power supply

Logic of Movement:
Sensor Reading
Action
Both LOW
Move forward
Left LOW, Right HIGH
Turn left
Left HIGH, Right LOW
Turn right
Both HIGH
Stop


 Applications in Real Life:
Robots for line-following competitions
Automated material delivery in factories
Smart robots in hospitals to carry supplies
Education kits for learning robotics and coding
Base idea for self-driving car logic in small scale


 Summary:
The Smart Follower Bot is a beginner-friendly and practical project that teaches the use of sensors, motor drivers, and Arduino programming. It is useful in many real-life cases where repetitive movement along a fixed path is required. This robot works based on simple logic and sensor feedback and is easy to build and test.


