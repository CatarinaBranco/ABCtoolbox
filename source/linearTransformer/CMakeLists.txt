# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

## transformer ###########################################################################
file(GLOB linearTransformer_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)
file(GLOB linearTransformer_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang" OR "${CMAKE_CXX_COMPILER_ID}" STREQUAL "AppleClang")
    set_source_files_properties(${linearTransformer_sources} PROPERTIES
        COMPILE_FLAGS "-Wno-deprecated -Wno-write-strings -Wno-logical-op-parentheses -Wno-c++11-compat-deprecated-writable-strings -Wno-extra-tokens "
    )
endif()

add_executable(transformer${abctoolbox_version}
    ${ABCT_EXCLUDE_FROM_ALL}
    ${linearTransformer_headers}
    ${linearTransformer_sources}
)

if(ABCToolbox_Append_Version)
    set_target_properties(transformer${abctoolbox_version} PROPERTIES OUTPUT_NAME transformer)
    if(make_current)
        add_executable(transformer ALIAS transformer${abctoolbox_version})
    endif()
endif()
