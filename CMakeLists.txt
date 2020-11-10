cmake_minimum_required (VERSION 3.5)
# The version number.
set (CAVEMAN_VERSION_MAJOR 1)
set (CAVEMAN_VERSION_MINOR 0)

#Declaration du projet
project(CAVEMAN)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
#set(CMAKE_CXX_FLAGS "-std=gnu++0x")
set(CMAKE_CXX_FLAGS "-std=c++0x")
set(EXECUTABLE_OUTPUT_PATH bin/${CMAKE_BUILD_TYPE})

#Inclusion de SDL2
include_directories(/usr/include/SDL2)
link_directories(/usr/lib/x86_64-linux-gnu)


# variables
set(EXE_NAME Caveman)

#Génération de la liste des fichiers sources
file(
        GLOB_RECURSE
        source_files
        src/*
)

#Génération de la liste des fichiers headers
file(
        GLOB_RECURSE
        headers_files
        headers/*
)

# declaration executable
add_executable(
${EXE_NAME}
${headers_files}
${source_files}
)

#Configuration de l'édition de liens
target_link_libraries(
        ${EXE_NAME}
        SDL2
        SDL2_image
	SDL2_mixer
	z
)
