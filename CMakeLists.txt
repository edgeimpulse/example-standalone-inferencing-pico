cmake_minimum_required(VERSION 3.13.1)

set(MODEL_FOLDER source)
set(EI_SDK_FOLDER source/edge-impulse-sdk)

include(pico_sdk_import.cmake)

project(app C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 11)

pico_sdk_init()

add_executable(app
  source/main.cpp
  )

add_subdirectory(source)
target_link_libraries(app pico_stdlib)

# enable usb output, disable uart output
pico_enable_stdio_usb(app 1)
pico_enable_stdio_uart(app 0)

# add all sources to the project
target_sources(app PRIVATE ${SOURCE_FILES})

pico_add_extra_outputs(app)
