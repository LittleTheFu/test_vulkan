cmake_minimum_required(VERSION 3.16)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

project (test_vulkan)

add_subdirectory(${PROJECT_SOURCE_DIR}/third/glfw/)
include_directories(${PROJECT_SOURCE_DIR}/third/glfw/include)

add_subdirectory(${PROJECT_SOURCE_DIR}/third/glm/)
include_directories(${PROJECT_SOURCE_DIR}/third/glm/glm)

include_directories(${PROJECT_SOURCE_DIR}/third/vulkan/include)

include_directories(${PROJECT_SOURCE_DIR}/third/stb_image/include)



add_executable(test_vulkan main.cpp)

target_link_libraries(test_vulkan glfw)
target_link_libraries(test_vulkan glm)
target_link_libraries(test_vulkan ${PROJECT_SOURCE_DIR}/third/vulkan/Lib/vulkan-1.lib)

# 创建 debug 目录
file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/Debug)

# set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR}/install CACHE PATH "Install path prefix, prepended onto install directories." FORCE)
# 复制 shaders 目录到 build/debug 目录
file(COPY ${CMAKE_SOURCE_DIR}/shaders DESTINATION ${CMAKE_BINARY_DIR}/Debug)
file(COPY ${CMAKE_SOURCE_DIR}/textures DESTINATION ${CMAKE_BINARY_DIR}/Debug)