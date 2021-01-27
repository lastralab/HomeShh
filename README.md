# HomeShh
*Smart Home for people with different audition capabilities/preferences.*
<br>
<br>
<img width="40%" alt="screenshot 2017-06-02 13 31 13" src="https://cloud.githubusercontent.com/assets/22894897/26735392/359a385c-4798-11e7-8b29-aaf75361bb56.png"><br>
<br>
# Introduction

**Purpose**

The desired end result is to provide an alternative way of being alarmed from the surrounding signals that are often designed for hearing people. And also, to avoid external threats (hackers) by making it offline and autonomous (without the intervention of a smart device that can also be hacked/lost/stolen).

**Objectives**

-	Provide a reliable and effective alternative alarm system (not connected to any kind of network).
-	Create a design that will serve as a platform that can be flexible for diverse users with different needs.
-	Create an economical design with minimal financial cost.

**Scope**

The clients targeted by this project represent a small portion of the global population. For instance, approximately 15% of adults in the U.S.A. (37.5 million) aged 18 and over report some trouble hearing (<a href="https://www.cdc.gov/nchs/data/series/sr_10/sr10_260.pdf" target="_blank">Source</a>).  This project is intended for adults with trouble hearing, who live alone and require assistance from an alternative alarm system. However, the alarm system presented in this project may also be used by hearing people who just do not like the noisy alarms in their homes.

**Deliverables**

The system will work once the installation of the sensors and lights is finished.  The sensors must be connected to each alarm device (phone, doorbell, security alarm, etc.) in order to send the right signals to the microcontroller.  The RGB lights will be placed in each room of the house and the energy will be supplied by a light socket adapter.  Once the alarm devices are identified, they may be connected to the microcontroller via wires, and the microcontroller placed in a convenient location. The whole process may take a maximum of six hours.

**Assumptions**

The *HomeShh* embedded system will be installed in a single home that already has a security system, a doorbell, a <a href="https://en.wikipedia.org/wiki/Telecommunications_device_for_the_deaf" target="_blank">textphone</a>(TTY or TDD) and electricity installed.  

# Demo 
- Yellow color means the light is ON but nothing is happening.<br>
- Cyan color means a textphone-call is happening.<br>
- Red color is for Fire Alarm.<br>
<br>
<img width="100%" src="https://cloud.githubusercontent.com/assets/22894897/26525177/91887b0a-4325-11e7-9661-8c53bfa49b90.gif"/>

**Code for Demo**

```C++
//  _ ___ _______     ___ ___ ___  ___ _   _ ___ _____ ___ 
// / |_  )__ /   \   / __|_ _| _ \/ __| | | |_ _|_   _/ __| 
// | |/ / |_ \ |) | | (__ | ||   / (__| |_| || |  | | \__ \ 
// |_/___|___/___/   \___|___|_|_\\___|\___/|___| |_| |___/ 
//
// HomeShh - Capstone Project - Test 1
// Main Arduino Uno
// Author: Niam Moltta
// © L'Astra Lab

const int G =12;
const int B =11;
const int R =13;
const int S = 7;
const int T = 6;
const int V = A0;
const int Y = A3;
const int W = A1;
int s = 0;
int c = 0;
int ms = 0;
void setup() 
{
  pinMode(G, OUTPUT); 
  pinMode(B, OUTPUT); 
  pinMode(R, OUTPUT); 
  pinMode(S, OUTPUT); 
  pinMode(T, OUTPUT);
  Serial.begin(9600);
  pinMode(Y, INPUT); 
  pinMode(V, INPUT); 
  Nothing();
}
void loop() {
  s = analogRead(V);
  Serial.println("Signal");
  Serial.println(s);
  if ((s > 400) && (s < 800)) {
    Red();
    tone(T, 1000);
    delay(500);
  }
  else {
    noTone(T);
    Nothing();
  }
  ms = analogRead(W);
  Serial.println("Signal");
  Serial.println(ms);
  if ((ms > 400) && (ms < 800)) {
    Red();
    tone(T, 1000);
    delay(500);
  }
  else {
    noTone(T);
    Nothing();
  }
  c = analogRead(Y);
  Serial.println("Signal");
  Serial.println(c);
  if (c < 10) {
    Cyan();
    tone(S, 700);
    delay(500);
  }
  else {
    noTone(S);
    Nothing();
  }
}
void Red() { 
  digitalWrite(R, HIGH);
  digitalWrite(B, LOW);
  digitalWrite(G, LOW);
}
void Cyan() {
  digitalWrite(R, LOW);
  digitalWrite(B, HIGH);
  digitalWrite(G, HIGH);
}
void Nothing() {
  digitalWrite(R, HIGH);
  digitalWrite(G, HIGH);
  digitalWrite(B, LOW);
}
```
# Final Test

**Color table:**<br>
<img width="280" alt="color table" src="https://user-images.githubusercontent.com/22894897/27101869-b2829c1e-5059-11e7-849c-03c6c271d4d4.png"/>
<br>
<img width="100%" alt="image house labeled" src="https://user-images.githubusercontent.com/22894897/27061461-7c017cd6-4fba-11e7-8401-6c9a3f4c1e57.png"/>
<br>

