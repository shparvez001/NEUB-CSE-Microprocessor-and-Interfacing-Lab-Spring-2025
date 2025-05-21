# NEUB CSE Microprocessor and Interfacing Lab Spring 2025 Lab 8

## Task 1
Driving DC motor using L298 motor driver module.

Circuit:
![L298 Motor Driver Module pinout](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-8/l298n-module-pinout.jpg)
![Lab 8 Task 1 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-8/CSE-06133118-322-2501-lab8-task-1-2CKT_bb.png)


Code:
```c
int in1=3;
int in2=4;
int enA=5;

void setup() {
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(enA, OUTPUT);
  Serial.begin(115200);
}

void loop() {
  digitalWrite(enA, HIGH);
  //ROtate in one direction
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  Serial.println("Rotate in one direction");
  delay(1000);

  //Rotate in Opposite direction
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  Serial.println("Rotate in Opposite direction");
  delay(1000);
}
```

## Task 2
Varying Speed of DC motor using L298 motor driver module.

Circuit:
![Lab 8 Task 2 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-8/CSE-06133118-322-2501-lab8-task-1-2CKT_bb.png)

Code:
```c
int in1=3;
int in2=4;
int enA=5;

void setup() {
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(enA, OUTPUT);
  Serial.begin(115200);
}

void loop() {
  analogWrite(enA,180); //Varying the speed by providing a value from 0-255
  //ROtate in one direction
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  Serial.println("Rotate in one direction");
  delay(1000);

  //Rotate in Opposite direction
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  Serial.println("Rotate in Opposite direction");
  delay(1000);
}
```

## Task 3
Driving a Servo motor.

Circuit:
![Lab 8 Task 3 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-8/CSE-06133118-322-2501-lab8-task-3CKT_bb.png)

Code:
```c
#include<Servo.h>

Servo servo1;
int servo1pin=9;
int value;

void setup()
{
  servo1.attach(servo1pin);
  Serial.begin(115200);
}

void loop()
{
  if(Serial.available()>0)
  {
    value=Serial.read(); //Expecting value of 0 - 9
    value=value-48;
    if(value<=9&&value>=0)
    {
      value=value*20;
      servo1.write(value);
      Serial.print("Angle is ");
      Serial.println(value);
    }
    else{
      Serial.println("Angle out of bound");
    }
  }
}
```


## [Watch Class video Here](https://youtu.be/P47bwlIud5U)
