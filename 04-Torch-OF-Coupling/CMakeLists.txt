cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(Torch-OF)

# find wmake
find_program(FOUND_WMAKE wmake
            PATH /usr/lib/openfoam/)

if(FOUND_WMAKE)
    message(STATUS "Found wmake in ${FOUND_WMAKE}")
    add_custom_target(wmake-Torch ALL
            COMMAND ${FOUND_WMAKE}
            WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
            )

    add_test(NAME OF-Torch-run
            COMMAND torch-openfoam-solver
            WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
            )
endif()
