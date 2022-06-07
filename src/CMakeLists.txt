cmake_minimum_required(VERSION 3.5)

add_library(ehttp
    #STATIC
    SHARED
    epoll_socket.cpp
    http_server.cpp
    sim_parser.cpp
    simple_log.cpp
    threadpool.cpp
    http_parser.cpp
    multipart_parser.cpp
    simple_config.cpp
    string_utils.cpp

    deps/json-cpp/json_reader.cpp
    deps/json-cpp/json_value.cpp
    deps/json-cpp/json_writer.cpp
)

target_link_libraries(ehttp pthread m)
