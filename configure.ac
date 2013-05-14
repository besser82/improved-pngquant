###
# Initialize autoconf with basic info about the project
#
# Edit these for changes:
#
# projectname
# numeric Version
# maintainer / bug-reporting
# name of tarball
# url of homepage
###
AC_INIT([pngquant],
	[2.0.0],
	[Kornel Lesiński (pornel@pornel.net)],
	[pngquant],
	[http://pngquant.org])


###
# Initialize automake
#
# foreign	= make sure this portable to non-GNU-systems
# no-dist-gz 	= %{project}.tar.gz is not needed
# dist-*	= create a corresponding %{project}.tar.%{compressed}
# -Wportability	= warn when there are issues on portability
###
AM_INIT_AUTOMAKE([foreign dist-bzip2 -Wportability])


###
# Initialize libtool with static lib disabled
###
LT_INIT([disable-static])
AC_CONFIG_MACRO_DIR([m4.cache])


###
# Substitute @VAR@ in *.in
###
AC_SUBST(RELEASEDATE, "March 2013")
AC_SUBST(SOVERSION, "0:1:0")	# interface:rev:age 1:2:3 -> libfoo.so.1.3.2
AC_DEFINE(RELEASEDATE, March 2013)


###
# Check for a "ISO C99"-aware C-compiler
# Check libc is "ISO C99"-capable
###
AC_PROG_CC_C99
AC_PROG_CXX			# wanted by: ltmain.sh
AM_PROG_CC_C_O
AC_CHECK_HEADER_STDBOOL		# wanted by: lib/viter.c


###
# Check for explicitly required libs and add needed includes
###
PKG_CHECK_MODULES([libpng], [libpng >= 1.2.46])
PKG_CHECK_MODULES([zlib], [zlib >= 1.2.3])


###
# Check for needed headers, functions and their usability
###
AC_C_INLINE			# wanted by: lib/libimagequant.c
AC_C_RESTRICT			# wanted by: lib/libimagequant.c
AC_CHECK_FUNCS([memset])	# wanted by: lib/viter.c
AC_CHECK_FUNCS([pow])		# wanted by: lib/libimagequant.c
AC_CHECK_FUNCS([sqrt])		# wanted by: lib/mediancut.c
AC_CHECK_FUNCS([strrchr])	# wanted by: src/pngquant.c
AC_CHECK_FUNCS([strtol])	# wanted by: src/pngquant.c
AC_CHECK_FUNCS([strtoul])	# wanted by: src/pngquant.c
AC_CHECK_HEADERS([fcntl.h])	# wanted by: src/pngquant.c
AC_CHECK_HEADERS([limits.h])	# wanted by: lib/libimagequant.c
AC_CHECK_HEADERS([stddef.h])	# wanted by: lib/libimagequant.h
AC_CHECK_HEADERS([stdint.h])	# wanted by: lib/mempool.c
AC_CHECK_HEADERS([stdlib.h])	# wanted by: lib/viter.c
AC_CHECK_HEADERS([string.h])	# wanted by: lib/viter.c
AC_FUNC_ERROR_AT_LINE		# wanted by: lib/libimagequant.c
AC_FUNC_MALLOC			# wanted by: lib/libimagequant.c
AC_TYPE_SIZE_T			# wanted by: lib/libimagequant.c


###
# Check for optional, enhancing libs and headers
###
AC_CHECK_HEADERS([Cocoa/Cocoa.h])


###
# Create Makefile
###
AC_OUTPUT([Makefile])
