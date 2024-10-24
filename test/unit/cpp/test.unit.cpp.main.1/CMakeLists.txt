
add_executable(test.unit.cpp.main.1
	test.unit.cpp.main.1.cpp
	test_throw_int_NO_CATCHALL.cpp
	test_throw_int_USE_CATCHALL.cpp
)

target_link_libraries(test.unit.cpp.main.1
	PRIVATE
		Pantheios::Pantheios.core
		Pantheios::Pantheios.fe.all
		Pantheios::Pantheios.be.lrsplit
		Pantheios::Pantheios.ber.test
		Pantheios::Pantheios.bel.null
		Pantheios::Pantheios.bec.null
		Pantheios::Pantheios.bec.test
		Pantheios::Pantheios.util
)

if(WIN32)

	target_link_libraries(test.unit.cpp.main.1
		PRIVATE
			wininet
	)
endif(WIN32)

target_link_libraries(test.unit.cpp.main.1
	PRIVATE
		$<$<STREQUAL:${STLSOFT_INCLUDE_DIR},>:STLSoft::STLSoft>
		$<IF:$<VERSION_LESS:${xTests_VERSION},"0.23">,xTests::xTests.core,xTests::core>
)

list(APPEND X_GCC_CUSTOM_WARNINGS_TO_BE_SUPPRESSED writable-strings)
list(APPEND X_MSVC_CUSTOM_WARNINGS_TO_BE_SUPPRESSED 4459 4702)
define_target_compile_options(test.unit.cpp.main.1)

