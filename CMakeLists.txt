cmake_minimum_required(VERSION 3.1)
find_package(Protobuf REQUIRED)
include_directories(${PROTOBUF_INCLUDE_DIRS})

file(GLOB PROTO_FILES "*.proto")
PROTOBUF_GENERATE_CPP(PROTO_SRCS PROTO_HDRS ${PROTO_FILES})
add_library(protos-ch STATIC ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(protos-ch ${PROTOBUF_LIBRARIES})
