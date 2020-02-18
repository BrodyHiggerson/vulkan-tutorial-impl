cmake_minimum_required(VERSION 3.2)
project(vulkan-tutorial-impl)

IF(MSVC)
	# Setup warning level
	ADD_DEFINITIONS(/W4)		# Level 4
    ADD_DEFINITIONS(/WX)		# Warnings as errors
	
	# Suppress warnings
	ADD_DEFINITIONS(/wd4201)	# Nonstandard extension used: nameless struct/union
	ADD_DEFINITIONS(/wd4100)	# Unreferenced formal parameter)
	
	ADD_DEFINITIONS(/D NOMINMAX)
	
    # Disable exceptions
	ADD_DEFINITIONS(/EHsc)
	
	# Draft spec and standards-comformance mode
	ADD_DEFINITIONS(/std:c++latest)
	ADD_DEFINITIONS(/permissive-)
	
	# Multi-processor compilation
	ADD_DEFINITIONS(/MP)
ENDIF()

add_subdirectory(apps)
add_subdirectory(third_party)

SET_PROPERTY(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT app1)
