cmake_minimum_required(VERSION 3.12)

project(testing_test_all_op_resolver_test C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

add_executable(testing_test_all_op_resolver_test "")

target_include_directories(testing_test_all_op_resolver_test
  PRIVATE
  ${CMAKE_CURRENT_LIST_DIR}/../../tests/testing_test_all_op_resolver_test
)

set_target_properties(
  testing_test_all_op_resolver_test
  PROPERTIES
  COMPILE_FLAGS -Os
  COMPILE_FLAGS -fno-rtti
  COMPILE_FLAGS -fno-exceptions
  COMPILE_FLAGS -fno-threadsafe-statics
  COMPILE_FLAGS -nostdlib
)

pico_enable_stdio_usb(testing_test_all_op_resolver_test 1)
pico_enable_stdio_uart(testing_test_all_op_resolver_test 0)

target_sources(testing_test_all_op_resolver_test
  PRIVATE
  ${CMAKE_CURRENT_LIST_DIR}/../../tests/testing_test_all_op_resolver_test/test_all_op_resolver_test.cpp

)

target_link_libraries(
  testing_test_all_op_resolver_test
  pico-tflmicro
  pico-tflmicro_test
)

pico_add_extra_outputs(testing_test_all_op_resolver_test)
