cmake_minimum_required(VERSION 3.10)

project(MatMulAlgorithms)

set(CMAKE_CXX_STANDARD 23)
if(NOT DEFINED MULTIPLIER)
    set(MULTIPLIER "hybrid")
endif()


add_executable(with_canaries MatMulAlgorithms/main.cpp)
target_compile_options(with_canaries PRIVATE -fstack-protector-all)

add_executable(without_canaries MatMulAlgorithms/main.cpp)
target_compile_options(without_canaries PRIVATE -fno-stack-protector)

enable_testing()
add_test(NAME WithCanariesTest COMMAND with_canaries --mult ${MULTIPLIER} --sizes 2048_2048_2048)
add_test(NAME WithoutCanariesTest COMMAND without_canaries --mult ${MULTIPLIER} --sizes 2048_2048_2048)

