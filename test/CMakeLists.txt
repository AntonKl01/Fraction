include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip
)

set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(${PROJECT_NAME}.test
  AllTests.cpp
  tests.cpp)

target_link_libraries(${PROJECT_NAME}.test
  ${PROJECT_NAME} gtest_main)

target_compile_definitions(${PROJECT_NAME}.test 
  PRIVATE TEST_DIR="${CMAKE_CURRENT_LIST_DIR}/test")

include(GoogleTest)
gtest_discover_tests(${PROJECT_NAME}.test)

