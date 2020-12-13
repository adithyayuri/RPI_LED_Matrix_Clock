cmake_minimum_required(VERSION 2.8) 
set(CMAKE_CXX_STANDARD 14) 
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set project name
project(rpi_clock)

# Add Hezzler RGB Library directory
add_subdirectory(${PROJECT_SOURCE_DIR}/third_party/hezzler_rgb/)
# Include Hezzler RGB Library
set(HZELLER_RGB_DIR ${PROJECT_SOURCE_DIR}/third_party/hezzler_rgb/rpi-rgb-led-matrix/include/)

include_directories(${PROJECT_SOURCE_DIR}/source)

file(GLOB_RECURSE SRC_FILES ${PROJECT_SOURCE_DIR}/source/*.c*)
file(GLOB_RECURSE HEADER_FILES ${PROJECT_SOURCE_DIR}/source/*.h)

add_executable(rpi_clock ${SRC_FILES} ${HEADER_FILES})

include_directories(${HZELLER_RGB_DIR})

set_target_properties(rpi_clock PROPERTIES LINKER_LANGUAGE CXX)
target_link_libraries(rpi_clock hzeller_rgb)
ADD_DEPENDENCIES(rpi_clock hzeller_rgb)


