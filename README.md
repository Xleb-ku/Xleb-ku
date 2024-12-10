#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
#include <Fonts/FreeSerif9pt7b.h>

#include <math.h>

#define OLED_RESET 7
Adafruit_SSD1306 display(OLED_RESET);
#define a_battonA 13
#define a_battonB 12
#define b_battonA 11
#define b_battonB 10
#define c_battonA 9
#define c_battonB 8


#define poten A0
#define poten1 A1

//inline int pow(int x) { return x * x; }


int val_a = 0;
int val_b = 0;
int val_c = 0;
int formyla = 0;
int ileg = 0;




void setup() {
  Serial.begin(9600);

  pinMode(a_battonA, OUTPUT);
  pinMode(a_battonB, OUTPUT);
  pinMode(b_battonA, OUTPUT);
  pinMode(b_battonB, OUTPUT);
  pinMode(c_battonA, OUTPUT);
  pinMode(c_battonB, OUTPUT);


  display.begin(SSD1306_SWITCHCAPVCC, 0x3C);  // инициализация дисплея по интерфейсу I2C, адрес 0x3C
  display.clearDisplay(); // очистка дисплея
  display.setTextSize(1); // установка размера шрифта
  display.setTextColor(WHITE); // установка цвета текста
  display.setCursor(0, 0); // установка курсора в позицию X = 0; Y = 0
  //display.print (val_a "+" val_b); // записываем в буфер памяти дисплея нашу фразу
 // display.display(); // и её выводим на экран

  

 
}
void loop() {



  if(digitalRead(a_battonA) == 1){
    val_a++;
  }else{}
  if(digitalRead(a_battonB) == 1){
    val_a--;
  }else{}
  if(digitalRead(b_battonA) == 1){
    val_b++;
  }else{}
  if(digitalRead(b_battonB) == 1){
    val_b--;
  }else{}
  if(digitalRead(c_battonA) == 1){
   val_c++;
  }else{}
  if(digitalRead(c_battonB) == 1){
    val_c--;
  }else{}
 /*
 double disk = pow(val_b, 2) - 4 * val_a * val_c;
 double x1 = (val_b * (-1) + sqrt(disk)) / (2 * val_a);
 double x2 = (val_b * (-1) - sqrt(disk)) / (2 * val_a);
 */





  
  


  
  rehit();
  /*display.print (val_a );
  display.print (" ");
  display.print (val_b );
  display.print (" " );
  display.print (val_c );
  display.print (" " );
  display.print (disk );
  display.print (" " );
  display.print (x1 );
  display.print (" " );
  display.print (x2 );// записываем в буфер памяти дисплея нашу фразу
  display.display();
  display.clearDisplay();
  display.setCursor(0, 0); // установка курсора в позицию X = 0; Y = 0
 */
}

void rehit(){
  double disk = pow(val_b, 2) - 4 * val_a * val_c;
 double x1 = (val_b * (-1) + sqrt(disk)) / (2 * val_a);
 double x2 = (val_b * (-1) - sqrt(disk)) / (2 * val_a);
 double diskkorn = sqrt(disk);
 double diskk = 0;
  ileg = map(analogRead(A1), 0, 1023, 0, 6); 
  formyla = map(analogRead(A0), 0, 1023, 0, 10);
  switch (formyla) {
    case 0:
      switch(ileg){
         case 0:
           display.print (val_a );
           display.print ("x^2+");
           display.print (val_b );
           display.print ("x+" );
           display.print (val_c );
           display.print ("=0" );
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0); 
           break; 
         case 1:
           display.print ("D=" );
           display.print (val_b);
           display.print ("^2-4*");
           display.print (val_a );
           display.print ("*" );
           display.print (val_c);
           display.print ("=");
           display.print (disk);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
          case 2:
           display.print ("x1=(-" );
           display.print (val_b);
           display.print ("+");
           display.print ( diskkorn);
           display.print (")/(" );
           display.print (val_a);
           display.print ("*2)=");
           display.print (x1);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
            break;
          case 3:
           display.print ("x2=(-" );
           display.print (val_b);
           display.print ("-");
           display.print ( diskkorn);
           display.print (")/(" );
           display.print (val_a);
           display.print ("*2)=");
           display.print (x2);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
      }
 
      break;
    case 1:
       switch(ileg){
         case 0:
           display.print (val_a);
           display.print ("-");
           display.print (val_b);
           display.print ("=");
           display.print (val_a - val_b);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
          case 1:   
           display.print (val_a);
           display.print ("+");
           display.print (val_b);
           display.print ("=");
           display.print (val_a + val_b);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
          case 2:   
           display.print (val_a);
           display.print ("/");
           display.print (val_b);
           display.print ("=");
           display.print (val_a / val_b);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
          case 3:   
           display.print (val_a);
           display.print ("*");
           display.print (val_b);
           display.print ("=");
           display.print (val_a * val_b);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
       }
      
      
      break;
    case 2:
      switch(ileg){
        case 0:
           display.print (val_a );
           display.print ("x^4+");
           display.print (val_b );
           display.print ("x^2+" );
           display.print (val_c );
           display.print ("=0" );
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0); 
           break; 
       case 1:
           display.print ("D=" );
           display.print (val_b);
           display.print ("^2-4*");
           display.print (val_a );
           display.print ("*" );
           display.print (val_c);
           display.print ("=");
           display.print (disk);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
        case 2:
           display.print ("T1=(-" );
           display.print (val_b);
           display.print ("+");
           display.print ( diskkorn);
           display.print (")/(" );
           display.print (val_a);
           display.print ("*2)=");
           display.print (x1);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
            break;
        case 3:
           display.print ("T2=(-" );
           display.print (val_b);
           display.print ("-");
           display.print ( diskkorn);
           display.print (")/(" );
           display.print (val_a);
           display.print ("*2)=");
           display.print (x2);
           display.display();
           display.clearDisplay();
           display.setCursor(0, 0);
           break;
        case 4:
          display.print("x1=");
          display.print(sqrt(x1));
          display.display();
          display.clearDisplay();
          display.setCursor(0, 0);
          break;
         case 5:
          display.print("x2=");
          display.print(sqrt(x2));
          display.display();
          display.clearDisplay();
          display.setCursor(0, 0);
          break;
      }
      
      break;
    case 3:
      
      break;
  }
}
