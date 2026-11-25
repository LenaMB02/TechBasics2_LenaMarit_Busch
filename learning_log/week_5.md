# Learning Log Entry 5: 10.11.2026

## Notes:

* this week we moved from light and sound to actual movement with motors
* it was interesting to see how servo motors work and how they can be used for robotic arms or moving objects
* connecting the potentiometer and joystick to control the movement felt very intuitive once the wiring worked

---

## What we did:

* looked at different motor types (Servo, Stepper, DC motors) and the inside of a micro servo
* talked about the difference between positional servos (0–180°) and continuous servos (360°)
* connected a servo motor to the Arduino and controlled its angle
* tested how to change the speed of the servo movement
* used a potentiometer with `analogRead()` and `map()` to control the servo position
* read values from a joystick (X-axis, Y-axis, and button with `INPUT_PULLUP`) in the Serial Monitor
* combined two servos with the joystick to control movement in two directions

---

## What I have learned:

* positional servos move to a specific angle (0–180°), while continuous servos spin 360° and the signal controls speed
* `#include <Servo.h>`, `myservo.attach()`, and `myservo.write()` make controlling a servo really straightforward
* `map()` converts the analog input (0–1023) into angles (0–180) that the servo understands
* a joystick works basically like two potentiometers (for X and Y) plus a push button

---

## A code we used for controlling the servo:

```cpp
#include <Servo.h>

Servo myservo;

void setup() {
  myservo.attach(9);
}

void loop() {
  myservo.write(0);
  delay(2000);
  myservo.write(180);
  delay(2000);
}
