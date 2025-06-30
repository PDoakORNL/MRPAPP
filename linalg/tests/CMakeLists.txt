# linalg unit tests

set(test_srcs vector_cpu_test.cpp)
if(MRPAPP_HAVE_GPU)
set(test_srcs ${test_srcs} vector_gpu_test.cpp vector_cpu_gpu_test.cpp)
endif()

add_executable(test_vector ${test_srcs})
target_link_libraries(test_vector PUBLIC platform linalg Catch2::Catch2WithMain)
mrpapp_gpu_runtime_link(test_vector)
catch_discover_tests(test_vector)


set(test_srcs matrix_cpu_test.cpp)
if(MRPAPP_HAVE_GPU)
set(test_srcs ${test_srcs} matrix_gpu_test.cpp matrix_cpu_gpu_test.cpp)
endif()

add_executable(test_matrix ${test_srcs})
target_link_libraries(test_matrix PUBLIC platform linalg Catch2::Catch2WithMain psimaglite)
mrpapp_gpu_runtime_link(test_matrix)
catch_discover_tests(test_matrix)
