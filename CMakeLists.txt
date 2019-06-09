# ------------------------------------------------------------------------------
#        A Modular Optimization framework for Localization and mApping
#                               (MOLA)
#
# Copyright (C) 2018-2019, Jose Luis Blanco-Claraco, contributors (AUTHORS.md)
# All rights reserved.
# Released under GNU GPL v3. See LICENSE file
# ------------------------------------------------------------------------------

# Tell CMake we'll use C++ for use in its tests/flags
project(mola-common)

# Generate: mola-common-version.cmake
include(CMakePackageConfigHelpers)

if(NOT ${CMAKE_VERSION} VERSION_LESS "3.14.0")
	set(ARCH_INDEP_FLAG "ARCH_INDEPENDENT")
endif()

write_basic_package_version_file(mola-common-version.cmake
  VERSION 0.1.0
  COMPATIBILITY AnyNewerVersion
  $ARCH_INDEP_FLAG
)

# Generate: mola-common.cmake
# For now, it's static, so no need to parse the file.


# Install files:
# TODO
