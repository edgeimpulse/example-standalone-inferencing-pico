# Edge Impulse Example: stand-alone inferencing (Raspberry Pi Pico)

This repository runs an exported impulse on the Raspberry Pi Pico / RP2040. See the documentation at [Running your impulse locally](https://docs.edgeimpulse.com/docs/running-your-impulse-locally-1). This repository is based off of the [Arducam Pico4ML Magic Wand Example](https://github.com/ArduCAM/Pico4ML-Magic-Wand/).

## Requirements

### Hardware

* [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/).

### Software

* [Edge Impulse CLI](https://docs.edgeimpulse.com/docs/cli-installation).
* [GNU ARM Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads).
* [CMake](https://cmake.org/install/).
* Rasperry Pi Pico SDK:
   ```bash
   git clone -b master https://github.com/raspberrypi/pico-sdk.git
   cd pico-sdk
   git submodule update --init
   export PATH="<Path to Pico SDK>"
   ```

## Building the application

### Get the Edge Impulse SDK

Unzip the deployed `C++ library` from your Edge Impulse project and copy to the source directory of this repository:

   ```
   example-standalone-inferencing-pico/
   ├─ source
   ├─- model-parameters
   ├─- edge-impulse-sdk
   ├─- tflite-model
   ├─- CMakeLists.txt
   ├─ .gitignore
   ├─ LICENSE
   ├─ README.md
   └─ pico_sdk_import.cmake
   ```

### Compile

1. Create the `build` folder:
   ```bash
   mkdir build && cd build
   ```
1. Compile:
   ```bash
   cmake ..
   clear && make -j4
   ```

### Flash

Connect the Raspberry Pi Pico to your computer using a micro-USB cable while pressing and holding the **BOOTSEL** button.

Drag and drop the `build/pico_standalone.uf2` file to the **RPI-RP2** disk in your file explorer.

### Serial connection

Use screen, minicom or Serial monitor in Arduino IDE to set up a serial connection over USB. The following UART settings are used: 115200 baud, 8N1.
