set(CMAKE_UNITY_BUILD true)
set(CMAKE_UNITY_BUILD_BATCH_SIZE 64)

file(GLOB_RECURSE sources CONFIGURE_DEPENDS
  "${CMAKE_CURRENT_SOURCE_DIR}/usblib/*.c"
  "${CMAKE_CURRENT_SOURCE_DIR}/usblib/*.cpp"
)

set_source_files_properties(${sources} PROPERTIES LANGUAGE CXX)

add_library(tm4c_usblib ${sources})
target_include_directories(tm4c_driverlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

target_precompile_headers(
  tm4c_usblib
  PUBLIC
  <stddef.h>
  <stdint.h>
  <stdbool.h>
  <string.h>
)