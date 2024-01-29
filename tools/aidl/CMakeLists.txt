project(aidl CXX)   

# flex -o aidl_language_l.cpp aidl_language_l.ll
# bison -d  -o aidl_language_y.cpp aidl_language_y.yy


set(COMMON_SOURCES aidl_language_l.cpp aidl_language_y.cpp location.hh position.hh aidl_language_y.hpp aidl_language.cpp aidl_language.h
    aidl.cpp aidl.h code_writer.cpp code_writer.h import_resolver.cpp import_resolver.h io_delegate.cpp io_delegate.h
    line_reader.cpp line_reader.h logging.h options.cpp options.h os.h type_namespace.cpp type_namespace.h
    type_cpp.cpp type_cpp.h type_java.cpp type_java.h ast_cpp.cpp ast_cpp.h generate_cpp.cpp generate_cpp.h
    ast_java.cpp ast_java.h generate_java_binder.cpp generate_java.cpp generate_java.h)

set(CPP_SOURCES main_cpp.cpp)

set(JAVA_SOURCES main_java.cpp)

add_executable(aidl_cpp ${COMMON_SOURCES} ${CPP_SOURCES})
add_executable(aidl_java ${COMMON_SOURCES} ${JAVA_SOURCES})

target_include_directories(aidl_cpp PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(aidl_java PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})

target_link_libraries(aidl_cpp PRIVATE base libutils)
target_link_libraries(aidl_java PRIVATE base libutils)

