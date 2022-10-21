cmake_minimum_required(VERSION 3.20)

set(CXX_FILES src/init.cpp)

add_library(firebreath SHARED ${CXX_FILES})
target_include_directories(firebreath PUBLIC ${Dragon_INCLUDE_DIRS})
target_link_libraries(firebreath PUBLIC ${Dragon_LINK_LIBRARIES})
add_library(Dragon::Firebreath ALIAS firebreath)