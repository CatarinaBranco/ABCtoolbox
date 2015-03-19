# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

set(make_current)

if(ABCToolbox_Append_Version)
    set(abctoolbox_version _2_0_0)
    if(ABCToolbox_Current)
        set(make_current TRUE)
    endif()
else()
    set(abctoolbox_version)
endif()

if("${CMAKE_CURRENT_SOURCE_DIR}" STREQUAL "${CMAKE_SOURCE_DIR}")
    if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
        set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static-libgcc -static-libstdc++")
    elseif("${CMAKE_CXX_COMPILER_ID}" STREQUAL "clang")
        set(CMAKE_CXX_FLAGS        "${CMAKE_CXX_FLAGS} -std=c++11 -stdlib=libc++")
        set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static-libgcc -static-libstdc++")
    endif()
endif()

add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/source/ABCestimator")
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/source/ABCsampler")
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/source/cumuldens")
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/source/glm")
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/source/linearTransformer")
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/source/strStats")

set(make_current)
set(abctoolbox_version)
