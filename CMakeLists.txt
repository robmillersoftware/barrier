cmake_minimum_required(VERSION 3.10)

# Barrier - Open-source KVM software
project(Barrier)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find required packages
find_package(Qt5 COMPONENTS Widgets Core Gui REQUIRED)
find_package(Threads REQUIRED)

# Add subdirectories (if any)
add_subdirectory(src)

# Include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)
include_directories(${Qt5Widgets_INCLUDE_DIRS})
include_directories(${Qt5Core_INCLUDE_DIRS})
include_directories(${Qt5Gui_INCLUDE_DIRS})

# Link libraries
set(LINK_LIBS
    Qt5::Widgets
    Qt5::Core
    Qt5::Gui
    Threads::Threads
)

# Add executable
add_executable(barrier
    src/main.cpp
    # Add other source files here
)

# Link the executable with required libraries
target_link_libraries(barrier ${LINK_LIBS})

# Optional: Installation rules
install(TARGETS barrier DESTINATION bin)
