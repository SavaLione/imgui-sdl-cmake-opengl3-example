cmake_minimum_required (VERSION 3.13.1)

set(IMGUI_PROJECT "imgui")
set(IMGUI_PROJECT_VERSION "1.88")

project(${IMGUI_PROJECT}
    VERSION ${IMGUI_PROJECT_VERSION}
    LANGUAGES CXX
)

option(IMGUI_BUILD_SHARED "Build shared library" ON)
option(IMGUI_BUILD_EXAMPLE "Build example" OFF)

# Set default build to release
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Choose Release or Debug" FORCE)
endif()

message(STATUS "Build type: " ${CMAKE_BUILD_TYPE})

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

# Libraries dependencies
find_package(OpenGL REQUIRED)
find_package(SDL2 REQUIRED)

# Dear ImGui sources
set(IMGUI_SRC
    src/imgui.cpp
    src/imgui_demo.cpp
    src/imgui_draw.cpp
    src/imgui_impl_opengl3.cpp
    src/imgui_impl_sdl.cpp
    src/imgui_tables.cpp
    src/imgui_widgets.cpp
)

# Dear ImGui library
if(IMGUI_BUILD_SHARED)
    add_library(${PROJECT_NAME} SHARED ${IMGUI_SRC})
    target_compile_definitions(${PROJECT_NAME} PUBLIC IMGUI_SHARED_LIB)
else()
    add_library(${PROJECT_NAME} STATIC ${IMGUI_SRC})
endif()

add_library(imgui::imgui ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME} PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/include>" "$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>")

# OpenGL
target_link_libraries(${PROJECT_NAME} ${OPENGL_gl_LIBRARY})
target_include_directories(${PROJECT_NAME} PUBLIC ${OPENGL_INCLUDE_DIR})

# SDL2
target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC ${SDL2_INCLUDE_DIRS})

# Example
if(IMGUI_BUILD_EXAMPLE)
    add_subdirectory(example)
endif()
