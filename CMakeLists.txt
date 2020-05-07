cmake_minimum_required(VERSION 3.17)

set(NAME librtmp-1)

project(${NAME}, C)

if (WIN32)

    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

    add_definitions(
        -DUSE_GNUTLS
        -D_CRT_SECURE_NO_WARNINGS
        -D_WINSOCK_DEPRECATED_NO_WARNINGS
    )

    include_directories(
        C:/gstreamer/1.0/x86_64/include
    )

    link_directories(
        C:/gstreamer/1.0/x86_64/lib
    )

    link_libraries(
        WinMM.lib
        WSock32.Lib
        gnutls.lib
        nettle.lib
        gmp.lib
        hogweed.lib
        z.lib
    )

endif (WIN32)

if (UNIX)
    add_definitions(
        -DUSE_GNUTLS
    )

    include_directories()

    link_directories()

    link_libraries()
endif (UNIX)

file(GLOB FILES *.c *.h)

add_library(${NAME} SHARED ${FILES} )