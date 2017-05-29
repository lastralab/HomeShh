# HomeShh
*Smart Home for people with audition disabilities.*
<br><br>
**Coursera:** <a href="https://www.coursera.org/learn/internet-of-things-project/home/welcome"><b>Programming for the Internet of Things Capstone Project </b>by University of California, Irvine</a>.
<br>
# Documentation

**Background**

My idea began when I was hearing a lot of noise in my home.  Cars outside, neighbors moving furniture, dishes noise, the old fridge complaining, neighbors' kids crying, etc.  I needed to concentrate on something that day, so it was really bothering me.  And then, I started to imagine how is it to be deaf.  It seemed like a wonderful thing to me until I started to think in how would I be aware of the noises that are really important, like the door bell, the phone, things that I am used to hearing and that make me feel in control, somehow, of my time.  The microwave, the washing machine... And things that can save me from dying, like the fire alarm or the burglar alarm.  What if I am far away from my phone and someone is calling for an emergency to my house? What if my family needs me in the middle of the night and they are outside, but my phone is off and I can’t hear them? Then I got it.

If I were deaf I would like to have confidence when it comes to being aware of important sounds.  And I also wouldn’t like to have other things to worry about, so I imagined my house rigged with lightbulbs that change colors when something happens.  If I were to take a shower or my phone is not nearby, I would still know if something important were to happen.

I did some research and started to read forums for deaf people.  I found a lot of devices that are already in the market and they are pretty effective but also pretty expensive.  After encountering with a few situations where deaf people were complaining about devices that are built for them, but designed by hearing people, I used a community platform to ask them what would they want out of devices to fully satisfy their needs.  I received negative answers like “There are good things already invented” or “You should improve the Heads Up Display (HUD) that already exists” … so the post didn’t go through my expectations.  I searched for other forums where similar questions were asked and I found more useful answers, like: “I’ve used strobes to notify me when the phone was ringing while I was sleeping… it gave me headaches, so I use a fan now and it works better for me”.  After this, I realized it would be helpful to develop an embedded system that could be implemented economically and with the least inconvenience for most people with audition disabilities.

**Purpose**

Improve the quality of life of people with audition disabilities.  The desired end result is to provide an alternative way of being alarmed from the surrounding signals that are often designed for hearing people.

**Objectives**

-	Provide the user an alternative way to be notified by important alarms.
-	Provide a reliable and effective alternative alarm system.
-	Create a design that will serve as a platform that can be modified for diverse users with different needs.
-	Create an economical design with minimal financial cost.

**Scope**

While this project is intended to use economical components, it is crucial to select the best ones for stability and optimal performance, given changes in indoor temperature and humidity, and outdoor weather.

The clients targeted by this project represent a small portion of the global population. For instance, approximately 15% of adults in the U.S.A. (37.5 million) aged 18 and over report some trouble hearing.   This project is intended for adults with trouble hearing, who live alone and require assistance from an alternative alarm system. However, the alarm system presented in this project may also be used by hearing people who just do not like the noisy alarms in their homes.

**Deliverables**

The system will work once the installation of the sensors and lightbulbs is finished.  The sensors must be connected to each alarm device (phone, doorbell, security alarm, etc.) in order to send the right signals to the microcontroller.  The lightbulbs are wireless- controlled (Bluetooth), so lightbulbs around the house need to be replaced.  Once the alarm devices are identified, they may be connected to the microcontroller via wires, and the microcontroller placed in a convenient location. The whole process may take a maximum of four hours.

**Constraints**

The type of house may be crucial to determine time spent installing the system.  The house may contain its own alarm devices, or may be a building with other apartments involved, which might require different installation procedures.  The installation process may take one hour, or perhaps more, but the maximum deliverable time should not be more than four hours.

**Assumptions**

The *HomeShh* embedded system will be installed in a single home that already has a security system, a doorbell, a phone and electricity installed.  

# Preview

<img width="100%" alt="First Prototype" src="https://cloud.githubusercontent.com/assets/22894897/26525301/2dda1adc-432a-11e7-9246-1a05bf70bf40.png"/>

# First test

```C++
//  _ ___ _______     ___ ___ ___  ___ _   _ ___ _____ ___ 
// / |_  )__ /   \   / __|_ _| _ \/ __| | | |_ _|_   _/ __| 
// | |/ / |_ \ |) | | (__ | ||   / (__| |_| || |  | | \__ \ 
// |_/___|___/___/   \___|___|_|_\\___|\___/|___| |_| |___/ 
//
// HomeShh - Capstone Project - Test 1
// Main Arduino Uno
// by Tania Molina©

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
    Cian();
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
# Demo 
- Yellow color means the light is ON but nothing is happening.<br>
- Cyan color means a phone-call is happening.<br>
- Red color is for Fire Alarm.<br>
<br>
<img width="100%" src="https://cloud.githubusercontent.com/assets/22894897/26525177/91887b0a-4325-11e7-9661-8c53bfa49b90.gif"/>
**©L'Astra Lab**.
