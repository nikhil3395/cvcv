# cvcv
1st experi-------
int carRed = 12; // To assign the car lights
int carYellow = 11;
int carGreen = 10;
int pedRed = 9; // To assign the pedestrian lights
int pedGreen = 8;
int button = 2; // Tactile button pin
int crossTime = 5000; // time allowed to cross
unsigned long changeTime; // time since button pressed
void setup()
{
pinMode(carRed, OUTPUT);
pinMode(carYellow, OUTPUT);
pinMode(carGreen, OUTPUT);
pinMode(pedRed, OUTPUT);
pinMode(pedGreen, OUTPUT);
pinMode(button, INPUT); // button on pin 2
// turn on the green light
digitalWrite(carGreen, HIGH);
digitalWrite(pedRed, HIGH);
}
void loop()
{
int state = digitalRead(button);
/* check if button is pressed and it is
over 5 seconds since last button press */
if (state == HIGH && (millis() - changeTime) > 5000)
{
15 | P a g e
// Call the function to change the lights
changeLights();
}
}
void changeLights() {
digitalWrite(carGreen, LOW); // green off
digitalWrite(carYellow, HIGH); // yellow on
delay(2000); // wait 2 seconds
digitalWrite(carYellow, LOW); // yellow off
digitalWrite(carRed, HIGH); // red on
delay(1000); // wait 1 second till its safe
digitalWrite(pedRed, LOW); // ped red off
digitalWrite(pedGreen, HIGH); // ped green on
delay(crossTime); // wait for preset time period
// flash the ped green
for (int x=0; x<10; x++) {
digitalWrite(pedGreen, HIGH);
delay(250);
digitalWrite(pedGreen, LOW);
delay(250);
}
// turn ped red on
digitalWrite(pedRed, HIGH);
delay(500);
digitalWrite(carYellow, HIGH); // Yellow will switch on
digitalWrite(carRed, LOW); // red will switch off
delay(1000);
digitalWrite(carGreen, HIGH);
digitalWrite(carYellow, LOW); // Yellow will switch off
// record the time since last change of lights
changeTime = millis();
16 | P a g e
// Retun / Loop
}
