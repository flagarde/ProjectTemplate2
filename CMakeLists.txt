cmake_minimum_required(VERSION 3.12...3.18.1)

# Download CMakeCM
set(CMAKECM_BASE_URL
    "https://raw.githubusercontent.com/flagarde/CMakeCM/master"
    CACHE STRING "URL of the CMakeCM package")
set(CMAKECM_SHA256
    "9493e474c71d279c2b263afffb3ced51cfaf937a7c7103de444ab306f5f23df3"
    CACHE STRING "SHA256 of CMakeCM")
set(CMAKECM_INSTALL_DIR
    "${CMAKE_BINARY_DIR}/cmake/CMakeCM"
    CACHE STRING "Path where to install CMakeCM")
set(CMAKECM_MODULES_DIR "${CMAKECM_INSTALL_DIR}/Modules")
file(
  DOWNLOAD "${CMAKECM_BASE_URL}/CMakeCM.cmake"
  "${CMAKECM_INSTALL_DIR}/CMakeCM.cmake"
  INACTIVITY_TIMEOUT 5
  TIMEOUT 5
  EXPECTED_HASH SHA256=${CMAKECM_SHA256})
include("${CMAKECM_INSTALL_DIR}/CMakeCM.cmake")

include(Common)
include(GitInfos)

prevent_in_source_builds()

project(
  ProjectTemplate
  VERSION "0.2"
  DESCRIPTION "Template for C++ projects"
  HOMEPAGE_URL "${HOSTING_BASEURL}/${DEPOT_PROVIDER}/${REPOSITORY_NAME}"
  LANGUAGES CXX)

cxx_17()

default_install_prefix("${CMAKE_SOURCE_DIR}/bin")

include(Formatters)
# execute_process( COMMAND ${GIT_EXECUTABLE} "tag" "--list"
# "--format=%(refname:strip=2)" RESULT_VARIABLE RESULT OUTPUT_VARIABLE OUTPUT)
# message(STATUS "${OUTPUT}") string(REPLACE "\n" ";" OUTPUT ${OUTPUT})

# message(STATUS "${OUTPUT}") set(OUTPUT "L;LL;0.2;") list(LENGTH OUTPUT len)
# message(STATUS "len = ${len}")

# string(REPLACE " " ";" TAGS ${OUTPUT})

# message(STATUS "${PROJECT_VERSION}") list(FIND OUTPUT "${PROJECT_VERSION}"
# TAG)

# message(STATUS ${TAG}) endif()

# if(NOT ${TAG_EXISTS} EQUAL -1) message(STATUS "Tag v${PROJECT_VERSION} already
# exists") else() execute_process(

# COMMAND ${GIT_EXECUTABLE} tag v${PROJECT_VERSION} RESULT_VARIABLE RESULT
# OUTPUT_VARIABLE OUTPUT) endif()

# string (REGEX REPLACE "\n" ";"  TAGS ${TAGS}) set_property (CACHE REPO_TAG
# PROPERTY STRINGS ${TAGS})

configure_file("${CMAKE_SOURCE_DIR}/docs/README.md.in"
               "${CMAKE_SOURCE_DIR}/README.md" @ONLY)

# Use C++11
set(CMAKE_CXX_STANDARD 11)
# Require (at least) it
set(CMAKE_CXX_STANDARD_REQUIRED ON)
# Don't use e.g. GNU extension (like -std=gnu++11) for portability
set(CMAKE_CXX_EXTENSIONS OFF)

# Code Coverage Configuration
add_library(coverage_config INTERFACE)

option(CODE_COVERAGE "Enable coverage reporting" OFF)
if(CODE_COVERAGE AND CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
  # Add required flags (GCC & LLVM/Clang)
  target_compile_options(
    coverage_config
    INTERFACE -O0 # no optimization
              -g # generate debug info
              -fprofile-arcs -ftest-coverage)
  if(CMAKE_VERSION VERSION_GREATER_EQUAL 3.13)
    target_link_options(coverage_config INTERFACE -fprofile-arcs
                        -ftest-coverage)
  else()
    target_link_libraries(coverage_config INTERFACE -fprofile-arcs
                                                    -ftest-coverage)
  endif()
endif()

add_subdirectory(libs)

add_subdirectory(apps)

option(BUILD_TESTING "Build the testing tree." ON)
# Only build tests if we are the top-level project Allows this to be used by
# super projects with `add_subdirectory`
if(BUILD_TESTING AND (PROJECT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR))
  enable_testing()
  add_subdirectory(tests)
endif()
