project(win-capture)

set(win-capture_HEADERS
	obfuscate.h
	hook-helpers.h
	cursor-capture.h
	graphics-hook-info.h
	window-helpers.h
	dc-capture.h)

set(win-capture_SOURCES
	dc-capture.c
	obfuscate.c
	cursor-capture.c
	game-capture.c
	window-helpers.c
	monitor-capture.c
	window-capture.c
	load-graphics-offsets.c
	duplicator-monitor-capture.c
	plugin-main.c)

add_library(win-capture MODULE
	${win-capture_SOURCES}
	${win-capture_HEADERS})
target_link_libraries(win-capture
	libobs
	ipc-util
	psapi.lib)

install_obs_plugin_with_data(win-capture data)

add_subdirectory(graphics-hook)
add_subdirectory(get-graphics-offsets)
add_subdirectory(inject-helper)
