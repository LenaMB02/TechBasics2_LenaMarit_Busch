### **Learning Log Entry 1: 13.10.2026**

## Notes:
- I did not have my own kit yet, I borrowed one for the lesson
- ordered it on Amazon after it was in stock again
- it was pretty interesting, but also challenging to get into the first functions of the kit

## What we did:
- introduction to the topic of physical computing
- introduction to the syllabus (course plan with dates)
- starting with Arduino UNO
- developed a code to make the lamp blink (variety of delays to make it blink faster or slower)

## What I have learned:
- how Arduino UNO works
- how to make the right connections and write the right code to make the light blink
- advantages of a microcontroller (low-cost, single chip, self-contained computer system)
- microcontrollers are invisible computers inside drones e.g.
- void = function does not return anything
- loop -> constantly on/off = less brighter light (how we mimic it in a digital sense)
- changing the delay to make it blink slower so you can actually see it blinking bright

## The code we used for the blinking:

```cpp
void setup() {
  // put your setup code here, to run once:
  pinMode(13, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(13, LOW); // 0 - 0v, off
  delay(1000); // 1 second

  digitalWrite(13, HIGH); // 1 - 5v, on
  delay(1000);
}
```
