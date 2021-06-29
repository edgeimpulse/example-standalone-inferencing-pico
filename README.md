# Edge Impulse Stand-alone Inferencing (Raspberry Pi Pico)

This builds an exported impulse to a .uf2 file that can be dragged and dropped to a Raspberry Pi Pico. Based on the Arducam Pico4ML Magic Wand Example: https://github.com/ArduCAM/Pico4ML-Magic-Wand/ 

## Build & Flash

### Pre-requisites

* Raspberry Pi Pico
* Edge Impulse CLI
* GCC
* CMake
* Pico SDK:
   ```bash
   git clone -b master https://github.com/raspberrypi/pico-sdk.git
   cd pico-sdk
   git submodule update --init
   export PATH="<Path to Pico SDK>:$PATH"
   ```

### Get the Edge Impulse SDK

Unzip the deployed `C++ library` from your Edge Impulse project and copy only the folders to the root directory of this repository:

   ```
   example-standalone-inferencing-pico/
   ├─ edge-impulse-sdk
   ├─ model-parameters
   ├─ source
   ├─ tflite-model
   ├─ CMakeLists.txt
   ├─ LICENSE
   ├─ pico_sdk_import.cmake
   ├─ README.md
   ```

### Build

1. Get the submodules:
   ```bash
   git submodule update --init
   ```
1. Create the `build` folder:
   ```bash
   mkdir build && cd build
   ```
1. Compile:
   ```bash
   cmake .. && cmake --build . --parallel
   ```

### Flash

Connect the *Pico4ML* to the *PC* using the *micro-USB* cable and make sure to force it to *USB Mass Storage Mode* by pressing and holding the **BOOTSEL** button.

Drag the [build/pico_standalone.uf2](build/pico_standalone.uf2) file to the *RPI-RP2* disk!
