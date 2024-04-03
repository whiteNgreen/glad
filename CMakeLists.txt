cmake_minimum_required (VERSION 3.8)
project(gladProj)
set(HEADER_FILES ${CMAKE_SOURCE_DIR}/include/glad/glad.h ${CMAKE_SOURCE_DIR}/include/KHR/khrplatform.h)

add_library(glad
	src/glad.c

	${HEADER_FILES}
)

target_include_directories(glad PRIVATE ${CMAKE_SOURCE_DIR}/include)

if (GLAD_INSTALL)
	install(DIRECTORY include DESTINATION ${CMAKE_INSTALL_PREFIX}
		FILES_MATCHING PATTERN glad.h PATTERN khrplatform.h)
	install(EXPORT glad-targets DESTINATION include)
	install(TARGETS glad EXPORT glad-targets LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
endif()
