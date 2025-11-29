add_executable(tests tests.cpp)
target_link_libraries(tests PRIVATE edb::libedb Catch2::Catch2WithMain)


