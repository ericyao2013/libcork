# -*- coding: utf-8 -*-
# ------------------------------------------------------------------------------
# Copyright © 2018, libcork authors
# Please see the COPYING file in this distribution for license details.
# ------------------------------------------------------------------------------

#-------------------------------------------------------------------------------
# Preliminaries

ACLOCAL_AMFLAGS = -I m4
AM_CPPFLAGS = \
	-I$(top_srcdir)/include
lib_LTLIBRARIES = \
	libcork.la
check_LTLIBRARIES = libtests.la
check_PROGRAMS = \
	tests/test-bfs \
	tests/test-csp0 \
	tests/test-denotational \
	tests/test-environment \
	tests/test-equivalences \
	tests/test-events \
	tests/test-event-sets \
	tests/test-id-sets \
	tests/test-process-sets \
	tests/test-operators \
	tests/test-refinement
bin_PROGRAMS = libcork
TESTS = ${check_PROGRAMS}
LOG_DRIVER = env AM_TAP_AWK='$(AWK)' $(SHELL) $(top_srcdir)/tap-driver.sh
@VALGRIND_CHECK_RULES@

EXTRA_DIST = tap-driver.sh third_party
dist-hook:
	@rm -f `find $(top_distdir)/third_party -name $(am__dirstamp)`
	@rm -f `find $(top_distdir)/third_party -name '*.o'`
	@rm -f `find $(top_distdir)/third_party -name '*.lo'`
	@rm -rf `find $(top_distdir)/third_party -type d -name $(DEPDIR)`
	@rm -rf `find $(top_distdir)/third_party -type d -name .libs`

#-------------------------------------------------------------------------------
# libcork and tests

liblibcork_la_SOURCES = \
	src/basics.h \
	src/behavior.h \
	src/behavior.c \
	src/csp0.h \
	src/csp0.c \
	src/denotational.h \
	src/denotational.c \
	src/environment.h \
	src/environment.c \
	src/equivalence.h \
	src/equivalence.c \
	src/event.h \
	src/event.c \
	src/id-set.h \
	src/id-set.c \
	src/macros.h \
	src/map.h \
	src/map.c \
	src/normalization.h \
	src/normalization.c \
	src/process.h \
	src/process.c \
	src/refinement.h \
	src/refinement.c \
	src/set.h \
	src/set.c \
	src/operators.h \
	src/operators/external-choice.c \
	src/operators/interleave.c \
	src/operators/internal-choice.c \
	src/operators/prefix.c \
	src/operators/recursion.c \
	src/operators/sequential-composition.c \
	third_party/ccan/build_assert/build_assert.h \
	third_party/ccan/compiler/compiler.h \
	third_party/ccan/container_of/container_of.h \
	third_party/ccan/hash/hash.h \
	third_party/ccan/hash/hash.c \
	third_party/ccan/likely/likely.h
liblibcork_la_LDFLAGS = -export-symbols-regex '^csp_[^_]'
liblibcork_la_LIBADD = libjudy.la

libtests_la_SOURCES = \
	tests/test-cases.h \
	tests/test-case-harness.h \
	third_party/ccan/compiler/compiler.h \
	third_party/ccan/cppmagic/cppmagic.h \
	third_party/ccan/likely/likely.h

libcork_SOURCES = \
	src/libcork/has-trace.c.in \
	src/libcork/libcork.c \
	src/libcork/reachable.c.in \
	src/libcork/traces.c.in
libcork_LDADD = liblibcork.la

LDADD = liblibcork.la libtests.la
tests_test_bfs_LDFLAGS = -no-install
tests_test_csp0_LDFLAGS = -no-install
tests_test_denotational_LDFLAGS = -no-install
tests_test_environment_LDFLAGS = -no-install
tests_test_equivalences_LDFLAGS = -no-install
tests_test_events_LDFLAGS = -no-install
tests_test_event_sets_LDFLAGS = -no-install
tests_test_id_sets_LDFLAGS = -no-install
tests_test_operators_LDFLAGS = -no-install
tests_test_process_sets_LDFLAGS = -no-install
tests_test_refinement_LDFLAGS = -no-install

dist_doc_DATA = README.md
