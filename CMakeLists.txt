cmake_minimum_required(VERSION 3.5)

project(boost_ext_sml_vendor)

find_package(ament_cmake REQUIRED)

macro(build_boost_ext_sml)
  include(ExternalProject)

  externalproject_add(boost_ext_sml
    URL https://github.com/boost-ext/sml/archive/refs/heads/master.zip
    URL_HASH SHA256=53f1d85c680eaa8a69803a909627d4ce053003e6b9441fd724bf04ce244d9675
    BUILD_IN_SOURCE True
    DOWNLOAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}
    SOURCE_DIR source
    CONFIGURE_COMMAND ""
    BUILD_COMMAND ""
    INSTALL_COMMAND ""
  )

  install(
    DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/source/include/
    DESTINATION include
  )
endmacro()

  build_boost_ext_sml()

ament_export_include_directories(include)
# this ensures that the package has an environment hook setting the PATH
ament_package()
