bin_PROGRAMS = $(install_clients)

AM_CFLAGS = $(GCC_CFLAGS)
AM_CPPFLAGS =					\
	-DDATADIR='"$(datadir)"'		\
	-DBINDIR='"$(bindir)"'			\
	$(CLIENT_CFLAGS) $(CAIRO_EGL_CFLAGS)

if BUILD_CLIENTS

libexec_PROGRAMS =				\
	weston-desktop-shell
	
noinst_LTLIBRARIES = libtoytoolkit.la

libtoytoolkit_la_SOURCES =			\
	window.c				\
	window.h				\
	text-cursor-position-protocol.c		\
	text-cursor-position-client-protocol.h	\
	scaler-protocol.c			\
	scaler-client-protocol.h		\
	workspaces-protocol.c			\
	workspaces-client-protocol.h

libtoytoolkit_la_LIBADD =			\
	$(CLIENT_LIBS)				\
	$(CAIRO_EGL_LIBS)			\
	../shared/libshared-cairo.la -lrt -lm

weston_desktop_shell_SOURCES =			\
	desktop-shell.c				\
	desktop-shell-client-protocol.h		\
	desktop-shell-protocol.c
weston_desktop_shell_LDADD = libtoytoolkit.la


CLEANFILES = $(BUILT_SOURCES)
endif


wayland_protocoldir = $(top_srcdir)/protocol
include $(top_srcdir)/wayland-scanner.mk
