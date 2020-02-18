# GLFW - BEGIN
SET(BUILD_SHARED_LIBS OFF CACHE BOOL "Build shared libraries" FORCE)
SET(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "Build the GLFW example programs" FORCE)
SET(GLFW_BUILD_TESTS OFF CACHE BOOL "Build the GLFW test programs" FORCE)
SET(GLFW_BUILD_DOCS OFF CACHE BOOL "Build the GLFW documentation" FORCE)
SET(GLFW_INSTALL OFF CACHE BOOL "Generate installation target" FORCE)
SET(GLFW_VULKAN_STATIC OFF CACHE BOOL "Use the Vulkan loader statically linked into application" FORCE)

add_subdirectory(glfw)
SET_TARGET_PROPERTIES(glfw PROPERTIES FOLDER third_party)
if(MSVC)
	TARGET_COMPILE_OPTIONS(glfw PRIVATE /wd4152 /wd4204 /wd4244 /wd4456)
# else() What's the equivalent of the above on Linux?
	# TARGET_COMPILE_OPTIONS(glfw PRIVATE -Wall -Wextra -pedantic -Werror)
endif()
# GLFW - END

# GLM - BEGIN
SET(GLM_TEST_ENABLE OFF CACHE BOOL "" FORCE)
SET(GLM_TEST_ENABLE OFF)
ADD_SUBDIRECTORY(glm)
TARGET_COMPILE_DEFINITIONS(glm INTERFACE 
	GLM_FORCE_SWIZZLE 
	GLM_ENABLE_EXPERIMENTAL 
	#GLM_FORCE_LEFT_HANDED 
	# GLM_FORCE_CTOR_INIT # This option means that glm's vec classes no longer satisfy std::is_trivially_copyable, breaking serialization
)
SET_TARGET_PROPERTIES(glm_shared PROPERTIES FOLDER third_party)
SET_TARGET_PROPERTIES(glm_static PROPERTIES FOLDER third_party)
# GLM - END