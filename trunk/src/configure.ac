#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.67])
AC_INIT([sslog], [1.0], [sslog@logos.t.u-tokyo.ac.jp], [sslog], [http://code.google.com/p/sslog/])
AM_INIT_AUTOMAKE([foreign -Wall -Werror])
AC_CONFIG_HEADERS([trace_impl.h])
# AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_PROG_CC
AC_PROG_LIBTOOL
AM_PROG_CC_C_O
# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([stdlib.h string.h])

AC_ARG_WITH([java], 
  [AS_HELP_STRING([--with-java], [specify java])],
  [],
  [with_java=check])

CFLAGS="-I${with_java}/include -I${with_java}/include/linux $CFLAGS"
CPPFLAGS="-I${with_java}/include -I${with_java}/include/linux $CPPFLAGS"
AC_CHECK_HEADERS([jni.h])

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.
AC_FUNC_MALLOC
AC_CHECK_FUNCS([strstr])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
