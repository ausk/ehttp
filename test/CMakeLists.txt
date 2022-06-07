
cmake_minimum_required(VERSION 3.5)

add_executable(hello_server
    ${CMAKE_CURRENT_SOURCE_DIR}/hello_server.cpp
)
add_dependencies(hello_server ehttp)
link_libraries(${CMAKE_BINARY_DIR})
target_link_libraries(hello_server ehttp)
