# Learning Log Entry 4: 03.11.2026

## Notes:

* moving from simple inputs and outputs to sound generation and distance measurement
* difference between active and passive components
* learning why pull-down and pull-up resistors are crucial for clean buttons

---

## What we did:

* explored different waveforms (sine, triangular, pulse, sawtooth, complex waves)
* worked with buzzers: distinguished between active buzzers (built-in oscillator) and passive buzzers (require frequency signals)
* played different frequencies using tone(pin, frequency, duration) and built a melody player using the pitches.h library
* discovered how to add volume control using external libraries
* connected an ultrasonic distance sensor (HC-SR04) to measure distances using sound waves and built a parking assistance/object avoidance warning system
* compared ultrasonic sensors with infrared (IR/PIR) sensors regarding range, speed, and application
* wired push buttons using external pull-down and pull-up resistors, as well as the internal pull-up shortcut (INPUT_PULLUP)
* built a small music instrument (combined the passive buzzer and multiple buttons)

---

## What I have learned:

* active buzzers make sound directly when powered, passive buzzers need precise frequency signals to play specific notes
* ultrasonic sensors use sound reflection for long ranges (up to 4m+) -> infrared sensors work over shorter ranges (up to ~80cm) and react to thermal radiation or surface reflectivity
* push buttons require pull-up or pull-down resistors to avoid floating signals and ensure stable HIGH or LOW states
* using INPUT_PULLUP is an easy way to connect a button without separately physical resistors

---

## The code we used for the ultrasonic distance sensor:

```cpp
/***
Ultrasonic distance sensor
***/

// Define the Trig and Echo pin connections
const int trigPin = 9;
const int echoPin = 10;
const int buzzerPin = 2;

// Define variables to store duration and distance
long duration; // for potentially large number
int distance;

void setup() {
  // Start the serial communication
  Serial.begin(9600);

  // Define the Trig and Echo pins as Output and Input
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzerPin, OUTPUT);
}

void loop() {
  // Clear the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  // Sets the trigPin HIGH for 10 microseconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);

  Serial.print("Duration ");
  Serial.print(duration);
  Serial.print(" microseconds | ");

  // Calculating the distance
  distance = duration * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)

  if (distance < 30) {
    digitalWrite(buzzerPin, HIGH);
  } else {
    digitalWrite(buzzerPin, LOW);
  }
  
  // Displays the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  // Delay 500 milliseconds before next measurement
  delay(500);
}
