# USING CMAKE FEATURES >= VERSION 3.10
cmake_minimum_required(VERSION 3.10)

# BASE IS PROJECT NAME
project(base) 

# ADD RES, INC, LIB, SRC AND TEST (OPTIONAL) TO BUILD FOLDER
add_subdirectory(src)
# file(COPY ${CMAKE_SOURCE_DIR}/res/ DESTINATION ${CMAKE_BINARY_DIR}/res/)
# add_subdirectory(lib)
# add_subdirectory(inc)
option(BUILD_TEST "Build tests or not" OFF) # ON?
if(BUILD_TEST)
    message(STATUS "Bulding test ...")
    add_subdirectory(test)
endif()

# MAKING BASE.EXE IN BUILD FOLDER
add_executable(base
    src/main.cpp
)

# CHECK PACKAGES ARE INSTALLED OR NOT
find_package(SDL2 REQUIRED)
# find_package(SDL2_image REQUIRED)
# find_package(SDL2_ttf REQUIRED)
# find_package(SDL2_sound REQUIRED)
# find_package(SDL2_net REQUIRED)
# find_package(SDL2_mixer REQUIRED)
# find_package(SDL2_gfx REQUIRED)

# PUBLIC HEADER FILES IN THE MAIN SOURCE CODE. THUS, MAIN.CPP CAN USE SDL.H, SDL_IMAGE.H, ...
target_include_directories(base PUBLIC
    # lib
    # inc
    ${SDL2_INCLUDE_DIRS}
    # ${SDL2IMAGE_INCLUDE_DIRS}
    # ${SDL2TTF_INCLUDE_DIRS}
    # ${SDL2SOUND_INCLUDE_DIRS}
    # ${SDL2NET_INCLUDE_DIRS}
    # ${SDL2MIXER_INCLUDE_DIRS}
    # ${SDL2GFX_INCLUDE_DIRS}
)

# LINKING BASE.EXE WITH LIBRARY. THUS, BASE.EXE CAN OPEN IMAGE, PLAY VIDEO, LOAD FONT, ...
target_link_libraries(base PUBLIC 
    SDL2
    # SDL2_image
    # SDL2_ttf
    # SDL2_sound
    # SDL2_net
    # SDL2_mixer
    # SDL2_gfx
)