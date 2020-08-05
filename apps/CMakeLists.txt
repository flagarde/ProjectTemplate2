add_executable(main main.cpp)

install(TARGETS main RUNTIME DESTINATION bin)

enable_testing()
add_test(NAME main COMMAND main)
