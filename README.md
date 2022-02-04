# esp32_wifi
#include <Arduino.h>
#include <WiFi.h>

#define WIFI_NETWORK "shahar lavon"
#define WIFI_PASSWORD "11111987"
#define WIFI_TIMEOUT_MS 80000

void connectionToWifi(){
  Serial.print("connecting to wifi");
  WiFi.mode(WIFI_STA);
  WiFi.begin(WIFI_NETWORK, WIFI_PASSWORD);

  unsigned long startAttempTime = millis();\

  while (WiFi.status() != WL_CONNECTED && (millis()-startAttempTime) < WIFI_TIMEOUT_MS){
    Serial.print(".");
    
    delay(100);
  }
  if (WiFi.status() != WL_CONNECTED){
    Serial.println("failed");
    //take action
  }
  else{
    Serial.print("connected");
    Serial.println(WiFi.localIP());
  }

}

void setup() {
  Serial.begin(9600);
  connectionToWifi();
}

void loop() {
  // put your main code here, to run repeatedly:
}
