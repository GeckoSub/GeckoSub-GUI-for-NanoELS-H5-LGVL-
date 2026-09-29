Base "Hello ELS!" LVGL demo for the ESP32P4-JC1060P470C_I_W_Y 7" V2 display — plain LVGL, no SquareLine Studio, no custom GUI. Starting point for anyone bringing this screen up from scratch.

Based on [wegi1/ESP32P4-JC1060P470C-I_W_Y](https://github.com/wegi1/ESP32P4-JC1060P470C-I_W_Y)

Code changes all done with Claude Sonnet 5.5

## RAM fix (PSRAM)
By default, LVGL keeps its own memory in a fixed block on the chip's built-in RAM, whether or not you have extra RAM available. This board also has 32MB of extra RAM (PSRAM), so we changed one setting in lv_conf.h (LV_USE_STDLIB_MALLOC to LV_STDLIB_CLIB) so LVGL uses that extra RAM instead. This frees up the chip's built-in RAM for everything else.

## Requirements
- ESP32 board package installed in Arduino IDE (Tools → Board → Boards Manager → "esp32" by Espressif), version **3.1.0 or newer**
- LVGL library version **9.2.2**
- Move the `demos` folder out of the LVGL library folder into this sketch's `src` folder (same location as `src/lcd` and `src/touch`)

## Arduino IDE board settings (Tools menu)
- Board: **ESP32P4 Dev Module**
- USB CDC On Boot: **Disabled**
- CPU Frequency: **360MHz**
- Core Debug Level: **None**
- USB DFU On Boot: **Disabled**
- Erase All Flash Before Sketch Upload: **Disabled**
- Flash Frequency: **80MHz**
- Flash Mode: **QIO**
- Flash Size: **16MB (128Mb)**
- JTAG Adapter: **Disabled**
- USB Firmware MSC On Boot: **Disabled**
- Partition Scheme: **16M Flash (3MB APP/9.9MB FATFS)**
- PSRAM: **Enabled**
- Upload Mode: **UART0 / Hardware CDC**
- Upload Speed: **921600**
- USB Mode: **USB-OTG (TinyUSB)**

## Flashing
Connect to the board's top USB-C port (native USB-Serial/JTAG, no external USB-serial chip) and upload as normal with the settings above.
