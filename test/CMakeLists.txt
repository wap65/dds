cmake_minimum_required(VERSION 3.10)

project(tests)

add_executable(dtest dtest.cpp args.cpp compare.cpp loop.cpp parse.cpp print.cpp testcommon.cpp TestTimer.cpp)
target_link_libraries(dtest dds)

add_custom_command(TARGET dtest POST_BUILD 
					COMMAND ${CMAKE_COMMAND} -E copy $<TARGET_FILE:dds> $<TARGET_FILE_DIR:dtest>)