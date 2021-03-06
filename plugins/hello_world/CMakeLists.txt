###
# Loadable algorithms

find_package( OpenCV REQUIRED )

set( plugin_headers
  hello_world_detector.h
  hello_world_filter.h
  )

set( plugin_sources
  hello_world_detector.cxx
  hello_world_filter.cxx
  )

kwiver_install_headers(
  SUBDIR     viame
  ${plugin_headers}
  )

kwiver_install_headers(
  ${CMAKE_CURRENT_BINARY_DIR}/viame_hello_world_export.h
  NOPATH   SUBDIR     viame
  )

kwiver_add_library( viame_hello_world
  ${plugin_headers}
  ${plugin_sources}
  )

target_link_libraries( viame_hello_world
  PUBLIC               vital_algo
                       ${OpenCV_LIBRARIES}
  )

algorithms_create_plugin( viame_hello_world
  register_algorithms.cxx
  )
