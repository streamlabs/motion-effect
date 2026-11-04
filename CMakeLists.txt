cmake_minimum_required(VERSION 3.22...3.25)

set(motion-transition_SOURCES
	./src/helper.c
	./src/motion-transition/motion-transition.c
)

set(motion-transition_HEADERS
	./src/helper.h
)

add_library(motion-transition MODULE)
add_library(OBS::mtransition ALIAS motion-transition)

target_sources(
	motion-transition
	PRIVATE ${motion-transition_SOURCES}
	${motion-transition_HEADERS})

target_link_libraries(motion-transition PRIVATE OBS::libobs)

set_target_properties(motion-transition PROPERTIES FOLDER "plugins/motion-transition")

set_property(GLOBAL APPEND PROPERTY OBS_MODULE_LIST "motion-transition")
set_target_properties(motion-transition PROPERTIES PREFIX "")

# cmake-format: off
set_target_properties_obs(motion-transition PROPERTIES FOLDER plugins/motion-transition PREFIX "")
# cmake-format: on