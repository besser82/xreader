SUBDIRS = mdvi-lib

AM_CPPFLAGS = 					\
	-I$(top_srcdir)				\
	-I$(top_srcdir)/libdocument		\
	-I$(srcdir)/mdvi-lib			\
	-DXREADER_LOCALE_DIR=\"$(datadir)/locale\"	\
	-DXREADER_COMPILATION			\
	$(WARN_CFLAGS)				\
	$(BACKEND_CFLAGS)			\
	$(SPECTRE_CFLAGS)			\
	$(DISABLE_DEPRECATED)

backend_LTLIBRARIES = libdvidocument.la

libdvidocument_la_SOURCES = 	\
	dvi-document.c		\
	dvi-document.h  	\
	cairo-device.c		\
	cairo-device.h		\
	fonts.c			\
	fonts.h

libdvidocument_la_LDFLAGS = $(BACKEND_LIBTOOL_FLAGS)
libdvidocument_la_LIBADD = 				\
	mdvi-lib/libmdvi.la				\
	-lkpathsea					\
	$(top_builddir)/libdocument/libxreaderdocument.la	\
	$(BACKEND_LIBS)					\
	$(SPECTRE_LIBS)

if WITH_TYPE1_FONTS
libdvidocument_la_LIBADD += -lt1
endif

backend_in_files = dvidocument.xreader-backend.in
backend_DATA = $(backend_in_files:.xreader-backend.in=.xreader-backend)

EXTRA_DIST = $(backend_in_files)

CLEANFILES = $(backend_DATA)

@EV_INTLTOOL_XREADER_BACKEND_RULE@

-include $(top_srcdir)/git.mk
