cmake_minimum_required(VERSION 3.16...3.18.1)

set(GITHUB_ORGANIZATION "flagarde")
set(PROJECT_NAME "ProjectTemplate")

project(${PROJECT_NAME} VERSION "0.1.0.0" DESCRIPTION "Template for C++ projects" HOMEPAGE_URL "https://github.com/${GITHUB_ORGANIZATION}/${PROJECT_NAME}" LANGUAGES CXX)

configure_file("${CMAKE_SOURCE_DIR}/docs/README.md.in" "${CMAKE_SOURCE_DIR}/README.md" @ONLY)

add_executable(main main.cpp)

install(TARGETS main)

enable_testing()
add_test(NAME main COMMAND main)
