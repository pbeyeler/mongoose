cmake_minimum_required(VERSION 3.10)
project(mongoose C)

find_package(OpenSSL REQUIRED)

set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -W -Wall -Werror -Wno-unused-function -DMG_ENABLE_SSL -O0")
set(CMAKE_EXE_LINKER_FLAGS_DEBUG "${CMAKE_EXE_LINKER_FLAGS_DEBUG}")

set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -W -Wall -Werror -Wno-unused-function -DMG_ENABLE_SSL -O3")
set(CMAKE_EXE_LINKER_FLAGS_RELEASE "${CMAKE_EXE_LINKER_FLAGS_RELEASE}")

add_library(mongoose SHARED mongoose.c)

target_link_libraries(mongoose ${OPENSSL_LIBRARIES})

install(TARGETS mongoose DESTINATION ${CMAKE_INSTALL_PREFIX})
