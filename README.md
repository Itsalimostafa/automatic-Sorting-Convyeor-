# automatic-Sorting-Convyeor-

#define sensor0 A0 // Sharp IR GP2Y0A41SK0F (4-80cm, analog)
#define sensor1 A1
void setup() {
  Serial.begin(9600); // start the serial port
}

void loop() {
  
  // 5v
  float volts = analogRead(sensor0)*0.0048828125; 
  float volts1 = analogRead(sensor1)*0.0048828125;// value from sensor * (5/1024)
  int distance0 = 13*pow(volts, -1); // worked out from datasheet graph
  delay(1000); // slow down serial port 
  int distance1 = 13*pow(volts1, -1); 
 
 if (distance0 <= 80){
     
  Serial.print("dinstance0 ="); 
   Serial.println(distance0*2); 
    // print the distance
  // value from sensor * (5/1024)
 }
  delay(1000); // slow down serial port 
  
 if (distance1 <= 80){
        Serial.print("dinstance1 ="); 
   Serial.println(distance1*2); 
 }
 float h;
 float W;
 int L=25;
 float volume;
  h=45-(distance0*2);
  delay(2000); // slow down serial port 
  W=47-(distance1*2*2);
  volume=L*W*h ;
  Serial.print("volume="); 
   Serial.println(volume); 
int relayPin = 3;
int relayPin2= 4;
int relayPin5= 5;
int loopDelay = 1000;
  { if (volume <12000){

    pinMode(relayPin, OUTPUT);// set pin as output
   // digitalWrite(relayPin, HIGH); // set initial state OFF for low trigger relay
  Serial.begin(9600);// initialize serial monitor with 9600 baud
  Serial.println("box A");
  delay(500);

  // AC load control with 5V relay
 // turn relay ON
   digitalWrite(relayPin, HIGH);
  Serial.println("Relay is ON");  
  delay(2000);// wait for 2 seconds


 // turn relay OFF
  digitalWrite(relayPin, LOW);
  Serial.println("Relay is OFF");   
  delay(2000);// wait for 2 seconds
 
}  if  (12000<=volume<=22000){
  pinMode(relayPin2, OUTPUT);// set pin as output
  digitalWrite(relayPin2, LOW); // set initial state OFF for low trigger relay
  Serial.begin(9600);// initialize serial monitor with 9600 baud
  Serial.println("box B");
  delay(500);

  // AC load control with 5V relay
 // turn relay ON
   digitalWrite(relayPin2, HIGH);
  Serial.println("Relay is ON");  
  delay(2000);// wait for 2 seconds


 // turn relay OFF
  digitalWrite(relayPin2, LOW);
  Serial.println("Relay is OFF");   
  delay(2000);// wait for 2 seconds
  }
      else if  (volume>22001){
  pinMode(relayPin5, OUTPUT);// set pin as output
  digitalWrite(relayPin5, LOW); // set initial state OFF for low trigger relay
  Serial.begin(9600);// initialize serial monitor with 9600 baud
  Serial.println("box B");
  delay(500);

  // AC load control with 5V relay
 // turn relay ON
   digitalWrite(relayPin5, HIGH);
  Serial.println("Relay is ON");  
  delay(2000);// wait for 2 seconds


 // turn relay OFF
  digitalWrite(relayPin5, LOW);
  Serial.println("Relay is OFF");   
  delay(2000);// wait for 2 seconds
}
}

 
