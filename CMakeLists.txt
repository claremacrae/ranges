cmake_minimum_required(VERSION 3.9.2)
project(ranges)

set(CMAKE_VERBOSE_MAKEFILE OFF)

set(CMAKE_CXX_STANDARD 14)

add_executable(
    ${PROJECT_NAME}
    adjacent.hpp
    algorithm.hpp
    cartesian_product.hpp
    iterator_range.hpp
    main.cpp
    named_type.hpp
    test_cartesian_product.cpp
    transform.hpp
    variadic.hpp
    zip.hpp
)

if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    target_compile_options(${PROJECT_NAME} PRIVATE
        -Wall
        -Wextra
        -Wpedantic
        -Werror
        -Wno-unused-function
        )
elseif(CMAKE_CXX_COMPILER_ID STREQUAL "MSVC")
    target_compile_options(${PROJECT_NAME} PRIVATE
        /W4
        /WX
        /wd4505 # unreferenced local function has been removed
        )
endif()
