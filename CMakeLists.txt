project(breeze-gtk)
set(PROJECT_VERSION "5.14.80")
set(PROJECT_VERSION_MAJOR 5)

cmake_minimum_required(VERSION 2.8.12)

find_package(ECM 0.0.9 REQUIRED NO_MODULE)
include(FeatureSummary)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR} "${CMAKE_SOURCE_DIR}/cmake")
find_package(GTKEngine)
find_package(Sass REQUIRED)

if(CMAKE_VERSION VERSION_LESS 3.12.0)
    find_package(PythonInterp 3 REQUIRED)
else()
    find_package(Python3 COMPONENTS Interpreter REQUIRED)
endif()

include(KDEInstallDirs)

add_subdirectory(kconf_update)
add_subdirectory(src)

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
