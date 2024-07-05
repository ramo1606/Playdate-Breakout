# Minimum CMake version required
cmake_minimum_required(VERSION 3.14)

# Project name and language
project(breakout_playdate C)

# Set C standard to C89/ANSI C
set(CMAKE_C_STANDARD 90)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

# Check for Playdate SDK path
if(NOT DEFINED ENV{PLAYDATE_SDK_PATH})
    message(FATAL_ERROR "Please set PLAYDATE_SDK_PATH environment variable to your Playdate SDK location.")
endif()
set(PLAYDATE_SDK_PATH $ENV{PLAYDATE_SDK_PATH})

# Include Playdate game support
include("${PLAYDATE_SDK_PATH}/C_API/buildsupport/playdate_game.cmake")

# Define source files
set(SOURCE_FILES
    Source/src/main.c
    Source/src/game.c
    Source/src/paddle.c
    Source/src/ball.c
    Source/src/brick.c
    Source/src/utils.c
)

# Define header files
set(HEADER_FILES
    Source/src/game.h
    Source/src/paddle.h
    Source/src/ball.h
    Source/src/brick.h
    Source/src/utils.h
)

# Create executable
add_executable(${PROJECT_NAME} ${SOURCE_FILES} ${HEADER_FILES})

# Link Playdate libraries
target_link_libraries(${PROJECT_NAME} PRIVATE ${PLAYDATE_LIBRARIES})

# Include Playdate headers
target_include_directories(${PROJECT_NAME} PRIVATE ${PLAYDATE_INCLUDE_PATHS})

# Set compile options
target_compile_options(${PROJECT_NAME} PRIVATE 
    ${PLAYDATE_COMPILE_OPTIONS}
    -Wall
    -Wextra
    -Wpedantic
)

# Set compile definitions
target_compile_definitions(${PROJECT_NAME} PRIVATE ${PLAYDATE_COMPILE_DEFINITIONS})

# Copy assets to output directory
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${CMAKE_SOURCE_DIR}/Source/assets $<TARGET_FILE_DIR:${PROJECT_NAME}>/assets
)

# Add tests subdirectory
add_subdirectory(Source/tests)