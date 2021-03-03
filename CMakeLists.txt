cmake_minimum_required(VERSION 3.9)
project(b6)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake_modules/)

add_library(b6 STATIC Device.cc Device.hh Packet.cc Packet.hh Error.hh Enum.hh Device.cc Packet.cc)

find_package(hidapi REQUIRED)
if (HIDAPI_FOUND)
    include_directories(${HIDAPI_INCLUDE_DIRS})
    target_link_libraries(b6 ${HIDAPI_LIBRARIES})
endif(HIDAPI_FOUND)

install(TARGETS b6 DESTINATION lib)
install(FILES Device.hh Packet.hh Error.hh Enum.hh DESTINATION include/b6)