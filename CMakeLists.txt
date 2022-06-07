cmake_minimum_required(VERSION 3.5)
project(ehttp VERSION 1.6)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_BUILD_TYPE Release)

include_directories(
    ${PROJECT_SOURCE_DIR}/include/
    ${PROJECT_SOURCE_DIR}/include/ehttp
    ${PROJECT_SOURCE_DIR}/src
    ${PROJECT_SOURCE_DIR}/src/deps/json-cpp/
)

add_subdirectory(src)
add_subdirectory(test)


