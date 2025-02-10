# ESP32 Internet Radio with Cheap Yellow Display
## Overview
A DIY internet radio project using the ESP32 Cheap Yellow Display, transforming an old Philips radio into a modern streaming device with web-based station management.

![WiFi Radio](https://github.com/mogrikid/PhilRadio/blob/Main/images/radio.jpg)
![WiFi Radio UI](https://github.com/mogrikid/PhilRadio/blob/Main/images/screen.jpg)


## Features

- Web-based radio station management
- Touchscreen interface for station selection
- WiFi connectivity
- Volume control via potentiometer
- Persistent station storage
- Embedded web server for station configuration

## Hardware Requirements

- ESP32 Cheap Yellow Display
- Old Philips radio (or similar)
- 10kΩ potentiometer
- External USB power connection
- 10kΩ Resistor to [improve the audio quality](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/Mods/README.md).

## Hardware Modifications
### Audio Quality Improvement
As detailed in the original project mod, add a resistor to enhance audio output quality, as described in [this project](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/Mods/README.md).

## Software Dependencies

- Arduino IDE
- Required Libraries:
  - Audio
  - ArduinoJson
  - lvgl
  - Preferences
  - WiFi
  - ESPAsyncWebServer
  - SPIFFS
  - XPT2046_Touchscreen
  - TFT_eSPI



## Installation

Note: As time of writing, uploading the sketch works with Arduino 2.x.x., but uploading the SPIFFS data is only possible by using the ESP32fs Plugin in Arduino 1.x.x

### Installing from source

1. Clone the repository
2. Install required libraries via Arduino IDE
3. Working Arduino IDE settings:

| Board                                | ESP32 Dev Module            |
|--------------------------------------|-----------------------------|
| Port                                 | [Your Port]                 |
| CPU Frequency                        | 240MHz (WiFi/BT)            |
| Core Debug Level                     | None                        |
| Erase All Flash Before Sketch Upload | Disabled                    |
| Events Run On                        | Core 1                      |
| Flash Frequency                      | 80MHz                       |
| Flash Mode                           | QIO                         |
| Flash Size                           | 4MB (32Mb)                  |
| JTAG Adapter                         | Disabled                    |
| Arduino Runs on                      | Core 1                      |
| Partition Scheme                     | No OTA (2MB APP/2MB SPIFFS) |
| PSRAM                                | Disabled                    |
| Upload Speed                         | 460800                      |

4. Upload code to ESP32 Cheap Yellow Display
5. From here, use Arduino IDE 1.x.x, as the ESP32fs plugin was not supported in 2.x.x as time of writing
6. Install the [ESP32fs-plugin](https://github.com/me-no-dev/arduino-esp32fs-plugin) in Arduino 1.x.x. as library from Github
7. In the Arduino IDE, select Tools > ESP32 Sketch Data Upload
8. Once the CYD started, connect to a wifi station, restart and connect to the webserver from a browser and add radio stations via http://device-ip (listed in the headline of the screen, once connected)

### Installing from binary release

1. Download latest release from the [releases page](https://github.com/mogrikid/PhilRadio/releases)
2. Download [the esptool](https://github.com/espressif/esptool?tab=readme-ov-file) from Github
3. Upload the release binary with the following command
```bash 
python3 esptool.py --chip esp32 \
  --port [YOUR PORT]] \
  --baud 115200 \
  --before default_reset \
  --after hard_reset \
  write_flash \
  -z \
  --flash_mode dio \
  --flash_freq 40m \
  --flash_size detect \
  0x1000 release/wifiRadio.ino.bootloader.bin \
  0x8000 release/wifiRadio.ino.partitions.bin \
  0x10000 release/wifiRadio.ino.bin
```
4. In Arduino 1.x.x (2.0 is currently not supported here), create a new project or clone this one
5. Create a data folder inside that project, place the index.html from the release in that folder
6. Install the [ESP32fs-plugin](https://github.com/me-no-dev/arduino-esp32fs-plugin) in Arduino 1.x.x. as library from Github
7. In the Arduino IDE, select Tools > ESP32 Sketch Data Upload
8. Once the CYD started, connect to a wifi station, restart and connect to the webserver from a browser and add radio stations via http://device-ip (listed in the headline of the screen, once connected)

## Web Interface
Access the web configuration at http://device-ip to:
- View current radio stations
- Add/remove stations

![WiFi Radio Webserver](https://github.com/mogrikid/PhilRadio/blob/Main/images/server.png)

Credits
Inspired by and building upon the [ESP32 Cheap Yellow Display project](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display).

## License
This project is licensed as MIT as per the [license file](https://github.com/mogrikid/PhilRadio/blob/Main/LICENSE)

## Final Note
The code is far from perfect, but the UI works, the radio plays flawlessly for hours and maybe others can build upon it. 
