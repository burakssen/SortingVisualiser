cmake_minimum_required(VERSION 3.27)
project(sorting)

set(CMAKE_CXX_STANDARD 23)

set(SOURCE_DIR src)
set(VENDOR_DIR vendor)

add_subdirectory("${VENDOR_DIR}/raylib")

file(GLOB_RECURSE SOURCE_FILES 
    "${SOURCE_DIR}/**.cpp" 
    "${SOURCE_DIR}/**.h" 
    "${VENDOR_DIR}/rlImGui/rlImGui.cpp" 
    "${VENDOR_DIR}/rlImGui/*.h"
    "${VENDOR_DIR}/imgui/imgui_demo.cpp"
    "${VENDOR_DIR}/imgui/imgui_draw.cpp"
    "${VENDOR_DIR}/imgui/imgui_tables.cpp"
    "${VENDOR_DIR}/imgui/imgui_widgets.cpp"
    "${VENDOR_DIR}/imgui/imgui.cpp"
)

add_executable(sorting "${SOURCE_FILES}")

target_include_directories(sorting PUBLIC 
    "${SOURCE_DIR}"
    "${VENDOR_DIR}/raylib/src"
    "${VENDOR_DIR}/imgui"
    "${VENDOR_DIR}/rlImGui"
)

target_link_libraries(sorting PUBLIC raylib)