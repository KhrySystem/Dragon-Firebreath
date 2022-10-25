cmake_minimum_required(VERSION 3.20)


set(CXX_FILES src/init.cpp)

if(DRAGON_BUILD_SHARED)
	set(DYNAMIC_LOADER ON)
	add_subdirectory(openxr)
	add_library(firebreath SHARED ${CXX_FILES})
else() 
	add_subdirectory(openxr)
	add_library(firebreath STATIC ${CXX_FILES})
endif()
target_include_directories(firebreath PUBLIC ${Dragon_INCLUDE_DIRS})
target_link_libraries(firebreath PUBLIC openxr_loader ${Boost_LIBRARIES})
add_library(Dragon::Firebreath ALIAS firebreath)