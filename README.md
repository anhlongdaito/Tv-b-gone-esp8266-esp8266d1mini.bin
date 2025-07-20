## How TV-B-Gone Works

TV-B-Gone is a simple but powerful universal remote that can turn off almost any TV. It works by sending a sequence of infrared (IR) power-off codes for hundreds of TV brands.

### How it works:

1. **Startup:**
   - When powered on and the switch (D2) is set to ON, the ESP8266 begins the IR code transmission.

2. **Button Press:**
   - You press the push-button to start transmission.
   - The microcontroller (ESP8266) starts sending pre-programmed IR signals using standard TV remote power-off codes.

3. **IR Code Emission:**
   - The IR LEDs flash high-frequency signals (38kHz carrier) modulated with data that TVs recognize as the "power off" command.
   - The transistor (2N2222) boosts the current so multiple IR LEDs can fire strongly and cover a wider area.

4. **TV Response:**
   - When a nearby TV receives a matching code, it will turn off instantly.
   - Since hundreds of codes are sent in order, the chance of turning off almost any brand is very high.

5. **End:**
   - After all codes are sent, the device stops until you press the button again.

### Notes:
- The IR beam works best when pointed at the TV directly within 5–10 meters.
- You can use more LEDs to increase range.
- ![17530135441327243743740358195185](https://github.com/user-attachments/assets/7280942b-303a-4dad-8549-fc190c5ccf37)

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
## Wiring Instructions (Hardware Setup)

This project uses an ESP8266 board (NodeMCU or D1 Mini), IR LEDs, a 2N2222 transistor, a push-button, and a power switch. Below is a clear guide to connect everything:

### Connections:

- **IR LEDs (3–5 in parallel):**
  - Connect the **cathodes** (short legs) of all IR LEDs together to **Ground** (GND).
  - Connect the **anodes** (long legs) together through a **220–330 ohm resistor** to the **collector (C)** of the transistor.

- **2N2222 Transistor:**
  - **Collector (C)** → Connected to IR LEDs' anodes 
  - **Emitter (E)** → Connected to **GND**.
  - **Base (B)** → Connected to a **2.2kΩ resistor**, then to **GPIO D5** (or other pin you use).

- **Push-button:**
  - Connect one leg to **GPIO D6**.
  - Connect the other leg to **GND**.

- **Switch (Power control):**
  - Connect between **GND** and **GPIO D2**.
  - When **switch is OFF** → D2 is LOW → Device stays idle.
  - When **switch is ON** → D2 is HIGH → IR transmission is enabled.

> This switch acts as a safety trigger: it only allows transmission when toggled ON.

- **Power Supply:**
  - Use a 3.7V Li-ion battery (like 18650) with a boost converter or directly via USB for the ESP8266.

Make sure your components are securely soldered, and IR LEDs are properly aligned to point at the TV for best range!

![17530134325723276798421658483165](https://github.com/user-attachments/assets/0d484c54-de27-4afb-9945-ed2bd0afdb0f)


