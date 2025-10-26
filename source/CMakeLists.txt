cmake_minimum_required(VERSION 3.21)

project(InventoryFunctionsSE)

find_package(common REQUIRED CONFIG)
find_package(xbyak REQUIRED CONFIG)
find_package(skse64_common REQUIRED CONFIG)
find_package(skse64 REQUIRED CONFIG)

add_library(InventoryFunctionsSE SHARED
    InventoryFunctions64.cpp
    InventoryFunctions64.h
    main.cpp
    exports.def
)


target_link_libraries(
	InventoryFunctionsSE
	PUBLIC
        skse64::skse64
		skse64::skse64_common
		xse::common
)

set_target_properties(
	InventoryFunctionsSE
	PROPERTIES
		MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
)