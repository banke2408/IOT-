#include <Servo.h>

Servo myServo;

int trigPin = 10;
int echoPin = 11;

long duration;
int distance;

void setup() {
  Serial.begin(9600);
  myServo.attach(9);

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop() {

  // 0 to 180
  for (int i = 0; i <= 180; i++) {
    myServo.write(i);
    delay(40);

    distance = getDistance();

    Serial.print(i);        // angle
    Serial.print(",");
    Serial.print(distance); // distance
    Serial.print(".");
  }

  // 180 to 0
  for (int i = 180; i >= 0; i--) {
    myServo.write(i);
    delay(40);

    distance = getDistance();

    Serial.print(i);
    Serial.print(",");
    Serial.print(distance);
    Serial.print(".");
  }
}

int getDistance() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  int dist = duration * 0.034 / 2; // distance in cm
  return dist;
}
