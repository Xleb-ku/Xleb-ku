#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
/*------------------------------------------------*/
#define OLED_RESET 7
Adafruit_SSD1306 display(OLED_RESET);
/*------------------------------------------------*/

void setup() {
  display.begin(SSD1306_SWITCHCAPVCC, 0x3C);  // инициализация дисплея по интерфейсу I2C, адрес 0x3C
  display.clearDisplay(); // очистка дисплея
  display.setTextSize(1); // установка размера шрифта
  display.setTextColor(WHITE); // установка цвета текста
  display.setCursor(0, 0); // установка курсора в позицию X = 0; Y = 0
  display.print ("tponul gey"); // записываем в буфер памяти дисплея нашу фразу
  display.display(); // и её выводим на экран



}
/*------------------------------------------------*/
void loop() {
  display.startscrolldiagright(0x00, 0x0F); // прокручиваем сообщение по диагонали вправо
  delay(3000); // в течении 3-х секунд
  display.stopscroll(); // останавливаем прокрутку
  delay(1000); // ждём 1 секунду
  display.startscrolldiagleft(0x00, 0x0F); // прокручиваем сообщение по диагонали влево
  delay(3000); // в течение 3-х секунд
  display.stopscroll(); // останавливаем прокрутку
  delay(1000); // ждём 1 секунду
  display.startscrollright(0x00, 0x0F); // прокручиваем сообщение вправо
  delay(3000); // в течении 3-х секунд
  display.stopscroll(); // останавливаем прокрутку
  delay(1000); // ждём 1 секунду
  display.startscrollleft(0x00, 0x0F); // прокручиваем сообщение влево
  delay(3000); // в течение 3-х секунд
  display.stopscroll(); // останавливаем прокрутку
  delay(1000); // ждём 1 секунду

}
/*
