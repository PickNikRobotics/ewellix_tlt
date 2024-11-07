cmake_minimum_required(VERSION 3.22)
project(ewellix_tlt)

add_compile_options(-std=c++11)

# find dependencies
find_package(ament_cmake REQUIRED)

set(THIS_PACKAGE_INCLUDE_DEPENDS
  rclcpp
  rclpy
  std_msgs
  sensor_msgs
  # serial this is missing?
)

foreach(Dependency IN ITEMS ${THIS_PACKAGE_INCLUDE_DEPENDS})
  find_package(${Dependency} REQUIRED)
endforeach()


# add_executable(${PROJECT_NAME}_node
#   src/tlt_node.cpp
#   src/serial_com_tlt.cpp
#  )
# ament_target_dependencies(${PROJECT_NAME}_node ${THIS_PACKAGE_INCLUDE_DEPENDS})

# target_link_libraries(
#    ${PROJECT_NAME}_node
#   serial
#    )

install(
        DIRECTORY meshes urdf launch
        DESTINATION share/ewellix_tlt
)


ament_package()
