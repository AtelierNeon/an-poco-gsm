# Sources
file(GLOB SRCS_G "src/*.cpp")
POCO_SOURCES_AUTO(SRCS ${SRCS_G})

add_executable(PocoDoc ${SRCS})

target_link_libraries(PocoDoc PUBLIC Poco::Util Poco::XML Poco::CppParser)

if(NOT POCO_WITHOUT_INSTALL_FILES AND NOT POCO_WITHOUT_INSTALL_ALL)
	install(
		TARGETS PocoDoc EXPORT PocoDocTargets
		LIBRARY DESTINATION lib${LIB_SUFFIX}
		ARCHIVE DESTINATION lib${LIB_SUFFIX}
		RUNTIME DESTINATION bin
		INCLUDES DESTINATION include
	)
endif()
