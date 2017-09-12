cmake_minimum_required(VERSION 2.8.12)

if(CMAKE_COMPILER_IS_GNUCXX)
    add_definitions(-std=gnu++0x)
endif()

find_package(ZLIB REQUIRED)


find_package(OpenCV REQUIRED)
find_package(Boost COMPONENTS thread REQUIRED)
find_package(Boost COMPONENTS filesystem REQUIRED)
find_package(Boost COMPONENTS system REQUIRED)
find_package(Boost COMPONENTS date_time REQUIRED)

find_package(Pangolin 0.1 REQUIRED)




IF(UNIX)
    set(CMAKE_CXX_FLAGS "-O3 -msse2 -msse3")
ENDIF (UNIX)



include_directories(/home/gzhang8/bin/OpenNI-Bin-Dev-Linux-x64-v1.5.7.10/Include
			)

INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIR})
INCLUDE_DIRECTORIES(${ZLIB_INCLUDE_DIR})

set(Boost_USE_STATIC_LIBS OFF)
set(Boost_USE_MULTITHREADED ON)
set(Boost_USE_STATIC_RUNTIME OFF)
set(BOOST_ALL_DYN_LINK ON)   # force dynamic linking for all libraries


add_executable(klg2oni 
               src/klg2oni.cpp
	             src/RawLogReader.cpp
	             src/
               )

target_link_libraries(klg2oni
                      ${ZLIB_LIBRARY}
                      ${Boost_SYSTEM_LIBRARIES}
                      ${Boost_THREAD_LIBRARIES}
                      ${OpenCV_LIBS}
                      ${Pangolin_LIBRARIES}
                      ${Boost_FILESYSTEM_LIBRARIES}
                      #/home/gzhang8/bin/OpenNI-Bin-Dev-Linux-x64-v1.5.7.10/Lib/libOpenNI.so
                      #/home/gzhang8/bin/OpenNI-Bin-Dev-Linux-x64-v1.5.7.10/Lib/libnimRecorder.so
                      #/home/gzhang8/bin/OpenNI-Bin-Dev-Linux-x64-v1.5.7.10/Lib/libnimMockNodes.so
)
