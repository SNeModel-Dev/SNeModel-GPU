    cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
    project(cmake_and_cuda LANGUAGES CXX CUDA)
    set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake" ${CMAKE_MODULE_PATH})     
    include_directories( include )
    include(CTest)
     
    #add_library(cuda_test STATIC
#	src/test.cu
#      )
     
    # Request that particles be built with -std=c++11
    # As this is a public compile feature anything that links to 
    # particles will also build with -std=c++11
 #   target_compile_features(cuda_test PUBLIC cxx_std_11)
     
    # We need to explicitly state that we need all CUDA files in the 
    # particle library to be built with -dc as the member functions 
    # could be called by other libraries and executables
#    set_target_properties(cuda_test 
#                           PROPERTIES CUDA_SEPARABLE_COMPILATION ON)
     
    add_executable(cuda_test_exe src/test.cu)
     
    set_property(TARGET cuda_test_exe 
                 PROPERTY CUDA_SEPARABLE_COMPILATION ON)
    #target_link_libraries(cuda_test_exe PRIVATE cuda_test)
