add_subdirectory(example.cpp.main.1)
add_subdirectory(example.cpp.main.2)
if(WIN32)

	if(USE_MFC)

		add_subdirectory(example.cpp.main.MFC)
	endif(USE_MFC)
	add_subdirectory(example.cpp.wmain)
endif(WIN32)
