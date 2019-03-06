cmake_minimum_required(VERSION 3.8)
project(CoreWatcher C CXX)

SET(CMAKE_COLOR_MAKEFILE ON)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY Bin)

set(exe ${PROJECT_NAME})

add_executable (${PROJECT_NAME}
    Sources/main.cpp Sources/FileMonitor.cpp
)

set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 17)
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD_REQUIRED ON)
set_property(TARGET ${PROJECT_NAME} PROPERTY CMAKE_CXX_EXTENSIONS OFF)

TARGET_LINK_LIBRARIES(${PROJECT_NAME} stdc++ stdc++fs)

if (CMAKE_SIZEOF_VOID_P EQUAL 8)
    add_compile_definitions(PLATFORM=64)
else (CMAKE_SIZEOF_VOID_P EQUAL 8) 
    add_compile_definitions(PLATFORM=32)
endif (CMAKE_SIZEOF_VOID_P EQUAL 8)
