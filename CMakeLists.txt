cmake_minimum_required(VERSION 3.9)

project(glad)

install( FILES
        src/glad.c
        include/glad/glad.h
        include/KHR/khrplatform.h
)

# Find source files
file(GLOB SOURCES src/*.cpp)

# Include header files
include_directories(include/glad include/KHR)

# Create shared library
add_library(${PROJECT_NAME} SHARED ${SOURCES})

# Install library
install(TARGETS ${PROJECT_NAME} DESTINATION lib/${PROJECT_NAME})

# Install library headers
file(GLOB HEADERS include/*.h)
install(FILES ${HEADERS} DESTINATION include/${PROJECT_NAME})
