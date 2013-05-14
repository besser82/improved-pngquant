###
# Global compiler-flags
###
AM_CFLAGS			= -Wall -Wno-unknown-pragmas -DNDEBUG -O3 \
				  -fstrict-aliasing -ffast-math \
				  -funroll-loops -fomit-frame-pointer \
				  -ffinite-math-only

ACLOCAL_AMFLAGS			= -I m4.cache


###
# This is what we want to build
###
# libimagequant
lib_LTLIBRARIES			= libimagequant.la

libimagequant_la_SOURCES	= lib/blur.c lib/mediancut.c lib/nearest.c \
				  lib/viter.c lib/libimagequant.c \
				  lib/mempool.c lib/pam.c

libimagequant_la_HEADERS	= lib/blur.h lib/mediancut.h lib/nearest.h \
				  lib/viter.h lib/libimagequant.h \
				  lib/mempool.h lib/pam.h

libimagequant_ladir		= lib

libimagequant_includedir	= $(includedir)/imagequant/

libimagequant_la_LDFLAGS	= -version-info @SOVERSION@

###
# pngquant linked
bin_PROGRAMS			= pngquant

pngquant_SOURCES		= src/pngquant.c src/rwpng.c

pngquant_HEADERS		= src/rwpng.h

pngquantdir			= src

pngquant_CFLAGS			= $(libpng_CFLAGS) $(zlib_CFLAGS)

pngquant_LDADD			= $(libpng_LIBS) $(zlib_LIBS) $(lib_LTLIBRARIES)

###
# pngquant static-bin
# TODO


###
# Things to explicitly include in dist-tarball
###
EXTRA_DIST			= bootstrap Doxyfile.in libimagequant.pc.in \
				  pngquant.1 src/rwpng_cocoa.m
dist_doc_DATA			= AUTHORS ChangeLog COPYING NEWS README


###
# Things to exclude from dist-tarball
###
dist-hook:
	rm -rf	$(top_distdir)/*.m4 $(top_distdir)/config.* \
		$(top_distdir)/configure $(top_distdir)/compile \
		$(top_distdir)/depcomp $(top_distdir)/install-sh \
		$(top_distdir)/ltmain.sh $(top_distdir)/m4.cache/* \
		$(top_distdir)/missing $(top_distdir)/Makefile.in
