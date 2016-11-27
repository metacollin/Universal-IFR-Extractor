cmake_minimum_required(VERSION 2.8)

project("Universal IFR Extractor")

if(CMAKE_CXX_COMPILER_ID STREQUAL "AppleClang")
  if(CMAKE_CXX_COMPILER_VERSION VERSION_LESS 7.0)
    message(FATAL_ERROR "Need at least AppleClang 7.0 to compile.")
  endif()
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")
elseif(CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
  if(CMAKE_CXX_COMPILER_VERSION VERSION_LESS 3.4)
    message(FATAL_ERROR "Clang below version 3.4 will most likely not work. Please upgrade your compiler.")
  endif()
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")
else() # no GNU, no MSVC, no Clang
  message(WARNING "You are using an unsupported compiler. Compilation has only been tested with Clang.")
endif()

if(CMAKE_CXX_COMPILER_ID STREQUAL "Clang"
    OR CMAKE_CXX_COMPILER_ID STREQUAL "AppleClang")
  set(warning_options -Weverything
    -Wno-c++98-compat
    -Wno-padded
    -Wno-c++98-compat-pedantic
    -Wno-exit-time-destructors
    -Wno-missing-prototypes
    -Wno-weak-vtables
    -Wno-global-constructors
    -Wno-format-nonliteral
    -Wno-switch-enum
    -Wno-missing-noreturn
    -Wno-covered-switch-default
    )
endif()

add_executable(ifrextract UEFI.cpp EFI.CPP main.cpp)
