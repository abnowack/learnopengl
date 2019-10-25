add_executable(transformations Transformations.cpp)
target_link_libraries(transformations PRIVATE glad glfw3 opengl32)

FILE(GLOB SHADERS
	"*.fs"
	"*.vs"
)

file(COPY ${SHADERS} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
