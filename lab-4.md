# NEUB CSE Microprocessor and Interfacing Lab Spring 2025 Lab 4

## Task 1
Hello World program in Arduino.

Circuit:

![Lab 4 Task 1 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-4/CSE-06133118-322-2501-lab4-task-1CKT_bb.png)

Code:
```c
int ledPin=13;
void setup() {
  // put your setup code here, to run once:
  pinMode(ledPin, OUTPUT);
  Serial.begin(115200);

}

void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(ledPin, HIGH);
  delay(1000);
  Serial.println("LED ON");
  digitalWrite(ledPin, LOW);
  delay(500);
  Serial.println("LED OFF");
}

```


## [Watch Class video Here](https://www.youtube.com/watch?v=ulclNTYsoGQ)
