# Copyright (C) 2012-2018  (see AUTHORS file for a list of contributors)
#
# This file is part of GNSS-SDR.
#
# GNSS-SDR is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GNSS-SDR is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GNSS-SDR. If not, see <https://www.gnu.org/licenses/>.
#


add_subdirectory(libswiftcnav)

set(TELEMETRY_DECODER_LIB_SOURCES
    viterbi_decoder.cc
)

set(TELEMETRY_DECODER_LIB_HEADERS
    viterbi_decoder.h
    convolutional.h
)

include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_SOURCE_DIR}/src/core/system_parameters
    ${CMAKE_SOURCE_DIR}/src/core/interfaces
    ${CMAKE_SOURCE_DIR}/src/core/receiver
    ${CMAKE_SOURCE_DIR}/src/algorithms/telemetry_decoder/adapters
    ${Boost_INCLUDE_DIRS}
    ${GLOG_INCLUDE_DIRS}
    ${GFlags_INCLUDE_DIRS}
)

list(SORT TELEMETRY_DECODER_LIB_HEADERS)
list(SORT TELEMETRY_DECODER_LIB_SOURCES)

add_library(telemetry_decoder_lib
    ${TELEMETRY_DECODER_LIB_SOURCES}
    ${TELEMETRY_DECODER_LIB_HEADERS}
)
source_group(Headers FILES ${TELEMETRY_DECODER_LIB_HEADERS})

target_link_libraries(telemetry_decoder_lib gnss_system_parameters)
