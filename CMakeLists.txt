cmake_minimum_required(VERSION 3.29)

if (NOT DEFINED CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 17)
endif()

set(CMAKE_C_EXTENSIONS OFF)

project(
  libxcrypt
  VERSION 4.5.0
  DESCRIPTION ""
  LANGUAGES C)

set(CMAKE_C_VISIBILITY_PRESET hidden)

add_subdirectory(lib)