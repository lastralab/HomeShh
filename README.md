# HomeShh
*Smart Home for people with audition disabilities.*
<br>
For a simulation video click <a href="https://www.youtube.com/watch?v=kOvg-w_Msgw">here</a>. <br>
<img width="40%" alt="screenshot 2017-06-02 13 31 13" src="https://cloud.githubusercontent.com/assets/22894897/26735392/359a385c-4798-11e7-8b29-aaf75361bb56.png"><br>
<br>
# Introduction

**Background**

The idea began when I was hearing a lot of noise in my home.  Cars and motorcycles outside, neighbors moving furniture, dishes noise, the old fridge complaining, kids crying, etc.  I needed to concentrate on something that day, so the noises were really bothering me.  And then, I started to imagine how is it to be deaf.  It seemed like a wonderful thing to me until I started to think in how would I be aware of the noises that are really important, like the door bell, the phone... Or things that can save me from dying, like the fire alarm or the burglar alarm.  If I were deaf I would like to have confidence when it comes to being aware of important sounds.  And I also wouldn’t like to have other things to worry about (smartphone battery dead, hackers messing with the system, stolen smarthphone, etc.), so I imagined my house rigged with lightbulbs that change colors when something happens.  If I were to take a shower or my cellphone is not nearby, I would still know if something important were to happen.

I did some research and started to read forums for deaf people.  I found a lot of devices that are already in the market and they are pretty effective but also pretty expensive.  After encountering with a few situations where deaf people were complaining about devices that are built for them, but designed by hearing people, I used a community platform to ask them what would they want out of devices to fully satisfy their needs.  I received negative answers like “There are good things already invented” or “You should improve the Heads Up Display (HUD) that already exists” … so the post didn’t go through my expectations.  I searched for other forums where similar questions were asked and I found more useful answers, like: “I’ve used strobes to notify me when the phone was ringing while I was sleeping… it gave me headaches, so I use a fan now and it works better for me”.  After this, I realized it would be helpful to develop an embedded system that could be implemented economically and with the least inconvenience for most people with audition disabilities.

**Purpose**

The desired end result is to provide an alternative way of being alarmed from the surrounding signals that are often designed for hearing people. And also, to avoid external threats (hackers) by making it offline and autonomous (without the intervention of a smart device that can also be hacked/lost/stolen).

**Objectives**

-	Provide a reliable and effective alternative alarm system (not connected to any kind of network).
-	Create a design that will serve as a platform that can be modified for diverse users with different needs.
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
**Simulation:**<br>
<br>
https://www.tinkercad.com/things/afNAJcOk2rS-sim-zatknis-dom-/editel?sharecode=b4-hxomIlO_lSzW6PpGuVMrkRsW0HRKllROT_KIAYx4=
<br>
<br>
<img width="100%" alt="huge gif" src="https://user-images.githubusercontent.com/22894897/27100226-b2c14d34-5053-11e7-862c-7d18bc519132.gif"/> 
<br>
<br>
<p align="center"><a href="https://lastralab.github.io/website/" target="_blank"><br><button><img src="http://i.imgur.com/ERyS5Xn.png" alt="l'astra lab icon" width="50px" background="transparent" opacity="0.5" padding="0;"/></button></a></p><br><br>
