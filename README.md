//We are going to need 6 LED's and here you define in witch pin are connected
int LED = 10;
int LED1 = 12;
int LED2 = 2;
int LED3 = 3;
int LED4 = 4;
int LED5 = 5;

//Create servo object motor to control a servo
#include <Servo.h>
Servo myservo1;
Servo myservo2;

void setup() {

  pinMode (LED, OUTPUT);
  pinMode (LED1, OUTPUT);
  pinMode (LED2, OUTPUT);
  pinMode (LED3, OUTPUT);
  pinMode (LED4, OUTPUT);
  pinMode (LED5, OUTPUT);

  //Analog pin for the photoresistor
  pinMode (A0, INPUT);

  Serial.begin(9600);

  //Ateches the servos to the pins to the servo motors
  myservo1.attach (9);
  myservo2.attach (6);
}

void loop() {
  digitalWrite(LED, HIGH);

  //Here you can detect the value of the sensor (photoresistor)
  int sensorValue = analogRead (A0);
  Serial.print (sensorValue);
  delay (1);

  //If the value of the photoresistor is les than 250 will happen the following things
  if (sensorValue <= 30) {

    // Sart moving the motors and set the positions to the declared value
    myservo1.write(0);
    delay(100);
    myservo2.write(70);
    delay(500);
    myservo2.write(110);
    delay(100);

    // Turns the led on and off
    digitalWrite(LED1, HIGH);
    digitalWrite(LED2, HIGH);
    digitalWrite(LED3, HIGH);
    digitalWrite(LED4, HIGH);
    digitalWrite(LED5, HIGH);
    delay (500);
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, LOW);
    digitalWrite(LED5, LOW);
    delay (500);

    //Because we whant to se the LED's we close the top at the end
    myservo1.write(90);
    delay(500);
  }
}
