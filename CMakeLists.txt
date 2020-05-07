cmake_minimum_required(VERSION 3.17)

set(NAME librtmp-1)

project(${NAME}, C)

set(C_STANDARD 11)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

if (WIN32)

    set(CMAKE_CXX_FLAGS_RELEASE /Zi /Ob0 /Od /RTC1 /MTd)
    set(CMAKE_CXX_FLAGS_DEBUG /O2 /Ob2 /DNDEBUG /MT)

    add_definitions(
        -DUSE_GNUTLS
        -D_CRT_SECURE_NO_WARNINGS
        -D_WINSOCK_DEPRECATED_NO_WARNINGS
        -DUNICODE
        -D_UNICODE
    )

    include_directories(
        C:/gstreamer/1.0/x86_64/include
        C:/gstreamer/1.0/x86_64/include/glib-2.0
        C:/gstreamer/1.0/x86_64/lib/glib-2.0/include
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
        glib-2.0.lib
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

add_library(${NAME} SHARED ${FILES})