//#include <Servo.h>

//Servo myservo;  // create servo object to control a servo

// These numbers/pins (frontLPinFwd, trigPin, etc.) correspond to the DIGITAL pins of the Arduino. 

// Constant needed to convert to centimeters
#define CONVERT_TO_CM 29.1 



// FRONT MOTORS
int frontLPinFwd = 3;
int frontLPinRwd = 4;
int frontRPinFwd = 6;
int frontRPinRwd = 5;

// REAR MOTORS
int rearLPinFwd = 8;
int rearLPinRwd = 7;
int rearRPinFwd = 10;
int rearRPinRwd = 9;

// HCSR04 - Distance Sensor Pins
int trigPin = 11;
int echoPin = 12;
int LEDPin = 13;

// Math for trigger for the HCSR04
int duration = 0;
int cm = 0;

//int pos = 0

void setup() 
{  
  Serial.begin(9600); // Baud rate (change if you need to, should not need to)

  // Set the Arduino digital pins as outputs
  pinMode(frontLPinFwd, OUTPUT);
  pinMode(frontLPinRwd, OUTPUT);
  pinMode(frontRPinFwd, OUTPUT);
  pinMode(frontRPinRwd, OUTPUT);

  pinMode(rearLPinFwd, OUTPUT);
  pinMode(rearLPinRwd, OUTPUT);
  pinMode(rearRPinFwd, OUTPUT);
  pinMode(rearRPinRwd, OUTPUT); 

  pinMode(trigPin,  OUTPUT);
  pinMode(echoPin, INPUT); // input pin due to having to read the output from the HCSR04
  pinMode(LEDPin, OUTPUT);
}

// Deprecated, no need to use, may be helpful for reference later
// This is so that you can have multiple loops running in parallel
/*void forwardMovement(int motorSpeed, const long delayTime)
{
    static unsigned long lastTime = 0;
    const long interval = delayTime; // delay time
    static bool state;

    unsigned long now = millis();
  
    if(now - lastTime > interval && state == 0)
    {
      state = 1;
      lastTime = now;
      analogWrite(frontLPinFwd, motorSpeed);
      analogWrite(frontRPinFwd, motorSpeed);
      analogWrite(rearLPinFwd, motorSpeed);
      analogWrite(rearRPinFwd, motorSpeed); 
    }

    if(now - lastTime > interval && state == 1)
    {
      state = 0;
      lastTime = now;
      analogWrite(frontLPinFwd, 0);
      analogWrite(frontRPinFwd, 0);
      analogWrite(rearLPinFwd, 0);
      analogWrite(rearRPinFwd, 0);
    }  
}
*/



void loop() 
{

  // ** Demo Code //
  // Moves forward depending on the distance received from the HCSR04
  // ************************** //
  digitalWrite(trigPin, LOW);
  delayMicroseconds(5);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
      
  pinMode(echoPin, INPUT);
  duration = pulseIn(echoPin, HIGH);
  
  cm = (duration / 2) / CONVERT_TO_CM; // 
  if(cm > 5)
  {
    digitalWrite(LEDPin, HIGH); 
    analogWrite(frontLPinFwd, 255);
    analogWrite(frontRPinFwd, 255);
    analogWrite(rearLPinFwd, 255);
    analogWrite(rearRPinFwd, 255); 
  }
  else
  {
    delay(250);
    digitalWrite(LEDPin, LOW); 
    analogWrite(frontLPinFwd, 0);
    analogWrite(frontRPinFwd, 0);
    analogWrite(rearLPinFwd, 0);
    analogWrite(rearRPinFwd, 0); 
    delay(500);
  }
  
  delay(50);
  // ************************** //

  // SERVO CODE //
  /*
  for (pos = 0; pos <= 180; pos += 1) { // goes from 0 degrees to 180 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(1);                       // waits 15ms for the servo to reach the position
  }
  for (pos = 180; pos >= 0; pos -= 1) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(1);                       // waits 15ms for the servo to reach the position
  }
  */
    
}
