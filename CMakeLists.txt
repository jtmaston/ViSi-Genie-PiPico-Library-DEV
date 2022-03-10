cmake_minimum_required(VERSION 3.8)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico-sdk/pico_sdk_init.cmake)

project(GeniePico VERSION 0.1 LANGUAGES CXX C)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# rest of your project
add_library(PicoGenie STATIC
    ${PROJECT_SOURCE_DIR}/src/geniePicoDev.cpp
)

target_link_libraries(PicoGenie pico_stdlib)

set_target_properties(PicoGenie PROPERTIES
    PUBLIC_HEADER "${PROJECT_SOURCE_DIR}/src/geniePicoDEV.h"
)
target_include_directories(PicoGenie PRIVATE ${PROJECT_SOURCE_DIR}/src)
#target_compile_features(PicoGenie
#    PUBLIC
#    cxx_attributes
#    cxx_defaulted_functions
#    cxx_deleted_functions
#    cxx_final
#)

pico_add_extra_outputs(GenieTest)