cmake_minimum_required (VERSION 3.13.1)

set(IMGUI_EXAMPLE_PROJECT "imgui_example_sdl_opengl3")
set(IMGUI_EXAMPLE_PROJECT_VERSION "1.88")

project(${IMGUI_EXAMPLE_PROJECT}
    VERSION ${IMGUI_EXAMPLE_PROJECT_VERSION}
    LANGUAGES CXX
)

# Set default build to release
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Choose Release or Debug" FORCE)
endif()

message(STATUS "Build type: " ${CMAKE_BUILD_TYPE})

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)


# Libraries dependencies
find_package(OpenGL REQUIRED)
find_package(SDL2 REQUIRED)

# Example executable
add_executable(${PROJECT_NAME} src/main.cpp)


# OpenGL
target_link_libraries(${PROJECT_NAME} ${OPENGL_gl_LIBRARY})
target_include_directories(${PROJECT_NAME} PUBLIC ${OPENGL_INCLUDE_DIR})

# SDL2
target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC ${SDL2_INCLUDE_DIRS})

# ImGui
target_link_libraries(${PROJECT_NAME} imgui::imgui)
