# controlling-DC-motor-using-L293D

first of all we have to understand the pinout of the L293D motor driver, the figure below shows the pinout of the motor driver 


![L293D-Pinout](https://github.com/user-attachments/assets/1b7bce65-0ba9-4da9-a52d-eeb3aa024c16)


the output pins are used to control the DC motor while the input pins are used to give commands from the Arduino to the motor driver to control the direction of the rotation. the enable pins are used to control the speed of the motor.


the circuit diagram is shown in the figure below 


![image](https://github.com/user-attachments/assets/b4f049c0-712d-48c2-ba70-a4a7191a9923)


the Arduino code to control the DC motor

```
const int motor1Pin1 = 5; 
const int motor1Pin2 = 4; 
const int motor1Enable = 3; 

const int motor2Pin1 = 7; 
const int motor2Pin2 = 8; 
const int motor2Enable = 9; 

void setup() {
  
  pinMode(motor1Pin1, OUTPUT);
  pinMode(motor1Pin2, OUTPUT);
  pinMode(motor1Enable, OUTPUT);
  pinMode(motor2Pin1, OUTPUT);
  pinMode(motor2Pin2, OUTPUT);
  pinMode(motor2Enable, OUTPUT);

  // Enable motors
  digitalWrite(motor1Enable, HIGH);
  digitalWrite(motor2Enable, HIGH);
}

void loop() {
  

  // Motor 1 forward
  digitalWrite(motor1Pin1, HIGH);
  digitalWrite(motor1Pin2, LOW);
  analogWrite(motor1Enable, 255); // Full speed

  // Motor 2 forward
  digitalWrite(motor2Pin1, HIGH);
  digitalWrite(motor2Pin2, LOW);
  analogWrite(motor2Enable, 255); // Full speed

  delay(2000); // Run motors for 2 seconds

  // Motor 1 backward
  digitalWrite(motor1Pin1, LOW);
  digitalWrite(motor1Pin2, HIGH);
  analogWrite(motor1Enable, 255); // Full speed

  // Motor 2 backward
  digitalWrite(motor2Pin1, LOW);
  digitalWrite(motor2Pin2, HIGH);
  analogWrite(motor2Enable, 255); // Full speed

  delay(2000); // Run motors for 2 seconds

  // Stop motors
  digitalWrite(motor1Pin1, LOW);
  digitalWrite(motor1Pin2, LOW);
  analogWrite(motor1Enable, 0);

  digitalWrite(motor2Pin1, LOW);
  digitalWrite(motor2Pin2, LOW);
  analogWrite(motor2Enable, 0);

  delay(2000); // Stop for 2 seconds
}
```
