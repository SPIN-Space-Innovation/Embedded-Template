# MIT License
#
# Copyright (c) 2023 SPIN - Space Innovation
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

cmake_minimum_required(VERSION 3.19)

set(PICO_SDK_PATH "${CMAKE_CURRENT_LIST_DIR}/external/pico-sdk")

# initialize the SDK based on PICO_SDK_PATH
include(pico_sdk_import.cmake)

project(template)

# initialize the Pico SDK
pico_sdk_init()

set(TEMPLATE_C_SRC "")
set(TEMPLATE_CXX_SRC "")

include("${CMAKE_CURRENT_LIST_DIR}/src/CMakeLists.txt")

add_executable(template "${TEMPLATE_C_SRC};${TEMPLATE_CXX_SRC}")

include(${CMAKE_CURRENT_LIST_DIR}/external/FreeRTOS-Kernel.cmake)

target_link_libraries(template
    pico_stdlib
    FreeRTOS)

pico_add_extra_outputs(template)