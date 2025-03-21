# automatic-motor-switch-control-using-iot
The objective of the project is to design an IoT-based system for automatic motor switch control to optimize water and energy usage. It aims to enable remote monitoring, smart scheduling, and real-time diagnostics while preventing issues like overloading and water wastage. The solution focuses on efficiency, reliability, and sustainability.
#define BLYNK_TEMPLATE_ID "TMPL38E6wLL_S"
#define BLYNK_TEMPLATE_NAME "IOT Based Automated Motor Switch pump Control"

#include <ESP8266WiFi.h> #include <BlynkSimpleEsp8266.h>
char auth[] = "RHYrkoYE3LgTrXUEDG4rW_gimR9hDUHe"; char ssid[] = "Appi";
char pass[] = "Ammu@2005";

const int motorPin1 = D1; const int motorPin2 = D2; const int pumpPin1 = D5; const int pumpPin2 = D6;

void setup() { pinMode(motorPin1, OUTPUT); pinMode(motorPin2, OUTPUT); pinMode(pumpPin1, OUTPUT); pinMode(pumpPin2, OUTPUT);

digitalWrite(motorPin1, LOW); digitalWrite(motorPin2, LOW); digitalWrite(pumpPin1, LOW); digitalWrite(pumpPin2, LOW);

Serial.begin(115200);

Blynk.begin(auth, ssid, pass);
}

void loop() { Blynk.run();
}

BLYNK_WRITE(V1) {
int motorState = param.asInt(); if (motorState == 1) {
digitalWrite(motorPin1, HIGH); digitalWrite(motorPin2, LOW);
}
 
else
{
digitalWrite(motorPin1, LOW); digitalWrite(motorPin2, LOW);
}
}

BLYNK_WRITE(V2) {
int pumpState = param.asInt(); if (pumpState == 1) {
digitalWrite(pumpPin1, HIGH); digitalWrite(pumpPin2, LOW);
} else
{
digitalWrite(pumpPin1, LOW); digitalWrite(pumpPin2, LOW);
}
}
