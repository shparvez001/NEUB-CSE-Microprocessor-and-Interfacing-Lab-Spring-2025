# NEUB CSE Microprocessor and Interfacing Lab Spring 2025 Lab 6

## Task 1
EEPROM read and write code.

Circuit:
In either of the following circuits, you can use 4 or 8 LEDs. The circuit is the same, just the number of LEDs and the pins used are different. Use Resistance value of 220 ohm for each LED.
To use with 4 LEDs, use the following circuit:
![Lab 6 Task 1 Circuit in breadboard with 4 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-6/CSE-06133118-322-2501-lab6-task-1-2-variant1CKT_bb.png)

To use with 8 LEDs, use the following circuit:
![Lab 6 Task 1 Circuit in breadboard with 8 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-6/CSE-06133118-322-2501-lab6-task-1-2-variant2CKT_bb.png)

Code:
```c
#include<EEPROM.h>

const int ledPins[8]={A0,A1,A2,A3,A4,A5,2,3};

void setup() {

  Serial.begin(115200);

  for(int i=0;i<8;i++)
  {
    pinMode(ledPins[i],OUTPUT);
  }
  
  
  for(int i=0;i<16;i++)
  { 
    EEPROM.write(i,i);
    delay(100);
  }

  for(int i=0;i<16;i++)
  { 
    byte value=EEPROM.read(i);
    displayByteOnLED(value);
    Serial.println(value);
    delay(1000);
  }


}

void loop() {
  // Nothing
  Serial.println("Entered void loop");
  delay(10000);
}


void displayByteOnLED(byte value)
{
  for(int i=0;i<8;i++)
  {
    digitalWrite(ledPins[i],value>>i & 1);
  }
}

```

## Task 2
Using EEPROM to store a pattern of LED and pulsing through the pattern.

Circuit:
In either of the following circuits, you can use 4 or 8 LEDs. The circuit is the same, just the number of LEDs and the pins used are different. Use Resistance value of 220 ohm for each LED.
To use with 4 LEDs, use the following circuit:
![Lab 6 Task 2 Circuit in breadboard with 4 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-6/CSE-06133118-322-2501-lab6-task-1-2-variant1CKT_bb.png)

To use with 8 LEDs, use the following circuit:
![Lab 6 Task 2 Circuit in breadboard with 8 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-6/CSE-06133118-322-2501-lab6-task-1-2-variant2CKT_bb.png)

Code:
```c
#include<EEPROM.h>

const int ledPins[8]={A0,A1,A2,A3,A4,A5,2,3};
//byte ledStates[8]={1,2,4,8,16,32,64,128}; 
// byte ledStates[8]={1,3,7,15,31,63,127,255}; 
/*
new Pattern
00000001
00000011
00000111
00001111
00011111
00111111
01111111
11111111
*/
byte ledStates[8]={1,3,7,15,7,3,1,0}; 

void setup() {

  Serial.begin(115200);

  for(int i=0;i<8;i++)
  {
    pinMode(ledPins[i],OUTPUT);
  }
  // EEPROM.write(0,1); //00000001 =>1
  // EEPROM.write(1,2); //00000010 =>2
  // EEPROM.write(2,4); //00000100 =>4
  // EEPROM.write(3,8); //00001000 =>8
  // EEPROM.write(4,16); //00010000 =>16
  // EEPROM.write(5,32); //00100000 =>32
  // EEPROM.write(6,64); //01000000 =>64
  // EEPROM.write(7,128); //10000000 =>128

  //sizeof(ledStates)/sizeof(ledStates[0])

  for(int i=0;i<8;i++)
  {
    EEPROM.write(i,ledStates[i]);
  }


}

void loop() {
  // Nothing
  for (int i=0;i<8;i++)
  {
    byte value=EEPROM.read(i);
    displayByteOnLED(value);
    Serial.println(value);
    delay(1000);
  } 
  
}


void displayByteOnLED(byte value)
{
  for(int i=0;i<8;i++)
  {
    digitalWrite(ledPins[i],value>>i & 1);
  }
}

```

## Task 3
Create a function to output PWM with a specified duty cycle to any given pin. eg: pwm(pinName, dutyCycle);.

Circuit:
![Lab 6 Task 3 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-6/CSE-06133118-322-2501-lab6-task-3CKT_bb.png)

Code:
```c
int pwmPin=7;

void setup() {
  pinMode(pwmPin, OUTPUT);

}

void loop() {
  // put your main code here, to run repeatedly:
  pwm(pwmPin,20);
}

void pwm(int pin, int duty)
{
  int t_on=5;
  float x=((t_on*100)/duty)-t_on;
  int t_off=(int)x;
  digitalWrite(pin, HIGH);
  delay(t_on);
  digitalWrite(pin, LOW);
  delay(t_off);  
}
```

## Task 4
PWM using analogWrite() function.
This task is to use the `analogWrite()` function to output PWM signals. The `analogWrite()` function takes two parameters: the pin number and the duty cycle (0-255).

Circuit:
![Lab 6 Task 4 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-6/CSE-06133118-322-2501-lab6-task-4-5CKT_bb.png)

Code:
```c
int pwmPin=6;

void setup() {
  pinMode(pwmPin, OUTPUT);

}

void loop() {
  analogWrite(pwmPin,127);
  delay(1000);
  
  analogWrite(pwmPin,255);
  delay(1000);

  analogWrite(pwmPin,0);
  delay(1000);
}
  
```

## Task 5
Use `analogWrite()` to create a fading LED effect.
This task is to use the `analogWrite()` along with `map()` function to output PWM signals by providing duty cycle as percentage. 

Circuit:
![Lab 6 Task 5 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-6/CSE-06133118-322-2501-lab6-task-4-5CKT_bb.png)

Code:
```c
int pwmPin=6;

void setup() {
  pinMode(pwmPin, OUTPUT);

}

void loop() {  
  for(int i=0;i<11;i++)
  {
    analogWrite(pwmPin,map(i*10,0,100,0,255));
    delay(1000);
  }
}
    
```



## [Watch Class video Here](https://www.youtube.com/watch?v=FBq0LM6HCyM)
