cmake_minimum_required(VERSION 3.2)

set(PROJECT_VERSION VERSION 0.1)
project(OpenMEEG LANGUAGES C CXX ${PROJECT_VERSION})

set(OpenMEEG_HEADER_INSTALLDIR toto)
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake ${CMAKE_SOURCE_DIR}/cmake/FortranCInterface)

include(GenerateExportHeader)
include(BlasLapackOption)
include(CompileOptions)
include(CheckCXXFeatures)
CHECK_CXX_STANDARD_LIBRARY()

configure_file(${OpenMEEG_SOURCE_DIR}/OpenMEEGConfigure.h.in
               ${OpenMEEG_BINARY_DIR}/OpenMEEGConfigure.h)

set(OpenMEEG_INCLUDE_DIRECTORIES
    ${OpenMEEG_BINARY_DIR}
    ${OpenMEEG_SOURCE_DIR}
    # ${OpenMEEG_SOURCE_DIR}/src
    ${OpenMEEG_SOURCE_DIR}/OpenMEEGMaths/include
    ${OpenMEEG_SOURCE_DIR}/OpenMEEG/include
    ${OpenMEEG_BINARY_DIR}/OpenMEEG/src
    ${OpenMEEG_BINARY_DIR}/OpenMEEGMaths/src
    # ${OpenMEEG_OTHER_INCLUDE_DIRS}
    # ${matio_INCLUDE_DIRS}
)

include_directories(${OpenMEEG_INCLUDE_DIRECTORIES})

add_subdirectory(OpenMEEGMaths)
add_subdirectory(OpenMEEG)
