dnl Process this file with autoconf to produce a configure script
AC_PREREQ([2.60])
AC_INIT([cmockery], [0.1.5], [p.hosek@imperial.ac.uk])

AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE([foreign silent-rules subdir-objects color-tests -Wall -Werror])
AM_MAINTAINER_MODE
LT_INIT

AC_LANG([C])

dnl Toolchain checks
AC_PROG_CC_C99
if test x"$ac_cv_prog_cc_c99" = x"no"; then
	AC_MSG_ERROR([C compiler supporting C99 required])
fi

AC_PROG_LIBTOOL
AC_SUBST([LIBTOOL_DEPS])

AM_PROG_CC_C_O
AM_PROG_AS

dnl Checks for typedefs
AC_TYPE_SIZE_T
AC_TYPE_SIGNAL

dnl Check for sizes
AC_CHECK_SIZEOF([int])
AC_CHECK_SIZEOF([long])
AC_CHECK_SIZEOF([long long])

dnl Checks for header files
AC_HEADER_ASSERT
AC_HEADER_STDBOOL
AC_HEADER_STDC

AC_CHECK_HEADERS([malloc.h])
AC_CHECK_HEADERS([setjmp.h])
AC_CHECK_HEADERS([stddef.h])
AC_CHECK_HEADERS([stdio.h])

dnl Check for functions
AC_FUNC_MALLOC
AC_FUNC_VPRINTF

AC_CHECK_FUNCS([setjmp])
AC_CHECK_FUNCS([longjmp])
AC_CHECK_FUNCS([strcmp])
AC_CHECK_FUNCS([strcpy])
AC_CHECK_FUNCS([calloc])
AC_CHECK_FUNCS([free])
AC_CHECK_FUNCS([exit])
AC_CHECK_FUNCS([printf])
AC_CHECK_FUNCS([fprintf])
AC_CHECK_FUNCS([snprintf])

dnl Configuration files
AC_CONFIG_HEADERS([lib/config.h])
AC_CONFIG_FILES([Makefile])

dnl Doxygen documentation
DX_INIT_DOXYGEN([libcmockery], [Doxyfile])
DX_DOXYGEN_FEATURE([ON])

AC_OUTPUT
