find_package(FLTK)
if(FLTK_FOUND AND OPENGL_FOUND)
  include_directories(${FLTK_INCLUDE_DIR})
  include_directories(${CMAKE_CURRENT_SOURCE_DIR})
  FLTK_WRAP_UI(demo-ui demo.fl)
  add_library(demo-ui ${demo-ui_FLTK_UI_SRCS})
  target_link_libraries(demo-ui PRIVATE tinysplinecxx)
  add_executable(demo main.cxx eval.h sample.h frames.h)
  add_dependencies(demo demo-ui)
  target_link_libraries(demo demo-ui
    ${FLTK_LIBRARIES}
    ${OPENGL_LIBRARIES}
    tinysplinecxx
    )
endif()
