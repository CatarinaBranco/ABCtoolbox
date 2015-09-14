#
#  @file  CMakeLists.txt
#
#  Licensing of this file is governed by the Evolvix Contributors License Agreement
#  as described at http://evolvix.org/intro/legal
#
#  The license chosen for this file is the BSD-3-Clause
#  ( http://opensource.org/licenses/BSD-3-Clause ):
#
#  Copyright (c) 3/26/15  Authors and contributors as listed in the corresponding
#                code repository of this file and associated organizations if applicable.
#                All rights reserved.
#/////////////////////////////////////////////////////////////////////////////
#  Redistribution and use in source and binary forms, with or without modification,
#  are permitted provided that the following conditions are met:
#   - Redistributions of source code must retain the above copyright notice,
#     this list of conditions and the following disclaimer.
#   - Redistributions in binary form must reproduce the above copyright notice,
#     this list of conditions and the following disclaimer in the documentation
#     and/or other materials provided with the distribution.
#   - Neither the names of authors nor the names of their organizations nor
#     the names of other contributors to the project may be used to endorse or promote
#     products derived from this software without specific prior written permission.
#  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
#  AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
#  WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED.
#  IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT,
#  INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
#  BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
#  DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
#  LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE
#  OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED
#  OF THE POSSIBILITY OF SUCH DAMAGE.
#/////////////////////////////////////////////////////////////////////////////

# Set minimum required cmake version
cmake_minimum_required(VERSION 2.8)

if(NOT abctoolbox_master_build)
    message(WARNING "
strStats is being meta-built independently from the main ABCToolbox project.
This is not recommended and could lead to issues. Please run CMake out of source \
from the repository root and build the entire project together.
")
endif()
    
## strStats ##############################################################################
file(GLOB strStats_headers
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)
file(GLOB strStats_sources
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang" OR "${CMAKE_CXX_COMPILER_ID}" STREQUAL "AppleClang")
    set_source_files_properties(${strStats_sources} PROPERTIES
        COMPILE_FLAGS "-Wno-deprecated -Wno-write-strings -Wno-logical-op-parentheses -Wno-c++11-compat-deprecated-writable-strings -Wno-extra-tokens "
    )
endif()

add_executable(strStats${ABCToolbox_version}
    ${ABCToolbox_EXCLUDE_FROM_ALL}
    ${strStats_headers}
    ${strStats_sources}
)

if(ABCToolbox_Append_Version)
    set_target_properties(strStats${ABCToolbox_version} PROPERTIES OUTPUT_NAME strStats)
    if(ABCToolbox_Current)
        add_executable(strStats ALIAS strStats${ABCToolbox_version})
    endif()
endif()



