set(MOVEIT_LIB_NAME moveit_kinematics_plugin_loader)

add_library(${MOVEIT_LIB_NAME} SHARED src/kinematics_plugin_loader.cpp)
set_target_properties(${MOVEIT_LIB_NAME} PROPERTIES VERSION "${${PROJECT_NAME}_VERSION}")
ament_target_dependencies(${MOVEIT_LIB_NAME}
  rclcpp
  urdf
  pluginlib
  class_loader
  ament_index_cpp
  moveit_core
  Boost
)
target_link_libraries(${MOVEIT_LIB_NAME}
  moveit_rdf_loader
)

install(TARGETS ${MOVEIT_LIB_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin)

install(DIRECTORY include/ DESTINATION include)
