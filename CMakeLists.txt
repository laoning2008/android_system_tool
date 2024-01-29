cmake_minimum_required(VERSION 3.25)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(system CXX)

#CPM
include(${CMAKE_CURRENT_SOURCE_DIR}/cmake/CPM.cmake)

#gtest
# CPMAddPackage(NAME GRPC GITHUB_REPOSITORY google/googletest GIT_TAG v1.14.0)             


include_directories(${CMAKE_CURRENT_SOURCE_DIR}/core/libutils/include)

#base
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/core/base)

#libutils
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/core/libutils)

#aidl
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/tools/aidl)


