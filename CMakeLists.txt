cmake_minimum_required(VERSION 3.15)
project(learnopengl)

find_package(OpenGL REQUIRED)

add_subdirectory(dependencies/glad/)

include_directories(${PROJECT_SOURCE_DIR}/dependencies/glfw-3.3/include)
link_directories(${PROJECT_SOURCE_DIR}/dependencies/glfw-3.3/lib-vc2019/)

add_executable(windows src/Windows.cpp)
target_link_libraries(windows PRIVATE glad glfw3 opengl32)

add_executable(triangles src/Triangles.cpp)
target_link_libraries(triangles PRIVATE glad glfw3 opengl32)

add_executable(shaders src/Shaders.cpp)
target_link_libraries(shaders PRIVATE glad glfw3 opengl32)

set(SCRIPTS
	src/vertex.vs
	src/fragment.fs
)

foreach(_script ${SCRIPTS})
    configure_file(
        ${PROJECT_SOURCE_DIR}/${_script}
        ${PROJECT_BINARY_DIR}/${_script}
        COPYONLY
    )
endforeach(_script ${SCRIPTS})