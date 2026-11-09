Learning Log Entry 3: 27.10.2026

Notes:

* getting deeper into analog signals and PWM to control component behavior
* explored how to use serial communication to monitor readings and send inputs
* interesting to see how different sensors like tilt switches, potentiometers, and photoresistors work with digital and analog pins

What we did:

* learned about PWM (Pulse-Width Modulation) and duty cycles for dimming LEDs and controlling power
* explored the Arduino UNO pin layout (digital I/O, analog inputs, power, and serial TX/RX pins)
* used an oscilloscope to visualize signals graphically
* worked with a tilt switch using digitalRead() and compared INPUT vs. INPUT_PULLUP
* used a potentiometer on an analog pin (analogRead()), mapped the values using map(), and printed readings to the Serial Monitor and Serial Plotter
* explored voltage dividers and how adjustable resistors work
* read input data from the Serial monitor using Serial.readString() and Serial.parseInt()
* connected a photoresistor (LDR) with a 10k resistor to measure light intensity and trigger an LED

What I have learned:

* PWM uses rapid switching on and off to simulate analog power (0–255 scale)
* internal pull-up resistors (INPUT_PULLUP) prevent floating pins and unstable values without needing external resistors
* analogRead() returns a 10-bit value between 0 and 1023 (0V to 5V)
* how to use the map() function to convert sensor ranges (e.g., 0–1023 to 0–255 for PWM)
* photoresistors decrease in resistance as light intensity increases

The code we used for fading an LED using PWM and for reading an LDR:

```cpp
/*
Fading LED
*/
int ledPin = 5;    // LED needs to be connected to a PWM pin

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // fade in from min to max in increments of 5 points:
  for (int fadeValue = 0 ; fadeValue <= 255; fadeValue += 5) {
    analogWrite(ledPin, fadeValue);
    delay(30);
  }

  // fade out from max to min in increments of 5 points:
  for (int fadeValue = 255 ; fadeValue >= 0; fadeValue -= 5) {
    analogWrite(ledPin, fadeValue);
    delay(30);
  }
}

/*
Use LDR to control an LED
*/
int readingValue = 0;
const int ledPin = 2;

void setup() {
  Serial.begin(9600); 
  pinMode(A0, INPUT); // LDR is connected to A0
  pinMode(ledPin, OUTPUT);
}

void loop() {
  readingValue = analogRead(A0);
  Serial.println(readingValue);
  if (readingValue < 500) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }
}
