# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

## cumuldens #############################################################################
file(GLOB cumuldens_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)
file(GLOB cumuldens_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang" OR "${CMAKE_CXX_COMPILER_ID}" STREQUAL "AppleClang")
    set_source_files_properties(${cumuldens_sources} PROPERTIES
        COMPILE_FLAGS "-Wno-deprecated -Wno-write-strings -Wno-logical-op-parentheses -Wno-c++11-compat-deprecated-writable-strings -Wno-extra-tokens "
    )
endif()

add_executable(cumuldens${abctoolbox_version}
    ${ABCT_EXCLUDE_FROM_ALL}
    ${cumuldens_headers}
    ${cumuldens_sources}
)

if(ABCToolbox_Append_Version)
    set_target_properties(cumuldens${abctoolbox_version} PROPERTIES OUTPUT_NAME cumuldens)
    if(make_current)
        add_executable(cumuldens ALIAS cumuldens${abctoolbox_version})
    endif()
endif()

