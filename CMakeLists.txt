cmake_minimum_required(VERSION 3.23)
project(cpp_playground)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
FetchContent_MakeAvailable(googletest)

enable_testing()

# Add test executables
add_executable(cpp_tests tests/cpp_test.cc)
target_link_libraries(cpp_tests GTest::gtest_main)

# Use gtest_discover_tests for each test executable
include(GoogleTest)
gtest_discover_tests(cpp_tests)

# main executable
add_executable(main src/main.cpp)
