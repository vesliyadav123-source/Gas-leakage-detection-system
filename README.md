# Gas-leakage-detection-system
It is a project that observes the wanted and unwanted gases it depends on how were giving input and detects and it is useful to normal people how means when some one forgot to off their cylinder it detects and it will give buzzer sound and it show in advanced it will give a msg to the phone viya bluetooth 

     code 
       #define MQ2_SENSOR A0
#define BUZZER 8
#define LED 9

int gasValue = 0;
int threshold = 300; // Adjust based on sensitivity

void setup() {
  pinMode(MQ2_SENSOR, INPUT);
  pinMode(BUZZER, OUTPUT);
  pinMode(LED, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  gasValue = analogRead(MQ2_SENSOR);
  Serial.print("Gas Level: ");
  Serial.println(gasValue);

  if (gasValue > threshold) {
    digitalWrite(BUZZER, HIGH);
    digitalWrite(LED, HIGH);
    Serial.println("⚠️ Gas Leak Detected!");
  } else {
    digitalWrite(BUZZER, LOW);
    digitalWrite(LED, LOW);
  }

  delay(500);
}
