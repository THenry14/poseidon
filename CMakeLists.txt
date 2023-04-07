cmake_minimum_required(VERSION 3.5)

project(poseidon)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -O3 -fPIC")

set(SOURCES_C sources/f251.c sources/poseidon_rc.c sources/poseidon.c)
set(DEPENDENCIES sources/f251.h sources/poseidon_rc.h sources/poseidon.h)

add_library(poseidon_c_objects OBJECT ${SOURCES_C} ${DEPENDENCIES})
add_library(poseidon SHARED $<TARGET_OBJECTS:poseidon_c_objects>)

set_target_properties(poseidon PROPERTIES OUTPUT_NAME "poseidon")
