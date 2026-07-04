cmake_minimum_required(VERSION 3.3)
project("Better Fangame")

set(CMAKE_C_STANDARD 99)

include(FetchContent)
FetchContent_Declare(
    glfw
    GIT_REPOSITORY https://github.com/glfw/glfw
    GIT_TAG 3.4
    FIND_PACKAGE_ARGS
)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(glfw)

add_library(glad
    external/glad/src/glad.c
    external/glad/include/glad/glad.h
)
target_include_directories(glad PUBLIC external/glad/include)

add_executable(Better_Fangame src/main.c)
set_target_properties(Better_Fangame PROPERTIES OUTPUT_NAME "Better Fangame")

target_link_libraries(Better_Fangame  PRIVATE glad glfw)
