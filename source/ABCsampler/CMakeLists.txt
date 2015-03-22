# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

## ABCsampler ############################################################################
file(GLOB ABCsampler_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)
file(GLOB ABCsampler_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang" OR "${CMAKE_CXX_COMPILER_ID}" STREQUAL "AppleClang")
    set_source_files_properties(${ABCsampler_sources} PROPERTIES
        COMPILE_FLAGS "-Wno-deprecated -Wno-write-strings -Wno-logical-op-parentheses -Wno-c++11-compat-deprecated-writable-strings -Wno-extra-tokens "
    )
endif()

add_executable(ABCsampler${abctoolbox_version}
    ${ABCT_EXCLUDE_FROM_ALL}
    ${ABCsampler_headers}
    ${ABCsampler_sources}
)

if(ABCToolbox_Append_Version)
    set_target_properties(ABCsampler${abctoolbox_version} PROPERTIES OUTPUT_NAME ABCsampler)
    if(make_current)
        add_executable(ABCsampler ALIAS ABCsampler${abctoolbox_version})
    endif()
endif()

