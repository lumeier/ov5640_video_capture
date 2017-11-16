
cmake_minimum_required (VERSION 2.8.1)

########+ Project settings ########
PROJECT(ov_video_capture)
SET(LICENSE "MIT")

######## Build and include settings ########
include_directories(include
	$ENV{SDKTARGETSYSROOT}/usr/src/kernel/include/uapi
	$ENV{SDKTARGETSYSROOT}/usr/src/kernel/include
	$ENV{SDKTARGETSYSROOT}/usr/include
)

link_directories(
	${LINK_DIRECTORIES}
)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -Wextra -pedantic -mfp16-format=ieee")

add_executable(
	ov5640_test

	src/main.cc
	src/ipu_csc.c
	src/ov_video_capture.cc
)

target_link_libraries(
	ov5640_test
	opencv_core
	opencv_highgui
	opencv_imgcodecs
)
