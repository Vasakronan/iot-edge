#Andriy Rymar
#Compiling executable GW file 

cmake_minimum_required(VERSION 2.8.12)

set(java_gw_sources
    ./src/main.c
)

set(java_gw_headers
)

include_directories(./inc ${IOTHUB_CLIENT_INC_FOLDER})
include_directories(${GW_INC})
include_directories(../../modules/common)

add_executable(java_gw ${java_gw_headers} ${java_gw_sources})

add_dependencies(java_gw java_module_host logger)

target_link_libraries(java_gw gateway)
linkSharedUtil(java_gw)
linkHttp(java_gw)
install_broker(java_gw ${CMAKE_CURRENT_BINARY_DIR}/$(Configuration) )
copy_gateway_dll(java_gw ${CMAKE_CURRENT_BINARY_DIR}/$(Configuration) )
copy_iothub_client_dll(java_gw ${CMAKE_CURRENT_BINARY_DIR}/$(Configuration) )

add_module_to_solution(java_gw)
