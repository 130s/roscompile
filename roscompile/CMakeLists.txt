cmake_minimum_required(VERSION 3.5)
project(roscompile)

find_package(ament_cmake REQUIRED)
find_package(ros_introspection REQUIRED)

if(BUILD_TESTING)
#Cmake alternative not yet found so commented out.
#  catkin_download_test_data(test_data.zip
#      https://github.com/DLu/roscompile_test_data/raw/main/test_data.zip
#      DESTINATION ${CATKIN_DEVEL_PREFIX}/${CATKIN_PACKAGE_SHARE_DESTINATION}/test
#  )

  find_package(ament_cmake_pytest REQUIRED)
  ament_add_pytest_test(a_unit_test test/utest.py)

  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
  #  set(ROSLINT_PYTHON_OPTS --max-line-length=120 --ignore=E111,E114,E302)
endif()

install(PROGRAMS
        scripts/roscompile
        scripts/add_tests
        scripts/convert_to_format_2
        scripts/add_compile_options
        scripts/roscompile_command
        scripts/upgrade_manifest
        scripts/noetic_migration
        DESTINATION lib/${PROJECT_NAME})
install(FILES data/cmake.ignore data/cmake_patterns.ignore data/package.ignore data/package_patterns.ignore
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/data
)

ament_package()
