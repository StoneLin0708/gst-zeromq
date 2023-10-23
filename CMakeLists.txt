cmake_minimum_required(VERSION 3.16)

project(gst-zeromq VERSION 1.0.0 LANGUAGES C)

SET(CMAKE_MODULE_PATH
    ${CMAKE_CURRENT_SOURCE_DIR}/cmake
    ${CMAKE_MODULE_PATH}
)

find_package(PkgConfig REQUIRED)
pkg_search_module(gstreamer REQUIRED IMPORTED_TARGET gstreamer-1.0>=1.4)
pkg_search_module(gstreamer-controller REQUIRED IMPORTED_TARGET gstreamer-controller-1.0>=1.4)
pkg_search_module(gstreamer-base REQUIRED IMPORTED_TARGET gstreamer-base-1.0>=1.4)

find_package(ZeroMQ REQUIRED)
add_library(ZeroMQ::ZeroMQ INTERFACE IMPORTED)
target_include_directories(ZeroMQ::ZeroMQ INTERFACE ${ZeroMQ_INCLUDE_DIRS})
target_link_libraries(ZeroMQ::ZeroMQ INTERFACE ${ZeroMQ_STATIC_LIBRARY})

add_subdirectory(src/zeromq)