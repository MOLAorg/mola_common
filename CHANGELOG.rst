^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package mola_common
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Forthcoming
-----------
* Merge pull request `#1 <https://github.com/MOLAorg/mola_common/issues/1>`_ from MOLAorg/feat/no-soversion-option
  Add MOLA_NO_SOVERSION option, for Python wheels
* Standalone install: relocatable config, and the version from package.xml
  The installed mola_common-config.cmake added the absolute path of the
  source dir to CMAKE_MODULE_PATH (which did not even hold the CMake
  functions): now it only uses its own dir, so the installed package can be
  moved, e.g. inside a Python wheel.
  The non-ROS version file got an empty version (".."), since the
  MOLA_VERSION_NUMBER\_* variables were never defined, so find_package() with
  a version failed. The project version is now read from package.xml.
  ROS builds are not affected.
* Add MOLA_NO_SOVERSION option to build libraries without VERSION/SOVERSION
  Python wheels cannot hold the libfoo.so -> libfoo.so.X.Y symlinks, so
  packaging needs a single unversioned file per library. Off by default.
* Contributors: Jose Luis Blanco-Claraco

0.6.1 (2026-05-17)
------------------
* fix: remove stale wrong trace cmake message with each configured library
* Contributors: Jose Luis Blanco-Claraco

0.6.0 (2026-05-10)
------------------
* Detect and use ccache if found
* Contributors: Jose Luis Blanco-Claraco

0.5.3 (2026-05-07)
------------------
* bump min required cmake version to 3.22
* Contributors: Jose Luis Blanco-Claraco

0.5.2 (2025-10-21)
------------------
* Removed leftover inclusion of old mola-version.cmake file
* Contributors: Jose Luis Blanco-Claraco

0.5.1 (2025-09-12)
------------------
* Fix issue: cmake scripts attempt to read package.xml of the caller even if not defining a module
* Contributors: Jose Luis Blanco-Claraco

0.5.0 (2025-08-28)
------------------
* FIX: auto-created foo_version.cmake file now uses the caller's version from package.xml instead of mola_common version
* Update ROS badges in README
* cmake: fix correct cmake silent warnings of non-used variables
* silent cmake warning on unused CMAKE_EXPORT_COMPILE_COMMANDS (cmake-only pkg)
* Contributors: Jose Luis Blanco-Claraco

0.4.1 (2025-05-22)
------------------
* add mola_version_to_hexadecimal() to mola_cmake_functions (and fix tab formatting)
* Update package license to 'BSD-3-Clause'
* Silent warnings if built w/o any version of ROS
* Fix text references to license (correct one for this package is BSD-3)
* Contributors: Jose Luis Blanco-Claraco

0.4.0 (2024-08-20)
------------------
* Reorganize cmake scripts to make them compatible with both ROS1 catkin and ROS2 ament
* Contributors: Jose Luis Blanco-Claraco

0.3.3 (2024-08-14)
------------------
* make the package to build on ROS 1 too
* Contributors: Jose Luis Blanco-Claraco

0.3.2 (2024-08-09)
------------------
* Fix ament_xmllint warnings
* Contributors: Jose Luis Blanco-Claraco

0.3.1 (2024-04-30)
------------------
* Bump cmake_minimum_required to 3.5
* Fix clang warning
* Contributors: Jose Luis Blanco-Claraco

0.3.0 (2024-01-07)
------------------
* Fix usage of mola:: cmake prefix
* add package file attribute
* Contributors: Jose Luis Blanco-Claraco

0.2.2 (2023-09-08)
------------------
* Fix package name in docs
* Generate ament-correct package for ROS2 builds
* fix lib name in cmake warning message
* Contributors: Jose Luis Blanco-Claraco

0.2.1 (2023-09-02)
------------------

0.2.0 (2023-08-24)
------------------
* First public release as ROS 2 package.
