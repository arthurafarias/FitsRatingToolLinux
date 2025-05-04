cmake_minimum_required(VERSION 4.0)
project(NativeFitsLoader VERSION 0.1.0)

file(GLOB ${PROJECT_NAME}_SOURCES *.cpp)
file(GLOB ${PROJECT_NAME}_HEADERS *.h)

add_library(${PROJECT_NAME} SHARED ${${PROJECT_NAME}_SOURCES})

target_include_directories(${PROJECT_NAME} PUBLIC
    /usr/include
    /usr/include/cminpack-1
    /usr/local/include
)

target_link_directories(${PROJECT_NAME} PUBLIC
    /usr/lib
    /usr/local/lib
    /usr/include
)

target_link_libraries(${PROJECT_NAME} PUBLIC
    cminpack_d
    cfitsio
    blas
    sep
    m
)

install(TARGETS
    ${PROJECT_NAME}
        LIBRARY
            DESTINATION
                ${CMAKE_INSTALL_PREFIX}/lib
)