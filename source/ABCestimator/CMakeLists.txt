# Set minimum required cmake version
cmake_minimum_required(VERSION 3.0)

## ABCestimator ##########################################################################
file(GLOB ABCestimator_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)
file(GLOB ABCestimator_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

set_source_files_properties(${ABCestimator_sources} PROPERTIES
    COMPILE_FLAGS "-Wno-deprecated -Wno-write-strings -Wno-logical-op-parentheses -Wno-c++11-compat-deprecated-writable-strings -Wno-extra-tokens "
)

add_executable(ABCestimator${abctoolbox_version}
    ${ABCT_EXCLUDE_FROM_ALL}
    ${ABCestimator_headers}
    ${ABCestimator_sources}
)

add_custom_command(TARGET ABCestimator${abctoolbox_version} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different "${CMAKE_CURRENT_SOURCE_DIR}/../../scripts/plotPosteriorsGLM.r" "$<TARGET_FILE_DIR:ABCestimator${abctoolbox_version}>/plotPosteriorsGLM.r"
)

if(ABCToolbox_Append_Version)
    set_target_properties(ABCestimator${abctoolbox_version} PROPERTIES OUTPUT_NAME ABCestimator)
    if(make_current)
        add_executable(ABCestimator ALIAS ABCestimator${abctoolbox_version})
    endif()
endif()
