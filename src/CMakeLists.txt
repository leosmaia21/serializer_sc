cmake_minimum_required(VERSION 3.10)

message("Subproject name: ${CMAKE_PROJECT_NAME}")
# Include SystemC headers (from the systemc subdirectory)
# include_directories(${PROJECT_SOURCE_DIR}/../systemc/include)

# Add your executable target

add_executable(${CMAKE_PROJECT_NAME} src/main.cpp)

target_include_directories(${CMAKE_PROJECT_NAME} PUBLIC ${PROJECT_SOURCE_DIR}/../systemc/include )

# Link against the SystemC library (built or pre-installed)
target_link_libraries(${CMAKE_PROJECT_NAME} PUBLIC systemc)

# Set C++ standard for your project
set_target_properties(${CMAKE_PROJECT_NAME} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
)

# Optionally set the output directory for the executable
set_target_properties(${CMAKE_PROJECT_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}")

