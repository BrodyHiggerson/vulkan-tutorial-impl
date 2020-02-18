PROJECT(app1)

add_executable(${PROJECT_NAME} main.cpp)

find_package(Vulkan REQUIRED FATAL_ERROR)

target_link_libraries(${PROJECT_NAME}
	${Vulkan_LIBRARIES}
	glfw
	glm
)

target_include_directories(${PROJECT_NAME} PRIVATE
	${Vulkan_INCLUDE_DIRS}
)