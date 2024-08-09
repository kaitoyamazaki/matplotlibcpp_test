cmake_minimum_required(VERSION 3.10)
project(plt)
 
set(CMAKE_CXX_STANDARD 11)

include_directories(${CMAKE_SOURCE_DIR}/include ~/.matplotlibcpp/include)
 
set(SOURCE_FILE "main.cpp" CACHE STRING "Source file to compile")
add_executable(plt ${SOURCE_FILE})
 
# matplotlibcppで使うPythonとNumpyを探す
find_package(Python3 COMPONENTS Development NumPy)
target_include_directories(plt PRIVATE ${Python3_INCLUDE_DIRS} ${Python3_NumPy_INCLUDE_DIRS})
target_link_libraries(plt Python3::Python Python3::NumPy)