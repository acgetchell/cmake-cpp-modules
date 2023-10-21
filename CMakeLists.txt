cmake_minimum_required(VERSION 3.28)
project(cmake_cpp_modules CXX)

# Turning off extensions avoids a clang-16 issue
# Not needed for clang-17
set(CMAKE_CXX_EXTENSIONS OFF)
# Set the C++ standard to 20
set(CMAKE_CXX_STANDARD 20)

# Create a library
add_library(foo)
# Add the module file to the library
target_sources(foo
PUBLIC
FILE_SET CXX_MODULES FILES
foo.cpp)

add_executable(cmake_cpp_modules
    foo.cpp)
# Create an executable
add_executable(hello main.cpp)
# Link to the library foo
target_link_libraries(hello foo)

