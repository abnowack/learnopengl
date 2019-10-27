add_executable(coordinates Coordinates.cpp)
target_link_libraries(coordinates PRIVATE glad glfw3 opengl32)

FILE(GLOB SHADERS
	"*.fs"
	"*.vs"
)

file(COPY ${SHADERS} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
