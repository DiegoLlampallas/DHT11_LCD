# Práctica ESP32 con DHT11 y pantalla LCD de Diego Llampallas

A continuación se mostrará acontinuación la programación de la práctica ESP32 con DHT11 y con lcd de 16x2:

## Introducción
A través de la página https://wokwi.com/  se puede hacer simulaciones de programas con arduino y sensores.
### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH11```) para adquirir temperatura y humedad del entorno, Se usará una pantalla LCD para visualización de resultados; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica se usaran los siguientes elementos:

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT11
- Pantalla LCD 16X2
- Fuente de voltaje de 5v
- Tierra



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 
1. Una vez dentro de wokwi seleccionar la tarjeta ESP32

![](https://github.com/DiegoLlampallas/Practica-DHT22/blob/main/6.png?raw=true)

2. Abrir la terminal de programación y colocar la siguente programación:
## Programación

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);

  lcd.setCursor(0, 0);
  lcd.print("Diego Llampallas");
  lcd.setCursor(0, 1);
  lcd.print("Modulo 5, Día 2");

  delay(1000);
}
```

## Librerías

1. **DHT sensor library for ESPx**
2. **LiquidCrystal I2C**

## Conexión

![](https://github.com/DiegoLlampallas/DHT11_LCD/blob/main/2.png?raw=true)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT11** 
4. Visualizar los datos en pantalla LCD 16X2

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial y en la pantalla LCD.

## Funcionamiento del programa

![](https://github.com/DiegoLlampallas/DHT11_LCD/blob/main/3.png?raw=true)
![](https://github.com/DiegoLlampallas/DHT11_LCD/blob/main/4.png?raw=true)

## Evidencias

[Página](https://wokwi.com/projects/367153177232147457)


# Créditos

Desarrollado por Ing. Diego Alberto Llampallas Vega

- [GitHub](https://github.com/DiegoLlampallas)