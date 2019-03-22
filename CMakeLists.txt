cmake_minimum_required(VERSION 3.2)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(NumberGenerators)

set(SRC_LIST
    src/FibonacciNumberGenerator.cpp
    src/PrimeNumberGenerator.cpp
    src/RandomNumberGenerator.cpp
    src/UtilityFunctions.cpp
)

include_directories(src)
add_library(${PROJECT_NAME}-lib ${SRC_LIST})
add_executable(${PROJECT_NAME} src/Generators.cpp)
target_link_libraries(${PROJECT_NAME} ${PROJECT_NAME}-lib)

set(TEST_SRC_LIST
    test/testMain.cpp
    test/RandomNumberGeneratorTests.cpp
    test/FibonacciNumberGeneratorTests.cpp
    test/PrimeNumberGeneratorTests.cpp
    test/UtilityFunctionsTests.cpp
)

add_executable(${PROJECT_NAME}-ut ${TEST_SRC_LIST})
target_link_libraries(${PROJECT_NAME}-ut ${PROJECT_NAME}-lib)