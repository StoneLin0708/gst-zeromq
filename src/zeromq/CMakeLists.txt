add_library(libgstzmq SHARED
	gstzmq.h
	gstzmqplugin.c
	gstzmqplugin.h
	gstzmqsink.c
	gstzmqsink.h
	gstzmqsrc.c
	gstzmqsrc.h
)

add_definitions(-DGST_LICENSE="LGPL")
add_definitions(-DVERSION="1.0.0")
add_definitions(-DPACKAGE="gst-zeromq")

target_link_libraries(libgstzmq
	ZeroMQ::ZeroMQ
    PkgConfig::gstreamer
    PkgConfig::gstreamer-base
    PkgConfig::gstreamer-controller
)

install(
	TARGETS libgstzmq
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}/gstreamer-1.0
)