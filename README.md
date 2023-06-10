# Práctica ESP32 con DHT11 y Lcd de Diego Llampallas

A continuación se mostrará acontinuación la programación de la práctica ESP32 con DHT11 y con lcd de 16x2:

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

## Funcionamiento del programa

![](https://github.com/DiegoLlampallas/DHT11_LCD/blob/main/3.png?raw=true)
![](https://github.com/DiegoLlampallas/DHT11_LCD/blob/main/4.png?raw=true)

## Evidencias

[Página](https://wokwi.com/projects/367153177232147457)


# Créditos

Desarrollado por Ing. Diego Alberto Llampallas Vega

- [GitHub](https://github.com/DiegoLlampallas)