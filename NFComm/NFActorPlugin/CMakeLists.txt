set(ProjectName "NFActorPlugin")
file(GLOB NFActorPlugin_ROOT_Cpp *.cpp)
file(GLOB NFActorPlugin_ROOT_CC *.cc)
file(GLOB NFActorPlugin_ROOT_Hpp *.h)

add_library(NFActorPlugin STATIC
	${NFActorPlugin_ROOT_Cpp}
	${NFActorPlugin_ROOT_CC}
	${NFActorPlugin_ROOT_Hpp})
	
if(UNIX)

	target_link_libraries(NFActorPlugin -static-libstdc++)

	add_definitions(
		-D_USRDLL
		-D_LIB
		-DNFDATABASEPLUGIN_EXPORTS
		-DWIN32_LEAN_AND_MEAN
		)
else()

endif()

set_target_properties( NFActorPlugin PROPERTIES OUTPUT_NAME_DEBUG "NFActorPlugin")
set_target_properties( NFActorPlugin PROPERTIES PREFIX "")
set_target_properties( NFActorPlugin PROPERTIES
	FOLDER "NFSDK"
	ARCHIVE_OUTPUT_DIRECTORY ${NFOutPutDir}
	RUNTIME_OUTPUT_DIRECTORY ${NFOutPutDir}
	LIBRARY_OUTPUT_DIRECTORY ${NFOutPutDir} )