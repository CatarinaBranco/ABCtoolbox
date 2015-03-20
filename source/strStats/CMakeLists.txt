# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

## strStats ##############################################################################
file(GLOB strStats_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)
file(GLOB strStats_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

set_source_files_properties(${strStats_sources} PROPERTIES
    COMPILE_FLAGS "-Wno-deprecated -Wno-write-strings -Wno-logical-op-parentheses -Wno-c++11-compat-deprecated-writable-strings -Wno-extra-tokens "
)

add_executable(strStats${abctoolbox_version}
    ${ABCT_EXCLUDE_FROM_ALL}
    ${strStats_headers}
    ${strStats_sources}
)

if(ABCToolbox_Append_Version)
    set_target_properties(strStats${abctoolbox_version} PROPERTIES OUTPUT_NAME strStats)
    if(make_current)
        add_executable(strStats ALIAS strStats${abctoolbox_version})
    endif()
endif()



