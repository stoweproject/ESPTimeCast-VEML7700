# ESPTimeCast with VEML7700 Ambient Light Sensor

This is a modified version of the ESPTimeCast project that adds support for the VEML7700 ambient light sensor. The sensor is used to automatically control the display brightness based on ambient light levels, and can also display the current LUX reading.

## Features Added

- Automatic display brightness control based on ambient light
- Display turns off completely when ambient light is below a configurable threshold
- Option to display current LUX reading on the LED matrix
- Configurable LUX threshold for turning off the display
- Web interface for configuring all VEML7700 settings

## Hardware Setup

### Wiring the VEML7700 Sensor

The VEML7700 is an I2C sensor that connects to the ESP8266 as follows:

| VEML7700 | Wemos D1 Mini |
|:--------:|:-------------:|
| VIN      | 3V3           |
| GND      | GND           |
| SCL      | D1 (GPIO 5)   |
| SDA      | D2 (GPIO 4)   |

### Complete Wiring Diagram

| Component | Wemos D1 Mini (v3.x) | Wemos D1 Mini (v4.0) |
|:----------|:---------------------|:---------------------|
| MAX7219 CLK | D6 (GPIO 12)       | 12                   |
| MAX7219 CS  | D7 (GPIO 13)       | 13                   |
| MAX7219 DIN | D8 (GPIO 15)       | 15                   |
| MAX7219 VCC | 3V3                | 3V3                  |
| MAX7219 GND | GND                | GND                  |
| VEML7700 VIN | 3V3               | 3V3                  |
| VEML7700 GND | GND               | GND                  |
| VEML7700 SCL | D1 (GPIO 5)       | D1 (GPIO 5)          |
| VEML7700 SDA | D2 (GPIO 4)       | D2 (GPIO 4)          |

## Configuration

The VEML7700 settings can be configured through the web interface under the "Advanced Settings" section:

1. **Enable VEML7700 Light Sensor**: Turn on/off the ambient light sensor functionality
2. **Show LUX Reading**: When enabled, the display will show the current LUX reading as an additional display mode
3. **LUX Threshold**: Set the light level (in LUX) below which the display will turn off completely

## How It Works

1. The VEML7700 sensor measures ambient light in LUX
2. If the measured LUX is below the threshold, the display turns off completely
3. When the LUX is above the threshold, the display operates normally
4. If "Show LUX" is enabled, the current LUX reading will be shown in the display rotation (Clock → Weather → Weather Description → LUX)

## Dependencies

This project requires the Adafruit VEML7700 library:

```
arduino-cli lib install "Adafruit VEML7700 Library"
```

This will also install the required dependencies:
- Adafruit BusIO
- Adafruit SSD1306
- Adafruit GFX Library
