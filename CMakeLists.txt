cmake_minimum_required(VERSION 3.16...3.18.1)

# Download CMakeCM
set(CMAKECM_BASE_URL
    "https://raw.githubusercontent.com/flagarde/CMakeCM/master"
    CACHE STRING "URL of the CMakeCM package")
set(CMAKECM_SHA256
    "a5739917401b3bddbd8a32e280008ed98aa1311cf1f217ac78490c800ed2ff9a"
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

include(CTest)
enable_testing()

include(ConfigurationTypes)

add_configuration(CONFIG Debug INTERPROCEDURAL_OPTIMIZATION OFF C_FLAGS "-g0" OBJC_FLAGS "-g0" OBJCXX_FLAGS "-g0" Fortran_FLAGS "-g0" ASM_FLAGS "-g0" CXX_FLAGS "-g0")

if("${CMAKE_C_COMPILER_ID}" MATCHES "(Apple)?[Cc]lang" OR "${CMAKE_CXX_COMPILER_ID}" MATCHES "(Apple)?[Cc]lang")
  add_configuration(CONFIG Coverage BASE_CONFIG Debug CXX_FLAGS "-fprofile-instr-generate -fcoverage-mapping" C_FLAGS "-fprofile-instr-generate -fcoverage-mapping")
elseif(CMAKE_COMPILER_IS_GNUCXX)
  add_configuration(CONFIG Coverage BASE_CONFIG Debug CXX_FLAGS "--coverage" "-fprofile-arcs" "-ftest-coverage" C_FLAGS "--coverage -fprofile-arcs -ftest-coverage")
else()
  message(ERROR "Code coverage requires Clang or GCC. Coverage Configuration will be equal to Debug")
  add_configuration(CONFIG Coverage BASE_CONFIG Debug)
endif()

set_default_configuration(Debug VERBOSE)

# Code Coverage Configuration
#add_library(coverage_config INTERFACE)

#option(CODE_COVERAGE "Enable coverage reporting" OFF)
#if(CODE_COVERAGE AND CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
  # Add required flags (GCC & LLVM/Clang)
#  target_compile_options(
#    coverage_config
#    INTERFACE -O0 # no optimization
#              -g # generate debug info
#              -fprofile-arcs -ftest-coverage)
#  if(CMAKE_VERSION VERSION_GREATER_EQUAL 3.13)
#    target_link_options(coverage_config INTERFACE -fprofile-arcs
#                        -ftest-coverage)
#  else()
#    target_link_libraries(coverage_config INTERFACE -fprofile-arcs
#                                                    -ftest-coverage)
#  endif()
#endif()

option(BUILD_DOCS_ONLY "Build documentation only" OFF)
option(BUILD_DOCS "Build documentation" ON)

if(BUILD_DOCS OR BUILD_DOCS_ONLY)
  add_subdirectory(docs)
  if(BUILD_DOCS_ONLY)
    return()
  endif()
endif()


add_subdirectory(src)

add_subdirectory(apps)

option(BUILD_TESTING "Build the testing tree." ON)
# Only build tests if we are the top-level project Allows this to be used by
# super projects with `add_subdirectory`
if(BUILD_TESTING AND (PROJECT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR))
  enable_testing()
  add_subdirectory(tests)
endif()




set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
