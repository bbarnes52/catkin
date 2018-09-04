cmake_minimum_required(VERSION 2.8.3)

set(catkin_EXTRAS_DIR ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

project(catkin)
message("bgb 1")
if(NOT DEFINED CATKIN_TOPLEVEL)
  include(${catkin_EXTRAS_DIR}/all.cmake NO_POLICY_SCOPE)
endif()
message("bgb 2")
catkin_package()
message("bgb 3")

install(FILES LICENSE
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
message("bgb 4")

# install cmake files for catkin (except some files only used at build time of catkin)
install(DIRECTORY cmake
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  USE_SOURCE_PERMISSIONS
  PATTERN "catkinConfig.cmake.in" EXCLUDE)

message("bgb 5")

catkin_python_setup()

message("bgb 6")

if(CATKIN_ENABLE_TESTING)
  catkin_add_nosetests(test/local_tests)
  catkin_add_nosetests(test/unit_tests)
endif()
