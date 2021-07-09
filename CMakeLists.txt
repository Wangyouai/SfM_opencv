cmake_minimum_required(VERSION 3.19)
project(SfM_test)

set(CMAKE_CXX_STANDARD 14)
set(OpenCV_DIR "/home/wya/Project/3rdparty/install/OpenCV/lib/cmake/opencv4")
set(VTK_DIR "/home/wya/Project/3rdparty/install/VTK/lib/cmake/vtk-9.0")

find_package(OpenCV 4.5.2 REQUIRED)
find_package(VTK REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS})
include_directories(${VTK_INCLUDE_DIRS})

add_executable(SfM_test main.cpp)
target_link_libraries(SfM_test ${OpenCV_LIBS} ${VTK_LIBS})