cmake_minimum_required(VERSION 3.10)

project(base)

file(COPY ${CMAKE_SOURCE_DIR}/res/ DESTINATION ${CMAKE_BINARY_DIR}/res/)

add_subdirectory(inc)
add_subdirectory(lib)
add_subdirectory(src)

option(BUILD_TEST "Build tests or not" OFF)
if(BUILD_TEST)
    message(STATUS "Bulding test ...")
    add_subdirectory(test)
endif()

add_executable(base
    src/main.cpp
)

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_ttf REQUIRED)
find_package(SDL2_sound REQUIRED)
find_package(SDL2_net REQUIRED)
find_package(SDL2_mixer REQUIRED)
# find_package(SDL2_gfx REQUIRED)

target_include_directories(base PUBLIC
    lib
    inc
    ${SDL2_INCLUDE_DIRS}
    ${SDL2IMAGE_INCLUDE_DIRS}
    ${SDL2TTF_INCLUDE_DIRS}
    ${SDL2SOUND_INCLUDE_DIRS}
    ${SDL2NET_INCLUDE_DIRS}
    ${SDL2MIXER_INCLUDE_DIRS}
    ${SDL2GFX_INCLUDE_DIRS}
)

target_link_libraries(base PUBLIC 
    SDL2
    SDL2_image
    SDL2_ttf
    SDL2_sound
    SDL2_net
    SDL2_mixer
    SDL2_gfx
)