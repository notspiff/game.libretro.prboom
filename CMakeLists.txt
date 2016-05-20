project(game.libretro.prboom)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(kodi REQUIRED)
find_package(libretro-prboom REQUIRED)

set(PRBOOM_CUSTOM_BINARY ${PRBOOM_LIB}
                         ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX})

build_addon(game.libretro.prboom PRBOOM "")
