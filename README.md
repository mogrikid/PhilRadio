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

1. Clone the repository
2. Install required libraries via Arduino IDE
3. Upload code to ESP32 Cheap Yellow Display
4. Set the wifi credentials with the onboard keyboard on screen and connect
5. connect to the webserver from a browser and add radio stations

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
