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

add_executable(textures src/Textures.cpp)
target_link_libraries(textures PRIVATE glad glfw3 opengl32)

set(SHADERS
	src/shaders/vertex.vs
	src/shaders/fragment.fs
	src/shaders/texture.vs
	src/shaders/texture.fs
)

set(RESOURCES
	src/resources/container.jpg
	src/resources/wall.jpg
)

foreach(_shader ${SHADERS})
    configure_file(
        ${PROJECT_SOURCE_DIR}/${_shader}
        ${PROJECT_BINARY_DIR}/${_shader}
        COPYONLY
    )
endforeach(_shader ${SHADERS})

foreach(_res ${RESOURCES})
    configure_file(
        ${PROJECT_SOURCE_DIR}/${_res}
        ${PROJECT_BINARY_DIR}/${_res}
        COPYONLY
    )
endforeach(_res ${RESOURCES})