
# 💡 The Idea

---

Η ιδέα του project είναι να δημιουργηθεί ένα ρομπότ κατοικίδιο που θα είναι ικανό να εκτελεί βασικές κινήσεις και να αλληλεπιδρά με το περιβάλλον. Θα βασίζεται σε ένα σύστημα ελέγχου με Arduino και θα χρησιμοποιεί αισθητήρες για να αντιλαμβάνεται το περιβάλλον του. Το ρομπότ θα είναι σε θέση να περπατάει.

![Prototype](https://github.com/Hlektronikoi/Zoaki/blob/main/Zoaki.gif)

# 🎥 Video

---

https://youtu.be/mbPmRKQrVss

# 📃 Materials

---



[1 Arduino uno compatible board](https://grobotronics.com/uno-compatible.html?gad_source=1&gclid=EAIaIQobChMI6fuZ1smaiwMVs8pEBx3dgQjOEAQYAiABEgLBUvD_BwE)

[8 μοτέρ MG90 για τις αρθρώσεις των ποδιών](https://grobotronics.com/servo-micro-2.8kg.cm-metal-gears-waveshare-mg90s.html)

[1 Waveshare LCD 1602 I2C](https://grobotronics.com/basic-16x2-character-lcd-rgb-3.3v-5v-i2c-protocol.html)

[4 packs jumper wires 15cm male to male](https://grobotronics.com/jumper-wires-15cm-male-to-male-pack-of-10.html)

[1 breadboard mini-black](https://grobotronics.com/breadboard-170-black.html?sl=en&srsltid=AfmBOornSqBo8LKOGWfVglvk-940Ss4kUXreP7u82EMMZgPjaDN9tIbk)

[1 Ultrasonic Sensor - Ranging Detector 2 - 400cm HC-SR04](https://grobotronics.com/ultrasonic-sensor-sr04.html?sl=en&srsltid=AfmBOooFlvRa-6Qu0Zk_XPp4RR_WE78Am6l__Cy5Fub8jk7ckyLn6PN8)

# 💻 Code Language

---

<picture>
  <img alt="Arduino" src="https://img.shields.io/badge/-Arduino-00979D?style=for-the-badge&logo=Arduino&logoColor=white">
</picture>

[![](https://visitcount.itsvg.in/api?id=Hlektronikoi&icon=0&color=0)](https://visitcount.itsvg.in)

```
#include <Servo.h>

//Pins for all
const int trigPin = 10;   // Trigger pin
const int echoPin = 11;  // Echo pin

//Servo legs names

Servo leg1;  // create servo object to control a servo
Servo leg2;  // create servo object to control a servo
Servo leg3;  // create servo object to control a servo
Servo leg4;  // create servo object to control a servo

Servo knee1;  // create servo object to control a servo
Servo knee2;  // create servo object to control a servo
Servo knee3;  // create servo object to control a servo
Servo knee4;  // create servo object to control a servo


void setup() {
  Serial.begin(9600);
  leg1.attach(5, 600, 2300);
  leg2.attach(2, 600, 2300);
  leg3.attach(7, 600, 2300);
  leg4.attach(4, 600, 2300);

  knee1.attach(6, 600, 2300);
  knee2.attach(9, 600, 2300);
  knee3.attach(8, 600, 2300);
  knee4.attach(3, 600, 2300);

  leg1.write(125);
  leg2.write(65);
  leg3.write(125);
  leg4.write(65);

  knee1.write(140);
  knee2.write(40);
  knee3.write(150);
  knee4.write(40);

  Serial.begin(9600);     // Start serial communication
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

 
}

void Sensor() 
{

  delay(100); // Wait before next measurement

}

void loop() { 

  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Measure the echo pulse duration in microseconds
  long duration = pulseIn(echoPin, HIGH);

  // Calculate distance (in cm)
  float distance = duration * 0.0343 / 2; // Speed of sound = 0.0343 cm/μs

  // Display results
  if (duration == 0) {
    Serial.println("Out of range!");
  } else {
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" cm");
  }

   delay(100);

  if (distance > 1 && distance <= 5) {
  leg3.write(70);
  leg4.write(120);
  knee3.write(130);
  knee4.write(40);
  leg1.write(70);
  leg2.write(120);
  knee1.write(130);
  knee2.write(40);
  

}

  if (distance > 6 && distance <= 15) {
  leg3.write(70);
  leg4.write(120);
  knee3.write(130);
  knee4.write(40);
  delay(100);
  knee1.write(40);
  knee2.write(120);
  delay(20);
  knee1.write(140);
  knee2.write(70);
  delay(20);
  knee1.write(40);
  knee2.write(120);
  delay(20);
  knee1.write(140);
  knee2.write(70);
  delay(20);
  knee1.write(40);
  knee2.write(120);
  delay(20);
  knee1.write(140);
  knee2.write(70);
  }


/* if (distance > 16 && distance <= 50) {


    knee1.write(145);
  delay(20);
  leg1.write(100);
  delay(20);
  knee1.write(160);
  delay(300);

  knee4.write(0);
  delay(20);
  leg4.write(80);
  delay(20);
  knee4.write(20);
  delay(300);


  knee2.write(0);
  delay(20);
  leg2.write(80);
  delay(20);
  knee2.write(20);
  delay(300);

  knee3.write(145);
  delay(20);
  leg3.write(100);
  delay(20);
  knee3.write(170);
  delay(500);

  knee1.write(180);
  knee2.write(50);
  knee3.write(140);
  knee4.write(50);

  leg1.write(135);
  leg2.write(55);
  leg3.write(135);
  leg4.write(55);

  
  delay(500); 
} */

if (distance > 51){


  leg1.write(135);
  leg2.write(55);
  leg3.write(135);
  leg4.write(55);

  knee1.write(160);
  knee2.write(20);
  knee3.write(140);
  knee4.write(10);
}
}
```
