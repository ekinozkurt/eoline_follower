# eoline_follower
//Line Following Robot 
int sag_enable=11; //EnA
int sol_enable=6; //EnB
int sag_ileri=10; // INPUT1
int sag_geri=9; // INPUT2
int sol_ileri=8; //INPUT3
int sol_geri=7; //INPUT4
int sensor=3; //SENSOR
int buzzerPin=2; //buzzer
#define ledbeyazPin=12 //beyaz led
#define ledkirmiziPin=4 //kırmızı led

void setup() {
  //Tekerler ve motor
pinMode(sag_ileri, OUTPUT);
pinMode(sag_geri, OUTPUT);
pinMode(sol_ileri, OUTPUT);
pinMode(sol_geri,OUTPUT);
pinMode(sag_enable, OUTPUT);
pinMode(sol_enable, OUTPUT);
// Siyah ve beyaz okuyan kızılötesi sensör
pinMode(sensor, INPUT);
//Buzzer
pinMode(buzzerPin, OUTPUT);

Serial.begin(9600);

//Led
pinMode(12, OUTPUT); // beyaz led
pinMode(4, OUTPUT);  // kırmızı led

}

void loop() {
  int veri= digitalRead(sensor);
Serial.println(veri); // sensörün okuduğu rengi 1-0 olarak monitöre yazdırma

  if (veri==1){ //siyah rengi okuması durumu
    digitalWrite(sag_ileri, HIGH);
    digitalWrite(sag_geri, LOW);
    digitalWrite(sol_ileri, HIGH);
    digitalWrite(sol_geri, LOW);
    analogWrite(sag_enable, 255);
    analogWrite(sol_enable, 255);
   
  //LED KOMUT KODLARI
 digitalWrite(12, HIGH);
 delay(100);
 digitalWrite(4,LOW);
 delay(50);
/* digitalWrite(12, LOW);
 delay(50);*/
 

//Buzzerkodu
int notalar[] = {1000, 294, 330, 349, 392, 440, 494, 523};

for (int i = 0; i < 8; i++) {
    tone(buzzerPin, notalar[i], 500); // Her nota 0.5 saniye boyunca çalacak
delay(500); // Her nota arasında yarım saniye bekle */
}

  }
  else if (veri==0){
    digitalWrite(sag_ileri, LOW);
    digitalWrite(sag_geri, LOW);
    digitalWrite(sol_ileri, LOW);
    digitalWrite(sol_geri, LOW);
    analogWrite(sag_enable, 0);
    analogWrite(sol_enable, 0);
    
  /*noTone(buzzerPin); // Ses kapat
    delay(500); // Notalar arasında 0.5 saniye bekle*/

digitalWrite(4, HIGH);
 delay(100);
 digitalWrite(12,LOW);
 delay(50);
 /*digitalWrite(4, LOW);
 delay(1000);*/
  }
    }
  
