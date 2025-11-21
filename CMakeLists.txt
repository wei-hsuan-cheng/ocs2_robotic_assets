cmake_minimum_required(VERSION 3.5)
project(ocs2_robotic_assets)

find_package(ament_cmake REQUIRED)

###########
## Build ##
###########

# Generate the header in the build tree so the source remains read-only safe.
set(GENERATED_INCLUDE_DIR "${CMAKE_CURRENT_BINARY_DIR}/include/${PROJECT_NAME}")
file(MAKE_DIRECTORY "${GENERATED_INCLUDE_DIR}")
configure_file(
  "${PROJECT_SOURCE_DIR}/include/${PROJECT_NAME}/package_path.h.in"
  "${GENERATED_INCLUDE_DIR}/package_path.h" @ONLY
)

#############
## Install ##
#############

install(DIRECTORY "${GENERATED_INCLUDE_DIR}/" DESTINATION include/${PROJECT_NAME})

install(DIRECTORY resources DESTINATION share/${PROJECT_NAME})

ament_export_include_directories("${GENERATED_INCLUDE_DIR}")
ament_package()
