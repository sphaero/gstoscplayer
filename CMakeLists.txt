cmake_minimum_required(VERSION 3.5)

project(gstoscplayer LANGUAGES C)

find_package(PkgConfig)
pkg_check_modules(GST 
    gstreamer-1.0 
    gstreamer-audio-1.0 
    gstreamer-app-1.0 
    gstreamer-tag-1.0 
    gstreamer-pbutils-1.0)

pkg_check_modules(CZMQ REQUIRED
    libczmq)

add_executable(gstoscplayer main.c gst-play-kb.c gst-play-kb.h)
target_include_directories(gstoscplayer PUBLIC ${GST_INCLUDE_DIRS} ${CZMQ_INCLUDE_DIRS})
target_compile_options(gstoscplayer PUBLIC ${GST_CFLAGS_OTHER} ${CZMQ_CFLAGS_OTHER})
target_link_libraries(gstoscplayer -lm ${GST_LIBRARIES} ${CZMQ_LIBRARIES})
target_link_directories(gstoscplayer PUBLIC ${GST_LIBRARY_DIRS})

install(TARGETS gstoscplayer
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
