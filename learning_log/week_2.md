### **Learning Log Entry 2: 20.10.2026**

## Notes:
- finally got my own kit and unpacked everything -> noticed it is too small, ordered the right one and sent the wrong one back
- starting to get more comfortable with breadboards and circuits
- combining multiple LEDs and understanding how resistors work was interesting

## What we did:
- introduction to the kit (differences between the pieces)
- explanation of the colour stripes (orange, orange, black, black, brown) -> Resistors
- looked at DC (Direct Current) vs. AC (Alternating Current)
- learned about Ohm's Law and why we need resistors to protect LEDs
- explored series and parallel circuits on the breadboard
- built a traffic light exercise (connecting red, yellow, and green LEDs to pins 2, 3, and 4)
- worked with RGB LEDs (Common Cathode) and wrote a custom function for the color mix

## What I have learned:
- never directly connect `+` and `-` to avoid a short circuit
- why the green LED looks a bit dimmer (different forward voltage compared to red/yellow)
- to make the green light brighter, you have to change the resistor (to a smaller value for the green, to make it slightly more even compared to the other colours)
- how to define pins as variables (`const int redLED = 2;`) to keep the code clean
- basics of using `analogWrite()` for controlling brightness and colors in functions


## The code we used for the simple circuit driving three LEDs (Red, Yellow, Green) on different pins
```cpp

// Define the pins for the LEDs
const int redLED = 2;
const int yellowLED = 3;
const int greenLED = 4;

void setup() {
  // Initialize the LED pins as outputs
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}

void loop() {
  // Turn all LEDs on simultaneously
  digitalWrite(redLED, HIGH);
  digitalWrite(yellowLED, HIGH);
  digitalWrite(greenLED, HIGH);
  delay(1000); // Wait for 1 second

  // Turn all LEDs off
  digitalWrite(redLED, LOW);
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, LOW);
  delay(1000); // Wait for 1 second

  // Turn LEDs on in sequence
  digitalWrite(redLED, HIGH);
  delay(500); // Wait for 0.5 seconds
  digitalWrite(redLED, LOW);

  digitalWrite(yellowLED, HIGH);
  delay(500); // Wait for 0.5 seconds
  digitalWrite(yellowLED, LOW);

  digitalWrite(greenLED, HIGH);
  delay(500); // Wait for 0.5 seconds
  digitalWrite(greenLED, LOW);

  delay(1000); // Wait for 1 second before repeating the sequence
}
