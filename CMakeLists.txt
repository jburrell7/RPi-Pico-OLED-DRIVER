# Set minimum required version of CMake
cmake_minimum_required(VERSION 3.12)

# Include build functions from Pico SDK
include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

# Set the name of the project (as PROJECT_NAME) and C/C++ standards
project(picoOled C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Creates a pico-sdk subdirectory in our project for the libraries
pico_sdk_init()

# List source files for the pro0ject here
add_executable(oledTest
    oledTest.c
    picoOled.c
)

# Link to the library functions (stdlib, etc)
target_link_libraries(oledTest
    pico_stdlib hardware_i2c
    )

pico_enable_stdio_usb(oledTest 1)
pico_enable_stdio_uart(oledTest 0)

# Create the output file
pico_add_extra_outputs(oledTest)

