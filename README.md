# Play HTTP aac Living stream

The demo plays a m3u downloaded from HTTP. 

## Compatibility

ESP32-ADF
https://www.olimex.com/Products/IoT/ESP32/ESP32-ADF/open-source-hardware

## Usage

### Prerequisites

Get ESP-ADF:
```bash
cd ~/
git clone --recursive https://github.com/espressif/esp-adf.git
cd esp-adf
git submodule update --init
export ADF_PATH=~/esp-adf
```

Set up ESP-IDF (required by ESP-ADF):
```bash
cd $ADF_PATH/esp-idf
./install.sh
. ./export.sh
```

### Build and Flash (CMake - Recommended)

Load the example:
```bash
git clone https://github.com/d3v1c3nv11/internet_radio_demo.git
cd internet_radio_demo
```

Configure the example:
```bash
idf.py menuconfig
```
- In the menuconfig interface, navigate to `Example Configuration` and fill in `WiFi SSID` and `WiFi Password`.

Build, flash and monitor:
```bash
idf.py build
idf.py flash monitor
```

### Build and Flash (Legacy Make)

Load and configure the example:
```bash
git clone https://github.com/d3v1c3nv11/internet_radio_demo.git
cd internet_radio_demo
make menuconfig
```
- In the menuconfig interface, navigate to `Example Configuration` and fill in `WiFi SSID` and `WiFi Password`.

Run the example:

```bash
make flash monitor
```

### Operation

Prepare the audio board:
- Connect speakers or headphones to the board.

The audio board will first connect to the Wi-Fi.
- Then the board will start playing automatically.
```bash
Use Touch buttons:
Volume: Vol- Vol+
Next station: <Play>
Presset station: <Set>
Loudness ON: <mode>
Loudness OFF: <record>
```

Note: Patch is required to es8388 driver in esp-adf to enable speakers. From project directory run
```bash
patch $ADF_PATH/components/audio_hal/driver/es8388/es8388.c < es8388_fix_speaker_volume.patch 
```

Graphical part of project is based on loboris/ESP32_TFT_library https://github.com/loboris/ESP32_TFT_library
