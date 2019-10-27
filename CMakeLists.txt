cmake_minimum_required(VERSION 3.15)
project(learnopengl)

find_package(OpenGL REQUIRED)

add_subdirectory(dependencies/glad/)

include_directories(
	${PROJECT_SOURCE_DIR}/dependencies/
	${PROJECT_SOURCE_DIR}/dependencies/glfw-3.3/include
	${PROJECT_SOURCE_DIR}/dependencies/glm
	${PROJECT_SOURCE_DIR}/src
)
link_directories(${PROJECT_SOURCE_DIR}/dependencies/glfw-3.3/lib-vc2019/)

add_subdirectory(src/0_windows/)
add_subdirectory(src/1_triangles/)
add_subdirectory(src/2_shaders/)
add_subdirectory(src/3_textures/)
add_subdirectory(src/4_transformations/)
add_subdirectory(src/5_coordinates/)

set(RESOURCES
	src/resources/container.jpg
	src/resources/awesomeface.png
	src/resources/wall.jpg
)

foreach(_res ${RESOURCES})
    configure_file(
        ${PROJECT_SOURCE_DIR}/${_res}
        ${PROJECT_BINARY_DIR}/${_res}
        COPYONLY
    )
endforeach(_res ${RESOURCES})