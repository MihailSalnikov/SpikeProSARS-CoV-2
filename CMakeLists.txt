cmake_minimum_required(VERSION 3.0.0)
project(SpikePro VERSION 0.1.0)

include(CTest)
enable_testing()

add_subdirectory(edlib)

add_executable(${PROJECT_NAME} SpikePro.cpp CSVparser.cpp CSVparser.hpp)

target_include_directories(
    edlib PUBLIC
    "${PROJECT_BINARY_DIR}"
    "${PROJECT_SOURCE_DIR}/edlib/include"
    "${PROJECT_SOURCE_DIR}/edlib/src"
)
target_link_libraries(${PROJECT_NAME} PUBLIC edlib)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
