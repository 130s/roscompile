cmake_minimum_required(VERSION 3.5)
project(ros_introspection)

find_package(ament_cmake REQUIRED)

if (BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

install(PROGRAMS
        scripts/print_packages.py
        DESTINATION lib/${PROJECT_NAME})

ament_package()