cmake_minimum_required(VERSION 3.10)

# 项目名称
project(main)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 源文件列表
file(GLOB SOURCES "*.cpp")

# 设置编译标志
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

# 添加可执行文件
add_executable(${PROJECT_NAME} ${SOURCES})

# 链接库
target_link_libraries(${PROJECT_NAME} m)

# 设置输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE})

# 清理目标
add_custom_target(custom_clean
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${PROJECT_NAME}
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_BINARY_DIR}/*.o
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_BINARY_DIR}/*.tga
)

