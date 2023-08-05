#include<LiquidCrystal_I2C.h>
#include<Wire.h>
LiquidCrystal_I2C lcd(32,16,2);
int Force_VAL = 0;
int reading;
void setup()
{
  pinMode(A0, INPUT);
  Serial.begin(9600);
  lcd.begin(16,2);
   lcd.init();
  lcd.backlight();
  lcd.setCursor(0,0);
  lcd.print("Loading Force...");
  lcd.setCursor(0,0);
  delay(1000);
  lcd.clear();
  lcd.print("Reading = ");
}

void loop()
{
  Force_VAL = analogRead(A0);
  reading=map(Force_VAL ,0,1023,0,466);
  Serial.println(reading);
  lcd.setCursor(0,1);
  lcd.print(Force_VAL);
  delay(10);
}
