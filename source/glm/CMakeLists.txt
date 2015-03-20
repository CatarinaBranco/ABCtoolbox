# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

## glm ###################################################################################
file(GLOB glm_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)
file(GLOB glm_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

set_source_files_properties(${glm_sources} PROPERTIES
    COMPILE_FLAGS "-Wno-deprecated -Wno-write-strings -Wno-logical-op-parentheses -Wno-c++11-compat-deprecated-writable-strings -Wno-extra-tokens "
)

add_executable(glm${abctoolbox_version}
    ${ABCT_EXCLUDE_FROM_ALL}
    ${glm_headers}
    ${glm_sources}
)

if(ABCToolbox_Append_Version)
    set_target_properties(glm${abctoolbox_version} PROPERTIES OUTPUT_NAME glm)
    if(make_current)
        add_executable(glm ALIAS glm${abctoolbox_version})
    endif()
endif()
