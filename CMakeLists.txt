cmake_minimum_required(VERSION 3.20)
project(gbemu C)

set(CMAKE_C_STANDARD 99)  # use C99 for now

# Set build type if not specified
if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Debug)
endif()

# Find packages
find_package(SDL2 CONFIG REQUIRED)
find_package(SDL2_ttf CONFIG REQUIRED)  
find_package(check CONFIG REQUIRED)

# Add subdirectories
add_subdirectory(lib)
add_subdirectory(gbemu)
add_subdirectory(tests)

# Enable testing
enable_testing()
add_test(NAME check_gbe COMMAND check_gbe)