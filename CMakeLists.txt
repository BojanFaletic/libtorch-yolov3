cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(yolo-app)


set(CMAKE_CXX_COMPILER "clang++")
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)


list(APPEND CMAKE_PREFIX_PATH "libtorch/share/cmake/Torch")

find_package(OpenCV 4.5 REQUIRED)
find_package(Torch REQUIRED)

include_directories( ${OpenCV_INCLUDE_DIRS} )

find_package(Torch REQUIRED)

aux_source_directory(. DIR_SRCS)

add_executable(yolo-app ${DIR_SRCS})
target_link_libraries(yolo-app ${OpenCV_LIBS})
target_link_libraries(yolo-app ${TORCH_LIBRARIES})