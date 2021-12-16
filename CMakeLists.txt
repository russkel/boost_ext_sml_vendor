cmake_minimum_required(VERSION 3.5)

project(boost_ext_sml_vendor)

find_package(ament_cmake REQUIRED)

macro(build_boost_ext_sml)
  include(ExternalProject)

  externalproject_add(boost_ext_sml
    URL https://raw.githubusercontent.com/boost-ext/sml/edfd7bd4cf53e5d63ac6f2c4b088c1a0de4793f0/include/boost/sml.hpp
    URL_HASH SHA256=ffb1fc382c67f746e7f39b7cd25cd6f4ce84c93f7d097bcc9d13a7fdfaea7230
    DOWNLOAD_NO_EXTRACT True
    BUILD_IN_SOURCE True
    DOWNLOAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}/source
    CONFIGURE_COMMAND ""
    BUILD_COMMAND ""
    INSTALL_COMMAND ""
  )

  install(
    DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/source/
    DESTINATION include/boost/
  )
endmacro()

build_boost_ext_sml()

ament_export_include_directories(include)
# this ensures that the package has an environment hook setting the PATH
ament_package()
