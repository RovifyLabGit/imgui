cmake_minimum_required(VERSION 3.10)
project(imgui)

find_package(glfw3 REQUIRED)
set(CMAKE_CXX_STANDARD 17)

set(IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(IMGUI_SRC_FILES
    ${IMGUI_DIR}/imgui.cpp
    ${IMGUI_DIR}/imgui_demo.cpp
    ${IMGUI_DIR}/imgui_draw.cpp
    ${IMGUI_DIR}/imgui_tables.cpp
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
)
include_directories(${IMGUI_DIR})
add_library(${PROJECT_NAME} ${IMGUI_SRC_FILES})
target_link_libraries(${PROJECT_NAME} PRIVATE glfw)
target_include_directories(${PROJECT_NAME} PUBLIC ${IMGUI_DIR})
target_compile_definitions(${PROJECT_NAME} PRIVATE IMGUI_IMPL_OPENGL_LOADER_GL3W)
