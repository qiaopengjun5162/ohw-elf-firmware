cmake_minimum_required(VERSION 3.20.0)

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(ohw)

zephyr_get_compile_options_for_lang_as_string(C options)

# get_cmake_property(_variableNames VARIABLES) foreach (_variableName
# ${_variableNames}) message(STATUS "${_variableName}=${${_variableName}}")
# endforeach()

file(
  GENERATE
  OUTPUT "${CMAKE_CURRENT_BINARY_DIR}/compile_options.txt"
  CONTENT "${options}")
string(
  REGEX
  REPLACE
    "\\$<SEMICOLON>\\$<TARGET_PROPERTY:compiler,imacros>\\$<SEMICOLON>[^$]+/autoconf\\.h"
    ""
    options
    "${options}")
separate_arguments(options_list UNIX_COMMAND "${options}")

add_subdirectory(temp)
add_subdirectory(wallets/psa)

target_sources(app PRIVATE
  src/main.c
  src/port/uart.c
  src/storage/storage.c)

target_compile_options(temp PRIVATE ${options_list})
target_compile_options(crypto PRIVATE ${options_list})

target_link_libraries(crypto PRIVATE zephyr_interface mbedTLS)

target_include_directories(app PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/wallets)

target_include_directories(app PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/temp)

target_include_directories(app PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src)

rust_cargo_application()

target_link_libraries(app PRIVATE crypto temp)
