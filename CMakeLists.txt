project (GeographicLib-JavaScript NONE)

# Version information
set (PROJECT_VERSION_MAJOR 2)
set (PROJECT_VERSION_MINOR 0)
set (PROJECT_VERSION_PATCH 0)
set (PROJECT_VERSION "${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}")
if (PROJECT_VERSION_PATCH GREATER 0)
  set (PROJECT_VERSION "${PROJECT_VERSION}.${PROJECT_VERSION_PATCH}")
endif ()

set (RELEASE_DATE "2021-mm-dd")

cmake_minimum_required (VERSION 3.13.0)

# Set a default build type for single-configuration cmake generators if
# no build type is set.
if (NOT CMAKE_CONFIGURATION_TYPES AND NOT CMAKE_BUILD_TYPE)
  set (CMAKE_BUILD_TYPE Release)
endif ()

# For JavaScript documentation
find_program (JSDOC jsdoc)

find_program (MINIFY minify REQUIRED)

set (INSTALL_PATH "lib/node_modules"
  CACHE PATH "Installation directory GeographicLib-JavaScript")

enable_testing ()

add_subdirectory (src)

if (JSDOC)
  add_subdirectory (doc)
endif ()
