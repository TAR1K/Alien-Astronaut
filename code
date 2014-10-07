
// ALIEN ASTRONAUT
// IR Proximity Sensor Code by Tarik El-Khateeb & Phuong Vu
// LED sequencing by Hart Reed & Tarik El-Khateeb

// and

// Sweep (for Servo)
// by BARRAGAN <http://barraganstudio.com>
// This example code is in the public domain.

#include <Servo.h>

Servo servoEyes;
int pos = 0;
int sensorPin = A0;
int servoPin = 9;
int ledPin = 2;
int sensorValue;
int timesMoved = 0;
boolean repeatMovement = false;


void setup() {
  pinMode(servoPin, OUTPUT);
  pinMode(sensorPin, INPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
  servoEyes.attach(9);
  servoEyes.write(0);
}

void loop() {
  sensorValue = analogRead(sensorPin);
  //Serial.println(sensorValue);
  if(sensorValue > 60) {
     repeatMovement = true;
  }
  if (repeatMovement) {
    moveEyes();
    //if(timesMoved==1)
    //{
      flashLights();
    //}else {
      //digitalWrite(ledPin, LOW);
    //}
  }
  delayMs(300);
}

void moveEyes() {
  for(pos = 0; pos < 70; pos += 1)  
  {                                  
    servoEyes.write(pos);             
    delayMs(30);                       
  }
  for(pos = 70; pos>=1; pos-=1)     
  {                                
    servoEyes.write(pos);              
    delayMs(30);                      
  }
  timesMoved++;
  Serial.println(timesMoved);
  if(timesMoved==2) {
    repeatMovement = false;
    timesMoved=0;
  }
}

void flashLights() {
  flicker();
  delayMs(60);
  flicker();
  delayMs(80);
  flicker();
  delayMs(80);
  flicker();
}

void delayMs(int time) {
  for (int i=0;i<time;i++)
  {
    delayMicroseconds(1000);
  }
}

void flicker() {
  int dly = 16383;
  Serial.println("Flash");
  digitalWrite(ledPin, HIGH);
  delayMicroseconds(dly);
  digitalWrite(ledPin, LOW);
  delayMicroseconds(dly);
  digitalWrite(ledPin, HIGH);
  delayMicroseconds(dly);
  digitalWrite(ledPin, LOW);
  delayMicroseconds(dly);
  digitalWrite(ledPin, HIGH);
  delayMicroseconds(dly);
  digitalWrite(ledPin, LOW);
  delayMicroseconds(dly);
}



