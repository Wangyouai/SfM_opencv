cmake_minimum_required(VERSION 3.19)
project(SfM_test)

set(CMAKE_CXX_STANDARD 14)
set(OpenCV_DIR "/home/wya/Project/3rdparty/install/OpenCV/lib/cmake/opencv4")
set(VTK_DIR "/home/wya/Project/3rdparty/install/VTK/lib/cmake/vtk-9.0")

find_package(OpenCV 4.5.2 REQUIRED)
find_package(VTK REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS})
include_directories(${VTK_INCLUDE_DIRS})

if(Ceres_FOUND)
    add_definitions("-DCERES_FOUND=1")
    list(APPEND LIBMV_LIGHT_LIBS simple_pipeline)
    if(Ceres_VERSION VERSION_LESS 2.0.0)
        list(APPEND LIBMV_LIGHT_INCLUDES "${CERES_INCLUDE_DIRS}")
    endif()
else()
    add_definitions("-DCERES_FOUND=0")
    message(STATUS "CERES support is disabled. Ceres Solver for reconstruction API is required.")
endif()

add_executable(SfM_test main.cpp)
target_link_libraries(SfM_test ${OpenCV_LIBS} ${VTK_LIBS})
