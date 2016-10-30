cmake_minimum_required(VERSION 3.6)

project(ungoliant)

set(CTPP_VERSION_MAJOR 0)
set(CTPP_VERSION_MINOR 1)
set(CTPP_VERSION_PATCH 0)

set(CTPP_VERSION         "${CTPP_VERSION_MAJOR}.${CTPP_VERSION_MINOR}.${CTPP_VERSION_PATCH}")
set(CTPP_IDENT           "ThatAintWorking")
set(CTPP_MASTER_SITE_URL "http://www.thataintworking.com/")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++03  -pthread")

set(SOURCE_FILES
        include/connection.hpp
        include/header.hpp
        include/mime_types.hpp
        include/reply.hpp
        include/request.hpp
        include/request_handler.hpp
        include/request_parser.hpp
        include/server.hpp
        src/connection.cpp
        src/main.cpp
        src/mime_types.cpp
        src/reply.cpp
        src/request_handler.cpp
        src/request_parser.cpp
        src/server.cpp)

include_directories(include)

add_subdirectory(lib/ctpp2-2.8.3)

link_libraries(boost_system boost_thread)

add_executable(ungoliant ${SOURCE_FILES})