cmake_minimum_required(VERSION 3.2)

# Just change this name. A static library will be generated
project(protos-ch)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# Generic simple stuff to compile all the protos of the folder using C++
find_package(Protobuf REQUIRED)
include_directories(${PROTOBUF_INCLUDE_DIRS})

# find files
file(GLOB PROTO_FILES "*.proto")

# generate intermediate .pb.cc and .pb.h file
PROTOBUF_GENERATE_CPP(PROTO_SRCS PROTO_HDRS ${PROTO_FILES})

# complile the project
add_library(${PROJECT_NAME} STATIC ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(${PROJECT_NAME} ${PROTOBUF_LIBRARIES})
