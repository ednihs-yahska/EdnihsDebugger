add_library(libedb libedb.cpp)
add_library(edb::libedb ALIAS libedb)

set_target_properties(
    libedb
    PROPERTIES OUTPUT_NAME edb
)

target_compile_features(libedb PUBLIC cxx_std_17)

target_include_directories(libedb
    PUBLIC
      $<INSTALL_INTERFACE:include>
      $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include>
    PRIVATE
      ${CMAKE_SOURCE_DIR}/src/include
)

include(GNUInstallDirs)
install(
  TARGETS libedb
  EXPORT edb-targets
  LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
  ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
  RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR}
  INCLUDES DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

install(
  DIRECTORY ${PROJECT_SOURCE_DIR}/include/
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

install(
  EXPORT edb-targets
  FILE edb-config.cmake
  NAMESPACE edb::
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/edb
)

