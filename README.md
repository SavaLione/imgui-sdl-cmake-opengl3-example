# imgui-sdl-cmake-opengl3-example
This is an example of compiling [Dear ImGui](https://github.com/ocornut/imgui) as a library using CMake.

## Dependencies
1. [CMake](https://cmake.org/)
2. [SDL - Simple Directmedia Layer (Version 2.0)](https://github.com/libsdl-org/SDL)
3. [OpenGL (SDL dependency)](https://www.khronos.org/opengl/)

Used Dear ImGui backends:
* [imgui_impl_opengl3](https://github.com/ocornut/imgui/blob/master/backends/imgui_impl_opengl3.h)
* [imgui_impl_sdl](https://github.com/ocornut/imgui/blob/master/backends/imgui_impl_sdl.h)

## Compile and install
Run:
```
$ mkdir build && cd build
$ cmake ..
$ make
```

### Build options
* ``IMGUI_BUILD_SHARED`` (default: ``ON``): Build shared library
* ``IMGUI_BUILD_EXAMPLE`` (default: ``OFF``): Build example

## Project structure
|File/Path                                        |Description                                                        |
|:------------------------------------------------|:------------------------------------------------------------------|
|[CMakeLists.txt](CMakeLists.txt)                 |CMake building automation script                                   |
|[src/](src/)                                     |Directory with Dear ImGui source files                             |
|[include/](include/)                             |Directory with Dear ImGui header files                             |
|[example/](example/)                             |Directory with example application that uses created ImGui library |
|[example/CMakeLists.txt](example/CMakeLists.txt) |CMake building automation script for example project               |
|[example/src/](example/src/)                     |Directory with source files for example project                    |

## Additional information
* Author of this example: Saveliy Pototskiy ([savalione.com](https://savalione.com))
* Link to GitHub: https://github.com/SavaLione/imgui-sdl-cmake-opengl3-example
* Date of creation: 2022-11-07
