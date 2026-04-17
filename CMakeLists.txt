set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/yrpc/lib)
include_directories(${PROJECT_SOURCE_DIR}/yrpc/src/include)
link_directories(${PROJECT_SOURCE_DIR}/yrpc/lib)
add_subdirectory(src)