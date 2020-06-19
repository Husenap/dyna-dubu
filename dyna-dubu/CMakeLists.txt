set(target_name "dyna-dubu")

set(src_files
    "src/main.cpp")

# Project
add_library(${target_name} STATIC ${src_files})

source_group("src" FILES "src/main.cpp")

set_target_properties(${target_name} PROPERTIES FOLDER ${PROJECT_NAME})

# Tests
add_executable(${target_name}_test "test/test.cpp")

target_link_libraries(${target_name}_test ${target_name})
target_link_libraries(${target_name}_test CONAN_PKG::gtest)

set_target_properties(${target_name}_test PROPERTIES FOLDER ${PROJECT_NAME})

gtest_discover_tests(${target_name}_test)