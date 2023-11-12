// Constants
const int echoPin = 2;    // Ultrasonic sensor echo pin
const int trigPin = 3;    // Ultrasonic sensor trigger pin
const int redPin = 4;     // Red LED pin
const int greenPin = 5;   // Green LED pin
const int yellowPin = 6;  // Yellow LED pin

// Variables
long duration;
int distance;

void setup() {
  // Initialize serial communication
  Serial.begin(9600);

  // Set pin modes
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
}

void loop() {
  // Trigger ultrasonic sensor
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Measure the distance
  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  // Print distance to serial monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  // Traffic signal control based on distance
  if (distance < 50) {
    // Red light ON, others OFF
    digitalWrite(redPin, HIGH);
    digitalWrite(greenPin, LOW);
    digitalWrite(yellowPin, LOW);
  } else if (distance >= 50 && distance < 100) {
    // Yellow light ON, others OFF
    digitalWrite(redPin, LOW);
    digitalWrite(greenPin, LOW);
    digitalWrite(yellowPin, HIGH);
  } else {
    // Green light ON, others OFF
    digitalWrite(redPin, LOW);
    digitalWrite(greenPin, HIGH);
    digitalWrite(yellowPin, LOW);
  }

  // Delay before next measurement
  delay(1000);
}
