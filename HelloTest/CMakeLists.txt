cmake_minimum_required(VERSION 3.26)
project(HelloTest)

set(CMAKE_CXX_STANDARD 17)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(
  ${PROJECT_NAME}
  HelloTest.cpp
)
target_link_libraries(
  ${PROJECT_NAME}
  GTest::gtest_main
  Hello
)

include(GoogleTest)
gtest_discover_tests(HelloTest)