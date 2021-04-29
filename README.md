# Code-for-Arduino-Rover
//rover prototyp version
#define echoPin 3 // attach pin D3 Arduino to pin Echo of HC-SR04
#define trigPin 2 // attach pin D2 Arduino to pin Echo of HC-SR04
#define echoPin1 31//attach pin D31 Arduino to pin Echo of HC-SR04
#define trigPin1 33//attach pin D33 Arduino to pin Trig of HC-SR04
#define echoPin2 35//attach pin D35 Arduino to pin Echo of HC-SR04
#define trigPin2 37//attach pin D37 Arduino to pin Trig of HC-SR04
long duration1; // variable for the duration of sound wave travel
int distance1; // variable for the distance measurement
long duration2; // variable for the duration of sound wave travel
int distance2;
long duration; // variable for the duration of sound wave travel
int distance;
int count = 0;
int count2 =0;
int count3 = 0;
int countrechts = 0;
int countrechts2 = 0;
int countrechts3 = 0;
void vorwaerts(){
  while(count <= 1100){
  count = count + 1;
  digitalWrite(53, LOW);
  digitalWrite(42, LOW);
  digitalWrite(8, HIGH);
  digitalWrite(10, LOW);
  digitalWrite(6, HIGH);
  digitalWrite(4, LOW);
  digitalWrite(9, HIGH);
  digitalWrite(7, HIGH);
  digitalWrite(5, HIGH);
  digitalWrite(11, HIGH);
  delayMicroseconds(800);
  digitalWrite(9,LOW);
  digitalWrite(11, LOW);
  digitalWrite(5,LOW);
  digitalWrite(7,LOW);
  delayMicroseconds(800);
  }
  count = 0;
}
void rueckwaerts(){
  // Clears the trigPin condition
  digitalWrite(trigPin1, LOW);
  delayMicroseconds(2);
  // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
  digitalWrite(trigPin1, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin1, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration1 = pulseIn(echoPin1, HIGH);
  // Calculating the distance
  distance1 = duration1 * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)
  // Displays the distance on the Serial Monitor
  Serial.print("Distance1: ");
  Serial.print(distance1);
  Serial.println(" cm");
    // Clears the trigPin condition
  digitalWrite(trigPin2, LOW);
  delayMicroseconds(2);
  // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
  digitalWrite(trigPin2, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin2, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration2 = pulseIn(echoPin2, HIGH);
  // Calculating the distance
  distance2 = duration2 * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)
  // Displays the distance on the Serial Monitor
  Serial.print("Distance2: ");
  Serial.print(distance2);
  Serial.println(" cm");
  delay(1);
  //////////////////////////////Nach Links Drehen////////////////////////////////////////
  if(distance1 < distance2){                                                           //
  Serial.print("Dreh nach Links_");                                                    //
  while (count <= 1400){                                                               // 
  count = count + 1;                                                                   //
  digitalWrite(6, LOW);                                                                //
  digitalWrite(4, LOW);                                                                //
  digitalWrite(7, HIGH);                                                               //   
  digitalWrite(5, HIGH);                                                               //
  delay(1);                                                                            //
  digitalWrite(5, LOW);                                                                // 
  digitalWrite(7, LOW);                                                                //
  delay(1);                                                                            //    
  }                                                                                    //
  while (count2 <= 3000){                                                              //
  count2 = count2+1;                                                                   //  
  digitalWrite(53, HIGH);                                                              //
  digitalWrite(4, LOW);                                                                // 
  digitalWrite(5, HIGH);                                                               // 
  digitalWrite(10, LOW);                                                               //
  digitalWrite(11, HIGH);                                                              //
  delay(1);                                                                            // 
  digitalWrite(5, LOW);                                                                // 
  digitalWrite(11, LOW);                                                               // 
  delay(1);                                                                            // 
  }                                                                                    // 
  while(count3 <=1655){                                                                //
  count3 = count3+1;                                                                   //
  digitalWrite(42, HIGH);                                                              //
  digitalWrite(53, LOW);                                                               //
  digitalWrite(6, HIGH);                                                               //
  digitalWrite(4, LOW);                                                                //
  digitalWrite(7, HIGH);                                                               // 
  digitalWrite(5, HIGH);                                                               //
  delay(1);                                                                            //  
  digitalWrite(7, LOW);                                                                // 
  digitalWrite(5, LOW);                                                                // 
  delay(1);                                                                            //
  }                                                                                    //
  }                                                                                    //
  ///////////////////////////////////////////////////////////////////////////////////////
  if(distance1 > distance2){
  Serial.print("Dreh nach Rechts_");  
  while (countrechts <= 1400){
  countrechts = countrechts + 1;
  digitalWrite(53,LOW);
  digitalWrite(49, LOW);
  digitalWrite(4, HIGH);
  digitalWrite(6, HIGH);
  digitalWrite(5, HIGH);
  digitalWrite(7, HIGH);
  delay(1);
  digitalWrite(5,LOW);
  digitalWrite(7, LOW);
  delay(1); 
 }
   while (countrechts2 <=3000){
  countrechts2 = countrechts2+1;
  digitalWrite(52, HIGH);
  digitalWrite(6, HIGH);
  digitalWrite(7, HIGH);
  digitalWrite(8, HIGH);
  digitalWrite(9, HIGH);
  delay(1);
  digitalWrite(7, LOW);
  digitalWrite(9, LOW);
  delay(1);
  }
  while (countrechts3 <=1655){
  countrechts3 = countrechts3+1;                                          
  digitalWrite(52,LOW);
  digitalWrite(42, HIGH);
  digitalWrite(6, HIGH);                                                               
  digitalWrite(4, LOW);                                                                
  digitalWrite(7, HIGH);                                                              
  digitalWrite(5, HIGH);                                                               
  delay(1);                                                                             
  digitalWrite(7, LOW);                                                                 
  digitalWrite(5, LOW);                                                                 
  delay(1);          
  }
  }
 count = 0; 
 count2 = 0;
 count3 = 0;
 countrechts = 0;
 countrechts2 = 0;
 countrechts3 = 0;
}
void ausweichen(){
  while(count <= 1100){
  count = count + 1;
  digitalWrite(53, LOW);
  digitalWrite(8, LOW);
  digitalWrite(10, HIGH);
  digitalWrite(6, LOW);
  digitalWrite(4, HIGH);
  digitalWrite(9, HIGH);
  digitalWrite(7, HIGH);
  digitalWrite(5, HIGH);
  digitalWrite(11, HIGH);
  delayMicroseconds(800);
  digitalWrite(9,LOW);
  digitalWrite(11, LOW);
  digitalWrite(5,LOW);
  digitalWrite(7,LOW);
  delayMicroseconds(800);
  }
  count = 0;
}
void setup() {
Serial.begin(9600); // // Serial Communication is starting with 9600 of baudrate speed
Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in Serial Monitor
Serial.println("with Arduino UNO R3");
pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT
pinMode (8, OUTPUT);
pinMode (9, OUTPUT);
pinMode (10, OUTPUT);
pinMode (11, OUTPUT);
pinMode (4, OUTPUT);
pinMode (5, OUTPUT);
pinMode (6, OUTPUT);
pinMode (7, OUTPUT);
pinMode (10, OUTPUT);
pinMode (11, OUTPUT);
pinMode(53, OUTPUT);
pinMode(52, OUTPUT);
pinMode(42, OUTPUT);
pinMode(trigPin1, OUTPUT); // Sets the trigPin as an OUTPUT
pinMode(echoPin1, INPUT); // Sets the echoPin as an INPUT
pinMode(trigPin2, OUTPUT); // Sets the trigPin as an OUTPUT
pinMode(echoPin2, INPUT); // Sets the echoPin as an INPUT
}
void loop(){
 //////////////////////////////////////////////////////////////////////////////////////////////// Radar-Messung-des-Abstands
 // Clears the trigPin condition
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)
  // Displays the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
//////////////////////////////////////////////////////////////////////////////////////////////////  
delayMicroseconds(100);
if(distance <= 55){
  rueckwaerts();
}
else
vorwaerts();
}

  
