#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
/*------------------------------------------------*/
#define OLED_RESET 7
Adafruit_SSD1306 display(OLED_RESET);
/*------------------------------------------------*/
#define a_battonA 13
#define a_battonB 12
#define b_battonA 11
#define b_battonB 10
#define c_battonA 9
#define c_battonB 8
#define D_button 7
#define poten A0
int val_a = 0;
int val_b = 0;
int val_c = 0;
int formyla = 0;


void setup() {
  display.begin(SSD1306_SWITCHCAPVCC, 0x3C);  // инициализация дисплея по интерфейсу I2C, адрес 0x3C
  display.clearDisplay(); // очистка дисплея
  display.setTextSize(1); // установка размера шрифта
  display.setTextColor(WHITE); // установка цвета текста
  display.setCursor(0, 0); // установка курсора в позицию X = 0; Y = 0
  //display.print (val_a "+" val_b); // записываем в буфер памяти дисплея нашу фразу
 // display.display(); // и её выводим на экран
  


}
/*------------------------------------------------*/
void loop() {

  display.print (val_a);
  display.print (val_b);
  display.print (val_c); // записываем в буфер памяти дисплея нашу фразу
  display.display(); // и её выводим на экран
  
  if(digitalRead(a_battonA) == 1){
    val_a++;
  }
  if(digitalRead(a_battonB) == 1){
    val_a--;
  }
  if(digitalRead(b_battonA) == 1){
    val_b++;
  }
  if(digitalRead(b_battonB) == 1){
    val_b--;
  }
  if(digitalRead(c_battonA) == 1){
    val_c++;
  }
  if(digitalRead(c_battonB) == 1){
    val_c--;
  }
  rehit();
}

void rehit(){
  formyla = map(analogRead(A0), 0, 1023, 0, 10);
  switch (formyla) {
    case 0:
      
      break;
    case 1:
      
      break;
    case 2:
      
      break;
    case 3:
      
      break;
  }
}
