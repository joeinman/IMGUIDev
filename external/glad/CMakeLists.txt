cmake_minimum_required(VERSION 3.12)

project(glad)

# Add glad library
add_library(glad STATIC
    "src/gl.c"
)

target_include_directories(glad PUBLIC
    "include"
)