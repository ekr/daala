# Libraries

lib_LTLIBRARIES = src/libdaalabase.la src/libdaaladec.la src/libdaalaenc.la

noinst_HEADERS = \
	src/adapt.h \
	src/block_size.h \
	src/block_size_dec.h \
	src/block_size_enc.h \
	src/dct.h \
	src/decint.h \
	src/encint.h \
	src/entcode.h \
	src/entdec.h \
	src/entenc.h \
	src/filter.h \
	src/generic_code.h \
	src/internal.h \
	src/intra.h \
        src/logging.h \
	src/mc.h \
	src/odintrin.h \
	src/pvq.h \
	src/pvq_code.h \
	src/state.h \
	src/tf.h

src_libdaalabase_la_CFLAGS = $(OGG_CFLAGS)
src_libdaalabase_la_LIBADD = $(OGG_LIBS)
if DUMP_IMAGES
  src_libdaalabase_la_LIBADD += $(PNG_LIBS)
endif
src_libdaalabase_la_LDFLAGS = -no-undefined \
 -version-info @OD_LT_CURRENT@:@OD_LT_REVISION@:@OD_LT_AGE@
src_libdaalabase_la_LDFLAGS += 
src_libdaalabase_la_SOURCES = \
	src/adapt.c \
	src/block_size.c \
	src/entcode.c \
	src/entdec.c \
	src/entenc.c \
	src/filter.c \
	src/generic_code.c \
	src/generic_decoder.c \
	src/generic_encoder.c \
	src/info.c \
	src/internal.c \
	src/intra.c \
	src/intradata.c \
	src/laplace_tables.c \
	src/logging.c \
	src/mc.c \
	src/newdct.c \
	src/pvq.c \
	src/pvq_decoder.c \
	src/pvq_encoder.c \
	src/state.c \
	src/switch_table.c \
	src/tf.c
if ENABLE_X86ASM
src_libdaalabase_la_SOURCES += \
	src/x86/cpu.c \
	src/x86/cpu.h \
	src/x86/x86int.h \
	src/x86/sse2mc.c \
	src/x86/x86state.c
endif

src_libdaaladec_la_CFLAGS = $(OGG_CFLAGS)
src_libdaaladec_la_LIBADD = src/libdaalabase.la $(OGG_LIBS)
if DUMP_IMAGES
  src_libdaaladec_la_LIBADD += $(PNG_LIBS)
endif
src_libdaaladec_la_LDFLAGS = -no-undefined \
 -version-info @OD_LT_CURRENT@:@OD_LT_REVISION@:@OD_LT_AGE@
src_libdaaladec_la_SOURCES = \
	src/block_size_dec.c \
	src/decode.c

src_libdaalaenc_la_CFLAGS = $(OGG_CFLAGS)
src_libdaalaenc_la_LIBADD = src/libdaalabase.la $(OGG_LIBS)
if DUMP_IMAGES
  src_libdaalaenc_la_LIBADD += $(PNG_LIBS)
endif
src_libdaalaenc_la_LDFLAGS = -no-undefined \
 -version-info @OD_LT_CURRENT@:@OD_LT_REVISION@:@OD_LT_AGE@
src_libdaalaenc_la_SOURCES = \
	src/block_size_dec.c \
	src/block_size_enc.c \
	src/encode.c \
	src/decode.c \
	src/infoenc.c \
	src/mcenc.c


# Example programs

noinst_PROGRAMS = \
	examples/dump_video \
	examples/encoder_example \
	examples/player_example

examples_dump_video_SOURCES = examples/dump_video.c
examples_dump_video_CFLAGS = $(OGG_CFLAGS)
examples_dump_video_LDADD = src/libdaalabase.la src/libdaaladec.la  $(OGG_LIBS)
if DUMP_IMAGES
  examples_dump_video_LDADD += $(PNG_LIBS)
endif

examples_encoder_example_SOURCES = examples/encoder_example.c
examples_encoder_example_CFLAGS = $(OGG_CFLAGS)
examples_encoder_example_LDADD = src/libdaalabase.la src/libdaalaenc.la $(OGG_LIBS) -lm
if DUMP_IMAGES
  examples_encoder_example_LDADD += $(PNG_LIBS)
endif

examples_player_example_SOURCES = examples/player_example.c
examples_player_example_CFLAGS = $(OGG_CFLAGS)
examples_player_example_LDADD = src/libdaalabase.la src/libdaalaenc.la $(OGG_LIBS)
if DUMP_IMAGES
  examples_player_example_LDADD += $(PNG_LIBS)
endif

# Includes

daalaincludedir = ${includedir}/daala
daalainclude_HEADERS = \
	include/daala/codec.h \
	include/daala/daaladec.h \
	include/daala/daalaenc.h

# Tools

noinst_PROGRAMS += \
	tools/png2y4m \
	tools/y4m2png \
	tools/dump_psnrhvs \
	tools/block_size_analysis \
	tools/plot_intra_maps \
	tools/init_intra_maps \
	tools/intra_stats \
	tools/intra_pred \
	tools/intra_trace \
	tools/trans \
	tools/trans2d \
	tools/init_intra_xform \
	tools/gen_cdf \
	tools/gen_laplace_tables

noinst_HEADERS += \
	tools/cholesky.h \
	tools/image.h \
	tools/image_tools.h \
	tools/int_search.h \
	tools/intra_fit_tools.h \
	tools/kiss99.h \
	tools/matidx.h \
	tools/od_covmat.h \
	tools/od_defs.h \
	tools/od_filter.h \
	tools/od_intra.h \
	tools/pythag.h \
	tools/stats_tools.h \
	tools/svd.h \
	tools/trans_tools.h \
	tools/vidinput.h

# png2y4m
tools_png2y4m_SOURCES = \
	tools/kiss99.c \
	tools/png2y4m.c
tools_png2y4m_CFLAGS = $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_png2y4m_LDADD = $(OGG_LIBS) $(PNG_LIBS)

# y4m2png
tools_y4m2png_SOURCES = \
	tools/vidinput.c \
	tools/y4m2png.c
tools_y4m2png_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_y4m2png_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS)

# dump_psnrhvs
tools_dump_psnrhvs_SOURCES = \
	tools/vidinput.c \
	src/newdct.c \
	tools/dump_psnrhvs.c
tools_dump_psnrhvs_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_dump_psnrhvs_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# block_size_analysis
tools_block_size_analysis_SOURCES = \
	tools/block_size_analysis.c \
	src/block_size.c \
	src/block_size_enc.c \
	tools/vidinput.c \
	src/newdct.c \
	src/internal.c \
	src/entcode.c \
	src/entenc.c \
	src/filter.c \
	src/switch_table.c
tools_block_size_analysis_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_block_size_analysis_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# plot_intra_maps
tools_plot_intra_maps_SOURCES = \
	tools/image.c \
	tools/plot_intra_maps.c \
	tools/intra_fit_tools.c \
	tools/vidinput.c
tools_plot_intra_maps_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_plot_intra_maps_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# init_intra_maps
tools_init_intra_maps_SOURCES = \
	tools/init_intra_maps.c \
	tools/intra_fit_tools.c \
	tools/vidinput.c
tools_init_intra_maps_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_init_intra_maps_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# intra_stats
tools_intra_stats_SOURCES = \
	tools/intra_stats.c \
	tools/intra_fit_tools.c \
	tools/od_covmat.c \
	tools/od_filter.c \
	tools/od_intra.c \
	tools/od_intra_data.c \
	tools/image_tools.c \
	tools/stats_tools.c \
	tools/vidinput.c \
	tools/image.c \
	src/filter.c \
	src/newdct.c \
	src/intra.c \
	src/tf.c \
	src/internal.c \
	src/intradata.c
tools_intra_stats_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS) -fopenmp
tools_intra_stats_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# intra_pred
tools_intra_pred_SOURCES = \
	tools/intra_pred.c \
	tools/intra_fit_tools.c \
	tools/od_covmat.c \
	tools/od_filter.c \
	tools/od_intra.c \
	tools/od_intra_data.c \
	tools/image_tools.c \
	tools/stats_tools.c \
	tools/vidinput.c \
	tools/image.c \
	tools/svd.c \
	tools/cholesky.c \
	src/filter.c \
	src/newdct.c \
	src/intra.c \
	src/intradata.c \
	src/internal.c \
	src/tf.c
tools_intra_pred_CFLAGS = $(OGG_CFLAGS) $(PNG_CFLAGS) -fopenmp
tools_intra_pred_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# intra_trace
tools_intra_trace_SOURCES = \
	tools/intra_trace.c \
	tools/intra_fit_tools.c \
	tools/od_covmat.c \
	tools/od_filter.c \
	tools/od_intra.c \
	tools/od_intra_data.c \
	tools/image_tools.c \
	tools/stats_tools.c \
	tools/trans_tools.c \
	tools/vidinput.c \
	tools/image.c \
	src/filter.c \
	src/newdct.c \
	src/intra.c \
	src/tf.c \
	src/internal.c \
	src/intradata.c
tools_intra_trace_CFLAGS = $(OGG_CFLAGS) $(PNG_CFLAGS) -fopenmp
tools_intra_trace_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# trans
tools_trans_SOURCES = \
	tools/trans.c \
	src/internal.c \
	tools/intra_fit_tools.c \
	tools/vidinput.c \
	tools/od_covmat.c \
	tools/od_filter.c \
	tools/od_intra.c \
	tools/od_intra_data.c \
	tools/stats_tools.c \
	tools/trans_tools.c \
	tools/int_search.c \
	tools/trans_data.c \
	tools/kiss99.c \
	tools/image.c \
	tools/svd.c \
	tools/cholesky.c \
	src/filter.c \
	src/newdct.c \
	src/intradata.c
tools_trans_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS) -fopenmp
tools_trans_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

#trans2d
tools_trans2d_SOURCES = \
	tools/trans2d.c \
	src/internal.c \
	tools/intra_fit_tools.c \
	tools/vidinput.c \
	tools/od_covmat.c \
	tools/od_filter.c \
	tools/od_intra.c \
	tools/od_intra_data.c \
	tools/stats_tools.c \
	tools/trans_tools.c \
	tools/int_search.c \
	tools/trans_data.c \
	tools/kiss99.c \
	tools/image.c \
	tools/svd.c \
	tools/cholesky.c \
	src/filter.c \
	src/newdct.c \
	src/intradata.c
tools_trans2d_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS) -fopenmp
tools_trans2d_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# init_intra_xform
tools_init_intra_xform_SOURCES = \
	tools/cholesky.c \
	tools/init_intra_xform.c \
	tools/intra_fit_tools.c \
	tools/svd.c \
	tools/vidinput.c \
	src/filter.c \
	src/newdct.c \
	src/intra.c \
	src/tf.c \
	src/internal.c \
	src/intradata.c
tools_init_intra_xform_CFLAGS = $(THEORA_CFLAGS) $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_init_intra_xform_LDADD = $(THEORA_LIBS) $(OGG_LIBS) $(PNG_LIBS) -lm

# gen_cdf
tools_gen_cdf_SOURCES = \
	tools/gen_cdf.c
tools_gen_cdf_CFLAGS = $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_gen_cdf_LDADD = $(OGG_LIBS) $(PNG_LIBS) -lm

# gen_laplace_tables
tools_gen_laplace_tables_SOURCES = \
	tools/gen_laplace_tables.c
tools_gen_laplace_tables_CFLAGS = $(OGG_CFLAGS) $(PNG_CFLAGS)
tools_gen_laplace_tables_LDADD = $(OGG_LIBS) $(PNG_LIBS) -lm


# Tests

noinst_PROGRAMS += \
	src/tests/ectest \
	src/tests/test_coef_coder \
	src/tests/logging_test

TESTS = \
	src/tests/ectest \
	src/tests/test_coef_coder \
	src/tests/logging_test

src_tests_ectest_SOURCES = src/tests/ectest.c
src_tests_ectest_CFLAGS = $(OGG_CFLAGS)
src_tests_ectest_LDADD = -lm

src_tests_test_coef_coder_SOURCES = src/tests/test_coef_coder.c
src_tests_test_coef_coder_CFLAGS = $(OGG_CFLAGS)	
src_tests_test_coef_coder_LDADD = src/libdaalabase.la src/libdaaladec.la $(OGG_LIBS) -lm

src_tests_logging_test_SOURCES = src/tests/logging_test.c
src_tests_logging_test_CFLAGS = $(OGG_CFLAGS)	
src_tests_logging_test_LDADD = src/libdaalabase.la src/libdaalaenc.la  $(OGG_LIBS)


# Docs

if ENABLE_DOCS
# Generate the paper from its sources.
# Requires transfig and pdflatex.

PAPER_SRCS = \
	doc/mc.tex \
	doc/daala.bib

FIG_SRCS = \
	doc/4-8sub.fig \
	doc/mvpred.fig
FIG_TEX_SRCS = blockidx.fig vbunsplit.fig

FIG_OBJS = \
	$(FIG_SRCS:.fig=.pdf) \
	$(FIG_TEX_SRCS:.fig=.pdftex) \
	$(FIG_TEX_SRCS:.fig=.pdftex_t)

#noinst_DATA = mc.pdf

CLEANFILES = \
	doc/mc.pdf \
	doc/mc.out \
	doc/mc.log \
	doc/mc.blg \
	doc/mc.bbl \
	doc/mc.aux \
	doc/blockidx.pdftex \
	doc/blockidx.pdftex_t \
	doc/vbunsplit.pdftex \
	doc/vbunsplit.pdftex_t \
	doc/mvpred.pdf \
	doc/4-8sub.pdf

mc.pdf : $(PAPER_SRCS) $(FIG_OBJS) $(EXTRA_FIGS) mc.bbl
	pdflatex mc
	pdflatex mc

mc.bbl : $(PAPER_SRCS) $(FIG_OBJS) $(EXTRA_FIGS)
	if [ mc.tex -nt mc.aux ] ; then pdflatex mc ; fi
	bibtex mc

figures : $(FIG_OBJS)

# rule to generate latex versions of the xfig figures
%.tex : %.fig
	fig2dev -L latex $< $@

%.pdf : %.fig
	fig2dev -L pdf -p 0 $< $@

%.pdftex : %.fig
	fig2dev -L pdftex -p 0 $< $@

%.pdftex_t : %.fig
	fig2dev -L pdftex_t -p $(<:.fig=.pdftex) $< $@
endif

ACLOCAL_AMFLAGS = -I m4

AM_CFLAGS = -I$(top_srcdir)/include $(DEPS_CFLAGS)

dist_doc_DATA = COPYING AUTHORS README.txt

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = daala.pc

debug:
	$(MAKE) CFLAGS="${CFLAGS} -O0 -ggdb -DOP_ENABLE_ASSERTIONS" all

EXTRA_DIST = \
	daala.pc.in \
	daala-uninstalled.pc.in \
	tools/unix/Makefile \
	unix/Makefile

# Targets to build and install just the library without the docs
daala install-daala: NO_DOXYGEN = 1

daala: all
install-daala: install

# Or just the docs
#docs: doc/doxygen-build.stamp

install-docs:
	@if [ -z "$(NO_DOXYGEN)" ]; then \
	  ( cd doc && \
	    echo "Installing documentation in $(DESTDIR)$(docdir)"; \
	    $(INSTALL) -d $(DESTDIR)$(docdir)/html/search; \
	    for f in `find html -type f \! -name "installdox"` ; do \
	      $(INSTALL_DATA) $$f $(DESTDIR)$(docdir)/$$f;     \
	    done ) \
	fi

doc/doxygen-build.stamp: doc/Doxyfile $(top_srcdir)/doc/daala_logo.svg \
                         $(top_srcdir)/include/*.h
	@[ -n "$(NO_DOXYGEN)" ] || ( cd doc && doxygen && touch $(@F) )


if HAVE_DOXYGEN

# Or everything (by default)
all-local: docs

install-data-local: install-docs

clean-local:
	$(RM) -r doc/html
	$(RM) -r doc/latex
	$(RM) doc/doxygen-build.stamp

uninstall-local:
	$(RM) -r $(DESTDIR)$(docdir)/html

endif

# We check this every time make is run, with configure.ac being touched to
# trigger an update of the build system files if update_version changes the
# current PACKAGE_VERSION (or if package_version was modified manually by a
# user with either AUTO_UPDATE=no or no update_version script present - the
# latter being the normal case for tarball releases).
#
# We can't just add the package_version file to CONFIGURE_DEPENDENCIES since
# simply running autoconf will not actually regenerate configure for us when
# the content of that file changes (due to autoconf dependency checking not
# knowing about that without us creating yet another file for it to include).
#
# The MAKECMDGOALS check is a gnu-make'ism, but will degrade 'gracefully' for
# makes that don't support it.  The only loss of functionality is not forcing
# an update of package_version for `make dist` if AUTO_UPDATE=no, but that is
# unlikely to be a real problem for any real user.
$(top_srcdir)/configure.ac: force
	@case "$(MAKECMDGOALS)" in \
	    dist-hook)                             exit 0       ;; \
	    dist-* | dist | distcheck | distclean) _arg=release ;; \
	esac; \
	if ! $(top_srcdir)/update_version $$_arg 2> /dev/null; then \
	    if [ ! -e $(top_srcdir)/package_version ]; then \
		echo 'PACKAGE_VERSION="unknown"' > $(top_srcdir)/package_version; \
	    fi; \
	    . $(top_srcdir)/package_version || exit 1; \
	    [ "$(PACKAGE_VERSION)" != "$$PACKAGE_VERSION" ] || exit 0; \
	fi; \
	touch $@

force:

# Create a minimal package_version file when make dist is run.
dist-hook:
	echo 'PACKAGE_VERSION="$(PACKAGE_VERSION)"' > $(top_distdir)/package_version

.PHONY: daala install-daala docs install-docs figures
