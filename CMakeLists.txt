cmake_minimum_required(VERSION 3.8)
project(my_package)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

################ BUILD DEPENDENCIES  #################
find_package(ament_cmake REQUIRED)          # c++    (optional)
find_package(rclcpp REQUIRED)               # c++    (optional)
# find_package(ament_cmake_python REQUIRED)   # python (optional)
find_package(rclpy REQUIRED)                # python (optional)
######################################################

################ FIND DEPENDENCIES  ##################
find_package(std_msgs REQUIRED)

################## INSTALL Python  ###################
install(PROGRAMS
  scripts/my_node.py
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()