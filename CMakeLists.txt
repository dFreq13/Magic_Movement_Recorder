cmake_minimum_required(VERSION 3.15)
project(Magic_Movement_Recorder LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)

FetchContent_Declare(
    imgui
    GIT_REPOSITORY https://github.com/ocornut/imgui.git
    GIT_TAG master
)

FetchContent_MakeAvailable(imgui)

file(GLOB_RECURSE SRC_FILES
    src/*.cpp
)

add_library(Magic_Recode SHARED
    ${SRC_FILES}
    ${imgui_SOURCE_DIR}/imgui.cpp
    ${imgui_SOURCE_DIR}/imgui_draw.cpp
    ${imgui_SOURCE_DIR}/imgui_tables.cpp
    ${imgui_SOURCE_DIR}/imgui_widgets.cpp
)

target_include_directories(Magic_Recode PRIVATE
    ${imgui_SOURCE_DIR}
)
