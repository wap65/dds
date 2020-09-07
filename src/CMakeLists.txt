cmake_minimum_required(VERSION 3.10)

project(dds)

option(USE_WINDOWS_THREADING "Build with WinAPI threads" "OFF")
option(USE_STL_THREADING "Build with std::thread" "ON")

add_library(${PROJECT_NAME} SHARED dds.cpp Init.cpp dump.cpp ABsearch.cpp ABstats.cpp CalcTables.cpp DealerPar.cpp File.cpp LaterTricks.cpp Memory.cpp Moves.cpp Par.cpp PlayAnalyser.cpp PBN.cpp QuickTricks.cpp Scheduler.cpp SolveBoard.cpp SolverIF.cpp System.cpp ThreadMgr.cpp Timer.cpp TimerGroup.cpp TimerList.cpp TimeStat.cpp TimeStatList.cpp TransTableS.cpp TransTableL.cpp)
if (${USE_WINDOWS_THREADING})
list(APPEND THREAD_OPTIONS "DDS_THREADS_WINAPI")
endif()

if (${USE_STL_THREADING})
list(APPEND THREAD_OPTIONS "DDS_THREADS_STL")
endif()

target_compile_definitions(${PROJECT_NAME} PRIVATE ${THREAD_OPTIONS})