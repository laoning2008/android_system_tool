project(aidl CXX)   

set(LIB_SOURCES String8.cpp String16.cpp)

add_library(libutils ${LIB_SOURCES})
target_include_directories(libutils PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)             
