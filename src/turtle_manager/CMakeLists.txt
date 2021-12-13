cmake_minimum_required(VERSION 3.5)
project(turtle_manager)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rclcpp REQUIRED)

find_package(std_msgs REQUIRED)
find_package(std_srvs REQUIRED)
find_package(turtlesim REQUIRED)

set(dependencies  "geometry_msgs" "rclcpp" "std_msgs" "std_srvs" "turtlesim")
add_executable(draw_square src/draw_square.cpp)
ament_target_dependencies(draw_square ${dependencies})
install(TARGETS   draw_square 
  DESTINATION lib/${PROJECT_NAME})

ament_package()
