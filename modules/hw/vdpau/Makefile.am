vdpaudir = $(pluginsdir)/vdpau
# Install the pkglib/pkglibexec first before relinking the modules.
# This ensures libtool re-linking is not racy.
installvpdauLTLIBRARIES = install-vdpauLTLIBRARIES
$(installvpdauLTLIBRARIES): install-pkglibLTLIBRARIES


libvlc_vdpau_la_SOURCES = hw/vdpau/vlc_vdpau.c hw/vdpau/vlc_vdpau.h
libvlc_vdpau_la_CFLAGS = $(VDPAU_CFLAGS)
libvlc_vdpau_la_LIBADD = $(X_LIBS) $(X_PRE_LIBS) -lX11 $(LIBDL)
libvlc_vdpau_la_LDFLAGS = \
	-no-undefined \
	-export-symbols-regex ^vdp_ \
	-version-info 0:0:0

libvdpau_instance_plugin_la_SOURCES = hw/vdpau/device.c
libvdpau_instance_plugin_la_CFLAGS = $(AM_CFLAGS) $(X_CFLAGS) $(VDPAU_CFLAGS)
libvdpau_instance_plugin_la_LIBADD = libvlc_vdpau.la \
	$(X_LIBS) $(X_PRE_LIBS) -lX11

libvdpau_avcodec_plugin_la_SOURCES = hw/vdpau/avcodec.c hw/vdpau/picture.c
libvdpau_avcodec_plugin_la_CFLAGS = $(AM_CFLAGS) \
	$(AVCODEC_CFLAGS) $(VDPAU_CFLAGS)
libvdpau_avcodec_plugin_la_LIBADD = libvlc_vdpau.la $(AVCODEC_LIBS)

libvdpau_deinterlace_plugin_la_SOURCES = hw/vdpau/deinterlace.c hw/vdpau/picture.c
libvdpau_deinterlace_plugin_la_CFLAGS = $(AM_CFLAGS) $(VDPAU_CFLAGS)
libvdpau_deinterlace_plugin_la_LIBADD = libvlc_vdpau.la

libvdpau_adjust_plugin_la_SOURCES = hw/vdpau/adjust.c hw/vdpau/picture.c
libvdpau_adjust_plugin_la_CFLAGS = $(AM_CFLAGS) $(VDPAU_CFLAGS)
libvdpau_adjust_plugin_la_LIBADD = libvlc_vdpau.la

libvdpau_sharpen_plugin_la_SOURCES = hw/vdpau/sharpen.c hw/vdpau/picture.c
libvdpau_sharpen_plugin_la_CFLAGS = $(AM_CFLAGS) $(VDPAU_CFLAGS)
libvdpau_sharpen_plugin_la_LIBADD = libvlc_vdpau.la

libvdpau_chroma_plugin_la_SOURCES = hw/vdpau/chroma.c hw/vdpau/picture.c
libvdpau_chroma_plugin_la_CFLAGS = $(AM_CFLAGS) $(VDPAU_CFLAGS)
libvdpau_chroma_plugin_la_LIBADD = libvlc_vdpau.la

if HAVE_VDPAU
pkglib_LTLIBRARIES += libvlc_vdpau.la
vdpau_LTLIBRARIES = libvdpau_instance_plugin.la \
	libvdpau_deinterlace_plugin.la libvdpau_adjust_plugin.la \
	libvdpau_sharpen_plugin.la libvdpau_chroma_plugin.la
if HAVE_AVCODEC_VDPAU
vdpau_LTLIBRARIES += libvdpau_avcodec_plugin.la
endif
endif
