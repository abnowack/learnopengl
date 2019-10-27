add_executable(camera Camera.cpp)
target_link_libraries(camera PRIVATE glad glfw3 opengl32)

FILE(GLOB SHADERS
	"*.fs"
	"*.vs"
)

file(COPY ${SHADERS} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
