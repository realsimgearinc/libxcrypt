add_library(libxcrypt STATIC crypt.c)
target_sources(libxcrypt PUBLIC
    alg-des-tables.c
    alg-des.c
    alg-gost3411-2012-core.c
    alg-gost3411-2012-hmac.c
    alg-hmac-sha1.c
    alg-md4.c
    alg-md5.c
    alg-sha1.c
    alg-sha256.c
    alg-sha512.c
    alg-sm3-hmac.c
    alg-sm3.c
    alg-yescrypt-common.c
    alg-yescrypt-opt.c
    alg-yescrypt-platform.c
    crypt-bcrypt.c
    crypt-des-obsolete.c
    crypt-des.c
    crypt-gensalt-static.c
    crypt-gost-yescrypt.c
    crypt-md5.c
    crypt-nthash.c
    crypt-pbkdf1-sha1.c
    crypt-scrypt.c
    crypt-sha256.c
    crypt-sha512.c
    crypt-sm3-yescrypt.c
    crypt-sm3.c
    crypt-static.c
    crypt-sunmd5.c
    crypt-yescrypt.c
    crypt.c
    gen-des-tables.c
    util-base64.c
    util-gensalt-sha.c
    util-get-random-bytes.c
    util-make-failure-token.c
    util-xbzero.c
    util-xstrcpy.c

    PUBLIC FILE_SET HEADERS
    BASE_DIRS ${CMAKE_CURRENT_LIST_DIR} FILES
        alg-des.h
        alg-gost3411-2012-const.h
        alg-gost3411-2012-core.h
        alg-gost3411-2012-hmac.h
        alg-gost3411-2012-precalc.h
        alg-gost3411-2012-ref.h
        alg-hmac-sha1.h
        alg-md4.h
        alg-md5.h
        alg-sha1.h
        alg-sha256.h
        alg-sha512.h
        alg-sm3-hmac.h
        alg-sm3.h
        alg-yescrypt.h
        byteorder.h
        config.h
        crypt-hashes.h
        crypt-obsolete.h
        crypt-port.h
        crypt.h
)

if(CMAKE_C_STANDARD STREQUAL 17)
    target_compile_definitions(libxcrypt PRIVATE -DHAVE_STATIC_ASSERT_IN_ASSERT_H)
    target_compile_definitions(libxcrypt PRIVATE -DHAVE_MEMSET_S)
endif()

if(CMAKE_C_BYTE_ORDER STREQUAL BIG_ENDIAN)
    target_compile_definitions(libxcrypt PRIVATE -DENDIANNESS_IS_BIG)
elseif(CMAKE_C_BYTE_ORDER STREQUAL LITTLE_ENDIAN)
    target_compile_definitions(libxcrypt PRIVATE -DENDIANNESS_IS_LITTLE)
endif()

install(TARGETS libxcrypt FILE_SET HEADERS)
install(FILES
    ${CMAKE_SOURCE_DIR}/LICENSING
    ${CMAKE_SOURCE_DIR}/NEWS
    ${CMAKE_SOURCE_DIR}/THANKS
    ${CMAKE_SOURCE_DIR}/AUTHORS
    DESTINATION .)

install(DIRECTORY ${CMAKE_SOURCE_DIR}/doc/ DESTINATION doc/)
