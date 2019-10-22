cmake_minimum_required(VERSION 3.15)
project(learnopengl)

find_package(OpenGL REQUIRED)

add_subdirectory(dependencies/glad/)

include_directories(${PROJECT_SOURCE_DIR}/dependencies/glfw-3.3/include)
link_directories(${PROJECT_SOURCE_DIR}/dependencies/glfw-3.3/lib-vc2019/)

add_executable(triangles src/Triangles.cpp)
target_link_libraries(triangles PRIVATE glad glfw3 opengl32)
