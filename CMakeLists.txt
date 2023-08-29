cmake_minimum_required(VERSION 2.6)
project(MergeSortCUDA)
find_package(CUDA)

message(STATUS "CMAKE_MODULE_PATH is " ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

cuda_add_library(MergeSortKernel STATIC mergeSort.cu bitonic.cu)

add_executable(MergeSort main.cpp mergeSort_host.cpp mergeSort_validate.cpp)
target_link_libraries(MergeSort MergeSortKernel)