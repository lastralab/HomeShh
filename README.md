# HomeShh

**Capstone**: Programming for the Internet of Things: *Smart Home for people with audition disabilities.*

## Documentation coming soon...

I'm still working on it.

<img width="100%" alt="screenshot 2017-05-27 15 18 06" src="https://cloud.githubusercontent.com/assets/22894897/26523522/c1d1fb8c-42ef-11e7-9005-6860891108f8.png">

First test:

```C++
// HomeShh - Capstone Project
// by Tania Molina.
// All rights reserved.

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
void Cian() {
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
# DEMO:<br>
-Yellow color means the light is ON but nothing is happening.<br>
-Cian color means a phone-call is happening.<br>
-Red color is for Fire Alarm.<br>

<img width="100%" src="https://cloud.githubusercontent.com/assets/22894897/26525064/70a900ac-4321-11e7-8ad8-68f91556237c.gif"/>
