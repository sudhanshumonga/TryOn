cmake_minimum_required(VERSION 2.8.4)

PROJECT(TryOn)

include(./lib/dlib/dlib/cmake)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "lib/")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "lib/")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "bin/")
find_package(OpenCV)
if (OpenCV_FOUND)
    include_directories(${OpenCV_INCLUDE_DIRS})

    ADD_EXECUTABLE(tryon tryon.cpp)
    TARGET_LINK_LIBRARIES(tryon dlib ${OpenCV_LIBS} )
else ()
    # Tell CMake to compile a program.  We do this with the ADD_EXECUTABLE()
    # statement which takes the name of the output executable and then a list of
    # .cpp files to compile.  Here each example consists of only one .cpp file but
    # in general you will make programs that const of many .cpp files.
    ADD_EXECUTABLE(tryon tryon.cpp)
    # Then we tell it to link with dlib.
    TARGET_LINK_LIBRARIES(tryon dlib)
endif ()