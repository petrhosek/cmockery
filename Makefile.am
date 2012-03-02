ACLOCAL_AMFLAGS = -I m4
AM_CPPFLAGS = -I$(top_srcdir)/include

MAINTAINERCLEANFILES = \
	Makefile.in

lib_LTLIBRARIES = libcmockery.la
libcmockery_la_SOURCES = \
	lib/config.h \
	lib/cmockery.c
libcmockery_la_LDFLAGS = -version-info 0:0:0
pkginclude_HEADERS = \
	include/cmockery.h

dist_doc_DATA = AUTHORS COPYING ChangeLog INSTALL NEWS README

include aminclude.am

TESTS =
XFAIL_TESTS =
TESTS_ENVIRONMENT = \
	TEST_SOURCE_DIR=$(srcdir)/tests \
	TEST_BUILD_DIR=$(top_builddir)/tests

check_PROGRAMS =
check_SCRIPTS =

unit_test_CPPFLAGS = -I$(top_srcdir)/tests -DUNIT_TESTING=1

TESTS += tests/calculator_test
check_PROGRAMS += tests/calculator_test
tests_calculator_test_SOURCES = \
	tests/calculator_test.c \
	tests/calculator.c
tests_calculator_test_CFLAGS = $(unit_test_CPPFLAGS)
tests_calculator_test_LDADD = $(top_builddir)/libcmockery.la

TESTS += tests/allocate_module_test
XFAIL_TESTS += tests/allocate_module_test
check_PROGRAMS += tests/allocate_module_test
tests_allocate_module_test_SOURCES = \
	tests/allocate_module_test.c \
        tests/allocate_module.c
tests_allocate_module_test_CFLAGS = $(unit_test_CPPFLAGS)
tests_allocate_module_test_LDADD = $(top_builddir)/libcmockery.la

TESTS += tests/assert_macro_test
XFAIL_TESTS += tests/assert_macro_test
check_PROGRAMS += tests/assert_macro_test
tests_assert_macro_test_SOURCES = \
	tests/assert_macro_test.c \
        tests/assert_macro.c
tests_assert_macro_test_CFLAGS = $(unit_test_CPPFLAGS)
tests_assert_macro_test_LDADD = $(top_builddir)/libcmockery.la

TESTS += tests/customer_database_test
XFAIL_TESTS += tests/customer_database_test
check_PROGRAMS += tests/customer_database_test
tests_customer_database_test_SOURCES = \
	tests/customer_database_test.c \
        tests/customer_database.c \
        tests/database.h
tests_customer_database_test_CFLAGS = $(unit_test_CPPFLAGS)
tests_customer_database_test_LDADD = $(top_builddir)/libcmockery.la

TESTS += tests/key_value_test
check_PROGRAMS += tests/key_value_test
tests_key_value_test_SOURCES = \
	tests/key_value_test.c \
        tests/key_value.c
tests_key_value_test_CFLAGS = $(unit_test_CPPFLAGS)
tests_key_value_test_LDADD = $(top_builddir)/libcmockery.la

TESTS += tests/product_database_test
XFAIL_TESTS += tests/product_database_test
check_PROGRAMS += tests/product_database_test
tests_product_database_testdir = tests
tests_product_database_test_SOURCES = \
	tests/product_database_test.c \
        tests/product_database.c \
        tests/database.h
tests_product_database_test_CFLAGS = $(unit_test_CPPFLAGS)
tests_product_database_test_LDADD = $(top_builddir)/libcmockery.la

rpm: dist-gzip packages/rpm.sh packages/rpm/rpm.spec
	@cd packages && ./rpm.sh ${PACKAGE} ${VERSION}

deb: dist-gzip packages/deb.sh packages/deb/*
	@cd packages && ./deb.sh ${PACKAGE} ${VERSION}

libtool: $(LIBTOOL_DEPS)
	$(SHELL) ./config.status --recheck

EXTRA_DIST = autogen.sh libtool packages/rpm.sh packages/rpm/rpm.spec packages/deb.sh packages/deb $(SCRIPTS)
