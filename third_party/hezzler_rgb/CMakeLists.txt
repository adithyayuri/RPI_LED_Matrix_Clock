cmake_minimum_required(VERSION 2.8)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(${PROJECT_SOURCE_DIR}/third_party/hezzler_rgb/rpi-rgb-led-matrix/lib)
include_directories(${PROJECT_SOURCE_DIR}/third_party/hezzler_rgb/rpi-rgb-led-matrix/include)

file(GLOB_RECURSE RGB_SRC_FILES ${PROJECT_SOURCE_DIR}/third_party/hezzler_rgb/rpi-rgb-led-matrix/lib/*.c*)
file(GLOB_RECURSE RGB_SRC_HEADER_FILES ${PROJECT_SOURCE_DIR}/third_party/hezzler_rgb/rpi-rgb-led-matrix/lib/*.h*)
file(GLOB_RECURSE RGB_HEADER_FILES ${PROJECT_SOURCE_DIR}/third_party/hezzler_rgb/rpi-rgb-led-matrix/include/*.h*)

set(HZELLER_RGB_SRCS ${RGB_SRC_FILES} ${RGB_SRC_HEADER_FILES} ${RGB_HEADER_FILES})

set(LIB_TYPE STATIC)

add_library (hzeller_rgb ${LIB_TYPE} ${HZELLER_RGB_SRCS})
target_link_libraries (hzeller_rgb -lrt -lm -lpthread)
set_target_properties(hzeller_rgb PROPERTIES LINKER_LANGUAGE CXX)

