project(gameclient.prboom)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)

include(ExternalProject)

externalproject_add(prboom
                    GIT_REPOSITORY https://github.com/libretro/libretro-prboom
                    GIT_TAG bfe7c22
                    PREFIX prboom
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make
                    BUILD_IN_SOURCE 1)

set(PRBOOM_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/prboom/src/prboom/prboom_libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                        prboom_libretro${CMAKE_SHARED_LIBRARY_SUFFIX} prboom)

build_addon(gameclient.prboom PRBOOM DEPLIBS)
add_dependencies(gameclient.prboom prboom)
