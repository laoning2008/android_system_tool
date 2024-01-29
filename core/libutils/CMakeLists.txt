project(aidl CXX)   

set(LIB_SOURCES String8.cpp String16.cpp include/utils/String8.h include/utils/String16.h
    SharedBuffer.cpp SharedBuffer.h)

add_library(libutils ${LIB_SOURCES})
target_include_directories(libutils PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)             
