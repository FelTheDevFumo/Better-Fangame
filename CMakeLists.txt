cmake_minimum_required(VERSION 3.3)
project("Better Fangame")

set(CMAKE_C_STANDARD 99)

# GLFW
add_subdirectory(external/glfw)

# GLAD
add_library(glad external/glad/src/glad.c)
target_include_directories(glad PUBLIC external/glad/include)

# Main executable
add_executable("better_fangame" src/main.c)
set_target_properties(better_fangame PROPERTIES OUTPUT_NAME "Better Fangame")

target_include_directories(better_fangame PRIVATE
    external/glad/include
    external/glfw/include
)

target_link_libraries(better_fangame PRIVATE
    glad
    glfw
)
