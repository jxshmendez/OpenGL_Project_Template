cmake_minimum_required(VERSION 3.10)
project(open_gl_project C CXX)  

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)

include_directories(${CMAKE_SOURCE_DIR}/include)

find_package(OpenGL REQUIRED)
find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

add_library(glad STATIC src/glad.c)
target_include_directories(glad PUBLIC ${CMAKE_SOURCE_DIR}/include)


add_executable(open_gl_project src/main.cpp)

target_link_libraries(open_gl_project
    glad
    ${GLFW_LIBRARIES}
    OpenGL::GL
    dl
    m
)
