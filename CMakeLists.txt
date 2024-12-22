
cmake_minimum_required(VERSION 3.10)
project(serializer)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_FLAGS  "-march=x86-64")
# Add the SystemC folder (if you want to build it from source)
add_subdirectory(systemc)

# Add your project folder
add_subdirectory(src)

if(CMAKE_EXPORT_COMPILE_COMMANDS)
    add_custom_target(copy_compile_commands ALL
        COMMAND ${CMAKE_COMMAND} -E copy_if_different
        ${CMAKE_BINARY_DIR}/compile_commands.json
        ${CMAKE_SOURCE_DIR}/compile_commands.json
    )
endif()
