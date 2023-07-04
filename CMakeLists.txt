cmake_minimum_required(VERSION 3.27.0)

# Project Name
project(IMGUIDev)

# Add Compile Options
add_compile_options(-Wall)

# Set up executable
add_executable(IMGUIDev)

# Set C++ standard
target_compile_features(IMGUIDev PRIVATE cxx_std_17)

# Source files
target_sources(IMGUIDev PRIVATE
    "src/Application.cpp"

    # IMGUI Files
    "external/imgui/imgui.cpp"
    "external/imgui/imgui_draw.cpp"
    "external/imgui/imgui_widgets.cpp"
    "external/imgui/imgui_tables.cpp"
    "external/imgui/backends/imgui_impl_glfw.cpp"
    "external/imgui/backends/imgui_impl_opengl3.cpp"
)

# Include Directories
target_include_directories(IMGUIDev PRIVATE
    "external/imgui"
    "external/imgui/backends"
    "external/glfw/include"
    "external/glad/include"
)

# Add subdirectories
add_subdirectory(external/glad)
add_subdirectory(external/glfw)

# Link libraries
find_package(OpenGL REQUIRED)
target_link_libraries(IMGUIDev PRIVATE glad glfw ${OPENGL_gl_LIBRARY})
