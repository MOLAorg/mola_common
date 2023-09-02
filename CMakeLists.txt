# ------------------------------------------------------------------------------
#        A Modular Optimization framework for Localization and mApping
#                               (MOLA)
#
# Copyright (C) 2018-2023, Jose Luis Blanco-Claraco, contributors (AUTHORS.md)
# All rights reserved.
# Released under GNU GPL v3. See LICENSE file
# ------------------------------------------------------------------------------

# Minimum CMake vesion: limited by CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS
cmake_minimum_required(VERSION 3.4)

project(mola_common)

include(GNUInstallDirs) # for install dirs in multilib
include(CMakePackageConfigHelpers)

# Instrumental lib:
add_library(${PROJECT_NAME} INTERFACE)

# Project version:
include(mola-version.cmake)

# Generate: mola_common-version.cmake
include(CMakePackageConfigHelpers)

if(NOT ${CMAKE_VERSION} VERSION_LESS "3.14.0")
	set(ARCH_INDEP_FLAG "ARCH_INDEPENDENT")
endif()

write_basic_package_version_file(
	# generate to the topmost root binary dir:
	${CMAKE_BINARY_DIR}/mola_common-config-version.cmake
  	VERSION ${MOLA_VERSION_NUMBER_MAJOR}.${MOLA_VERSION_NUMBER_MINOR}.${MOLA_VERSION_NUMBER_PATCH}
  	COMPATIBILITY AnyNewerVersion
  	${ARCH_INDEP_FLAG}
)

# Generate: mola_common.cmake
configure_file(
	# Input:
	mola_common-config.cmake.in
	# Output: generate to the topmost root binary dir:
	${CMAKE_BINARY_DIR}/mola_common-config.cmake
	# Parse: "@var_names@" only
	@ONLY
)

# Allow build-time finding of this package:
set(mola_common_DIR ${CMAKE_CURRENT_SOURCE_DIR} CACHE PATH "Path to mola_common")

# Install files:
install(
	FILES
		${CMAKE_BINARY_DIR}/${PROJECT_NAME}-config.cmake
		${CMAKE_BINARY_DIR}/${PROJECT_NAME}-config-version.cmake
		${CMAKE_SOURCE_DIR}/mola_cmake_functions.cmake
		${CMAKE_SOURCE_DIR}/mola-version.cmake
		${CMAKE_SOURCE_DIR}/mola-xxx-config.cmake.in
		DESTINATION
		${CMAKE_INSTALL_LIBDIR}/${PROJECT_NAME}/cmake
)

# Provide make uninstall:
if (NOT TARGET uninstall)
  configure_file(
    "${CMAKE_CURRENT_SOURCE_DIR}/cmake_uninstall.cmake.in"
    "${CMAKE_BINARY_DIR}/cmake_uninstall.cmake"
    IMMEDIATE @ONLY)
  add_custom_target(uninstall
    COMMAND ${CMAKE_COMMAND} -P ${CMAKE_BINARY_DIR}/cmake_uninstall.cmake)
endif()

