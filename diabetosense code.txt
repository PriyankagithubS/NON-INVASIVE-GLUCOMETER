#include <Wire.h>
#include <SPI.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
#define OLED_RESET 4
Adafruit_SSD1306
display(OLED_RESET);
int sensorPin = A0;
int digitalValue = 0;

#define OLED_RESET 4

#if (SSD1306_LCDHEIGHT != 64)
#endif

void setup() {

// Set up the display
display.begin(SSD1306_SWITCHCAPVCC, 0x3C);
display.clearDisplay();
display.setTextSize(1);
display.setTextColor(WHITE);
display.setCursor(0, 0);
  // Display static text
display.println("   Welcome to TEAM DIABETO SENSE");
display.display();
delay(1000);// Initialize with the I2C addr 0x3D if not working use 0x3C (for the 128x64)
//display.setTextColor(WHITE);
//display.clearDisplay();
//display.display();
//display.drawPixel(0, 0, WHITE);
//display.drawPixel(127, 0, WHITE);
//display.drawPixel(0, 63, WHITE);
//display.drawPixel(127, 63, WHITE);


}
void loop(){

delay(1);//delay time 1 mili second
display.clearDisplay();
display.setTextSize(1);//text size
display.setTextColor(WHITE);//text color
display.setCursor(0,0);
display.println("welcome to BIT");//display out text 1st line
display.setTextColor(WHITE,BLACK);
display.setTextSize (1);
display.setCursor (0,10);
display.println("Acetone value=" + String(digitalValue));

display.setTextSize (1);
display.setTextColor(WHITE,BLACK);
display.setCursor (0,20);  
digitalValue = analogRead(A0);
if(digitalValue>500)
{
display.println("Acetone is High");
}
else if(digitalValue>250)
{
display.println("Acetone is Medium");
}
     else
     {
     display.println("Acetone is Low");
     }
  delay(3000);
  display.display();
}