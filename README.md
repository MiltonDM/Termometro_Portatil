# Termometro Portatil

*Proyecto basado en arduino que permite medir la temperatura , mostrarla en pantalla de lcd e indicar valores ideales atraves de un led RGB.*

Ingredientes
-----
```
1 x Arduino Uno R3
1 x Light bulb Incandescent light bulb 12V / 3W 
1 x PIEZO 22mm DIAMETER
1 x led
1 x PIR Sensor  Passive infrared motion sensor
1 x Power Supply (simulador de corriente)
1 x Relay SPDT  5V SPDT
1 x Ambient Light Sensor [Phototransistor]
1 x Ultrasonic Distance Sensor
1 x LCD display 16x2
1 x Potentiometer 10k
1 x resistor 220 ohm
2 x resistor 1 kohm
```
Vista de componetes
-----

![imagen](https://github.com/matiaslavanchi/Termometro_Portatil/blob/master/Termometro-Esquema.png)

Vista de esquema
-----

![imagen](https://github.com/matiaslavanchi/Termometro_Portatil/blob/master/Termometro-circuito.png)

Codigo fuente
-----
```
#include <LiquidCrystal.h>


LiquidCrystal lcd(7, 8, 9, 10, 11, 12);
const int sensorPin= A0;
const int verde=2;
const int azul=3;
const int rojo=4;
void setup() { 
  lcd.begin(16, 2);
  pinMode(verde,OUTPUT);
  pinMode(azul,OUTPUT);
  pinMode(rojo,OUTPUT);
  lcd.setCursor(0, 0);
  lcd.print("Temperatura: ");
}

void loop() {
  
  int value = analogRead(sensorPin);
  float millivolts = (value / 1024.0) * 5.0;
  float celsius = (millivolts -0.5)*100; 
  lcd.setCursor(0, 1);
  lcd.print(celsius);
  lcd.print("°");
  
  if(celsius<0){
    digitalWrite(azul,255);
  	digitalWrite(verde,0);
    digitalWrite(rojo,0);}
  else if (celsius>40){
    	digitalWrite(rojo,255);
    	digitalWrite(azul,0);
   		digitalWrite(verde,0);}
        else	{
    	digitalWrite(verde,255);
  		digitalWrite(azul,0);
    	digitalWrite(rojo,0);}
  
  delay(1000);
}
```
Enlace al proyecto en 
[circuit.io](https://circuits.io/circuits/4871286-temperatura)
