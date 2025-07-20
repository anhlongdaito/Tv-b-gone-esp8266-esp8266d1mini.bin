# TV-B-Gone ESP8266 (D1 Mini Version)

This is a compact version of the classic [TV-B-Gone](https://github.com/adafruit/tvbgone) project, using an **ESP8266 D1 Mini** and **IR LEDs** to turn off most television sets in public places.

I have compiled the firmware into a `.bin` file to make it easy for others to flash and use without needing to build from source.

---

## 🔧 Hardware Required

- ESP8266 D1 Mini
- 1–4 IR LEDs (e.g. TSAL6200)
- Resistors (100–220 ohm depending on LED config)
- NPN transistor (optional, for driving multiple IR LEDs)
- Button (to trigger IR burst)
- Power source (e.g. 18650 battery or USB)

---

## Flashing Instructions

1. Install [ESPHome-Flasher](https://github.com/esphome/esphome-flasher/releases) **or** use `esptool.py`.
2. Connect your D1 Mini via USB.
3. Flash the `.bin` file provided in this repo:
   ```bash
   esptool.py --port /dev/ttyUSB0 write_flash 0x00000 Tv-b-gone-esp8266d1mini.bin
![17530131364984736583535560755682](https://github.com/user-attachments/assets/7a46a5fb-fa5d-435d-88ea-fd7c1f159004)
