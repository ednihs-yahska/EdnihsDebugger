add_executable(edb edb.cpp)
target_link_libraries(edb PRIVATE edb::libedb PkgConfig::libedit)

include(GNUInstallDirs)
install(
  TARGETS edb
  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

