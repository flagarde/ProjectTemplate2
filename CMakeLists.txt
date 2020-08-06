cmake_minimum_required(VERSION 3.16...3.18.1)

# Download CMakeCM
set(CMAKECM_BASE_URL "https://raw.githubusercontent.com/flagarde/CMakeCM/master" CACHE STRING "URL of the CMakeCM package")
set(CMAKECM_SHA256 "3ca3423211bedd9e700b220f157f447f30694b5ffe28e0f5195abc3f03a9f3b1" CACHE STRING "SHA256 of CMakeCM")
set(CMAKECM_INSTALL_DIR "${CMAKE_BINARY_DIR}/cmake/CMakeCM" CACHE STRING "Path where to install CMakeCM")
set(CMAKECM_MODULES_DIR "${CMAKECM_INSTALL_DIR}/Modules")
file(DOWNLOAD "${CMAKECM_BASE_URL}/CMakeCM.cmake" "${CMAKECM_INSTALL_DIR}/CMakeCM.cmake" INACTIVITY_TIMEOUT 5 TIMEOUT 5 EXPECTED_HASH SHA256=${CMAKECM_SHA256})
include("${CMAKECM_INSTALL_DIR}/CMakeCM.cmake")

include(GitInfos)

project(${REPOSITORY_NAME} VERSION "0.2" DESCRIPTION "Template for C++ projects" HOMEPAGE_URL "${HOSTING_BASEURL}/${DEPOT_PROVIDER}/${REPOSITORY_NAME}" LANGUAGES CXX)

#execute_process(
#    COMMAND ${GIT_EXECUTABLE} "tag" "--list" "--format=%(refname:strip=2)"
#    RESULT_VARIABLE RESULT
#    OUTPUT_VARIABLE OUTPUT)
#message(STATUS "${OUTPUT}")
#string(REPLACE "\n" ";" OUTPUT ${OUTPUT})

#message(STATUS "${OUTPUT}")
#set(OUTPUT "L;LL;0.2;")
#list(LENGTH OUTPUT len)
#message(STATUS "len = ${len}")

#string(REPLACE " " ";" TAGS ${OUTPUT})

#message(STATUS "${PROJECT_VERSION}")
#list(FIND OUTPUT "${PROJECT_VERSION}" TAG)

#message(STATUS ${TAG})
#endif()

#if(NOT ${TAG_EXISTS} EQUAL -1)
#  message(STATUS "Tag v${PROJECT_VERSION} already exists")
#else()
#  execute_process(

#    COMMAND ${GIT_EXECUTABLE} tag v${PROJECT_VERSION}
#    RESULT_VARIABLE RESULT
#    OUTPUT_VARIABLE OUTPUT)
#endif()

#string (REGEX REPLACE "\n" ";"  TAGS ${TAGS})
#set_property (CACHE REPO_TAG PROPERTY STRINGS ${TAGS})

configure_file("${CMAKE_SOURCE_DIR}/docs/README.md.in" "${CMAKE_SOURCE_DIR}/README.md" @ONLY)

add_executable(main main.cpp)

install(TARGETS main)

enable_testing()
add_test(NAME main COMMAND main)
