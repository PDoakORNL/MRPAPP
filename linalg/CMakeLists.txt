set(srcs vector.cpp matrix.cpp)
add_library(linalg STATIC ${srcs})
target_include_directories(linalg PUBLIC
"${PROJECT_SOURCE_DIR};${PROJECT_BINARY_DIR};${CMAKE_CURRENT_SOURCE_DIR};${CMAKE_CURRENT_SOURCE_DIR}/util")

target_link_libraries(linalg PUBLIC platform)

if(MRPAPP_HAVE_GPU)
   target_link_libraries(linalg PRIVATE gpu_utils)
endif(MRPAPP_HAVE_GPU)

get_property(linalg_include_dirs TARGET linalg PROPERTY INCLUDE_DIRECTORIES)
message("linalg target exports includes: ${linalg_include_dirs}")

add_subdirectory(tests)
