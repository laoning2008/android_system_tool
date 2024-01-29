project(base CXX)   

set(LIB_SOURCES_COMMON file.cpp logging.cpp parsenetaddress.cpp  quick_exit.cpp
    stringprintf.cpp strings.cpp)# properties.cpp

set(LIB_SOURCES_UNIX errors_unix.cpp)

set(LIB_SOURCES_WINDOWS errors_windows.cpp utf8.cpp)

set(LIB_SOURCES_TEST endian_test errors_test.cpp file_test.cpp logging_test.cpp
     parsedouble_test.cpp parseint_test.cpp parsenetaddress_test.cpp properties_test.cpp
     quick_exit_test.cpp stringprintf_test.cpp strings_test.cpp test_main.cpp test_utils.cpp utf8_test.cpp)

file(GLOB_RECURSE LIB_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/include *.h)

IF (WIN32)
    set(LIB_SOURCES ${LIB_SOURCES_COMMON} ${LIB_SOURCES_WINDOWS} ${LIB_HEADER})
ELSEIF (APPLE)
    set(LIB_SOURCES ${LIB_SOURCES_COMMON} ${LIB_SOURCES_UNIX} ${LIB_HEADER})
ELSEIF (UNIX)
    set(LIB_SOURCES ${LIB_SOURCES_COMMON} ${LIB_SOURCES_UNIX} ${LIB_HEADER})
ENDIF ()

add_library(base ${LIB_SOURCES})
target_include_directories(base PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)             
