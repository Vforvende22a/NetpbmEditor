cmake_minimum_required (VERSION 3.24)

project ("NetpbmEditor" VERSION 1.3)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_compile_options($<$<CXX_COMPILER_ID:MSVC>:/MP>)

include(CMakePrintHelpers)

cmake_print_variables(CMAKE_MODULE_PATH)
cmake_print_variables(CMAKE_PREFIX_PATH)

include(CTest)
    
if(BUILD_TESTING)
    message(STATUS "Make Catch2 available...")
    if(EXISTS ${CMAKE_SOURCE_DIR}/lib/Catch2)
        add_subdirectory(${CMAKE_SOURCE_DIR}/lib/Catch2)
  
    else()
        include(FetchContent)
        FetchContent_Declare(
        Catch2
        GIT_REPOSITORY https://github.com/catchorg/Catch2.git
        GIT_TAG        v3.4.0
        FIND_PACKAGE_ARGS
        )

        FetchContent_MakeAvailable(Catch2)
    endif()
    include(Catch)

    cmake_print_variables(Catch2_DIR)
    cmake_print_variables(catch2_SOURCE_DIR)
    cmake_print_variables(Catch2_SOURCE_DIR)
    cmake_print_variables(CMAKE_MODULE_PATH)
endif()

include_directories("src")

add_subdirectory(src)

if(BUILD_TESTING)
  add_subdirectory(test)
endif()
