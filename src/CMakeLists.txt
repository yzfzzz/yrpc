find_package(Protobuf REQUIRED)
set(PROTO_FILE rpcheader.proto)
protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS ${PROTO_FILE})

find_package(yaml-cpp REQUIRED)
aux_source_directory(. SRC_LIST)
# 生成一个库
add_library(yrpc ${SRC_LIST} ${PROTO_SRCS})

target_include_directories(yrpc PUBLIC 
    ${CMAKE_CURRENT_BINARY_DIR}
    ${PROTOBUF_INCLUDE_DIRS}
)

# muduo库是静态库
target_link_libraries(yrpc muduo_net muduo_base pthread glog zookeeper_mt yaml-cpp ${PROTOBUF_LIBRARIES})