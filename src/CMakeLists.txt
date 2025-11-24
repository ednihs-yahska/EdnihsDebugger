add_library(libedb libedb.cpp)
add_library(edb::libedb ALIAS libedb)

set_target_properties(
    libedb
    PROPERTIES OUTPUT_NAME edb
)

target_compile_features(libedb PUBLIC cxx_std_17)

target_include_directories(
    libedb
    PRIVATE include
    PUBLIC ${CMAKE_SOURCE_DIR}/include
)

