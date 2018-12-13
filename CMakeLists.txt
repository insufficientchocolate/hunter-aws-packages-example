cmake_minimum_required(VERSION 3.2)

include(cmake/HunterGate.cmake)
  
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.71.tar.gz"
    SHA1 "5342b852c620cf482144a4edf2686b4a64d68cda"
    LOCAL
)

project(hunter-aws-packages-example)

add_executable(
    handler
    main.cc
)

hunter_add_package(aws-lambda-runtime)
find_package(aws-lambda-runtime CONFIG REQUIRED)

target_link_libraries(handler AWS::aws-lambda-runtime)

