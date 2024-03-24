# Kontrol-Lampu-Rumahan-dengan-sesnor-PIR-dan-Sensor-Suara-Bluetooth
#include <LiquidCrystal.h>
String voice;
LiquidCrystal lcd (7, 6, 5, 4, 3, 2);
int pir = 10;
int pinPir = 10;
void setup() {
  // put your setup code here, to run once:
  pinMode(13, OUTPUT);
  pinMode(10, INPUT);
  Serial.begin(9600);
  lcd.begin(16, 2);
}

void loop() {
  pinPir = digitalRead (pir);
  lcd.setCursor(0,0);
  lcd.clear();

  if (Serial.available() > 0){ 
    voice = "";
    delay(150);
    voice = Serial.readString();
    delay(150);
  }
  
if ((voice == "menyalakan lampu")||(pinPir == HIGH)) {
    digitalWrite(13, HIGH);
    lcd.print("LAMPU HIDUP");
    delay(150);
  }
else if ((voice == "mematikan lampu")||(pinPir == LOW)) {
    digitalWrite(13, LOW);
    lcd.print("LAMPU MATI");
    delay(150);
  }
}
