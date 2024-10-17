cmake_minimum_required(VERSION 3.5)

project(libwvad)

aux_source_directory(src SOURCES)
aux_source_directory(src/vad VAD)
aux_source_directory(src/signal_processing SIGNAL)

set(CMAKE_C_FLAGS "-std=c11")

add_library(wvad STATIC ${SOURCES} ${VAD} ${SIGNAL})

target_include_directories(wvad
    PUBLIC
    include
)

set_property(TARGET wvad PROPERTY POSITION_INDEPENDENT_CODE 1)
install(TARGETS wvad DESTINATION lib)
