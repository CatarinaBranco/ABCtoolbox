# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
    set(CMAKE_EXE_LINKER_FLAGS "-static-libgcc -static-libstdc++")
endif()

add_definitions(-Wno-deprecated)
add_definitions(-Wno-write-strings)

file(GLOB ABCestimator_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/source/ABCestimator/*.h"
)
file(GLOB ABCestimator_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/source/ABCestimator/*.cpp"
)

add_executable(ABCestimator
    ${ABCestimator_headers}
    ${ABCestimator_sources}
)




file(GLOB ABCsampler_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/source/ABCsampler/*.h"
)
file(GLOB ABCsampler_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/source/ABCsampler/*.cpp"
)

add_executable(ABCsampler
    ${ABCsampler_headers}
    ${ABCsampler_sources}
)




file(GLOB cumuldens_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/source/cumuldens/*.h"
)
file(GLOB cumuldens_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/source/cumuldens/*.cpp"
)

add_executable(cumuldens
    ${cumuldens_headers}
    ${cumuldens_sources}
)




file(GLOB glm_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/source/glm/*.h"
)
file(GLOB glm_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/source/glm/*.cpp"
)

add_executable(glm
    ${glm_headers}
    ${glm_sources}
)





file(GLOB linearTransformer_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/source/linearTransformer/*.h"
)
file(GLOB linearTransformer_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/source/linearTransformer/*.cpp"
)

add_executable(transformer
    ${linearTransformer_headers}
    ${linearTransformer_sources}
)





file(GLOB strStats_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/source/strStats/*.h"
)
file(GLOB strStats_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/source/strStats/*.cpp"
)

add_executable(strStats
    ${strStats_headers}
    ${strStats_sources}
)


