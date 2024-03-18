# Autonomous-Car-Design-1


# sonar0315

#define SONIC_TRIG 2
#define SONIC_ECHO 3

void setup() {
Serial.begin(9600);

```cpp
pinMode(SONIC_TRIG, OUTPUT);
pinMode(SONIC_ECHO, INPUT);

```

}

void loop() {
digitalWrite(SONIC_TRIG, HIGH);
delayMicroseconds(10);
digitalWrite(SONIC_TRIG, LOW);

```cpp
unsigned long duration = pulseIn(SONIC_ECHO, HIGH);
unsigned long distance = duration / 58;
Serial.print(duration);
Serial.print(",");
Serial.println(distance);
Serial.println("cm");

delay(25);

```

}

# sonar0318

#include <NewPing.h>

#define TRIGGER_PIN  3  // Arduino pin tied to trigger pin on the ultrasonic sensor.
#define ECHO_PIN     2  // Arduino pin tied to echo pin on the ultrasonic sensor.
#define MAX_DISTANCE 100 // Maximum distance we want to ping for (in centimeters). Maximum sensor distance is rated at 400-500cm.

NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE); // NewPing setup of pins and maximum distance.

void setup() {
  Serial.begin(115200); // Open serial monitor at 115200 baud to see ping results.
}

void loop() {
  float distance = 0.0;
  delay(50);         // Wait 50ms between pings (about 20 pings/sec). 29ms should be the shortest delay between pings.
  distance == sonar.ping_cm();
  if(distance ==0) distance = MAX_DISTANCE;
  Serial.print("Ping: ");
  Serial.print(sonar.ping_cm()); // Send ping, get distance in cm and print result (0 = outside set distance range)
  Serial.println("cm");
}
