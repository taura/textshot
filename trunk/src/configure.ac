#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.67])
AC_INIT([sslog], [1.0], [sslog@logos.t.u-tokyo.ac.jp], [sslog], [http://code.google.com/p/sslog/])
AM_INIT_AUTOMAKE([foreign -Wall -Werror])
AC_CONFIG_HEADERS([trace_impl.h])
AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_PROG_CC
AC_PROG_LIBTOOL
AM_PROG_CC_C_O
# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([stdlib.h string.h])

# Checks for typedefs, structures, and compiler characteristics.

AC_CHECK_SIZEOF([int])
AC_CHECK_SIZEOF([long])
AC_CHECK_SIZEOF([long long])
AC_CHECK_SIZEOF([int64_t])
AC_CHECK_SIZEOF([void *])

# Checks for library functions.
AC_FUNC_MALLOC
AC_CHECK_FUNCS([strstr])

# checks for Java
AC_ARG_WITH([java], 
  [AS_HELP_STRING([--with-java], [specify java home directory X, in which to find X/bin/java])])
AC_CHECK_FILES([${with_java}/bin/java], [], 
  [AC_MSG_ERROR([java command not found. use --with-java to specify java home])])
AC_SUBST([default_jvm], [${with_java}/bin/java])

# add JAVA_HOME/include and JAVA_HOME/include/OS_TYPE 
# (e.g., JAVA_HOME/include/linux) to CFLAGS and CPPFLAGS

AC_CHECK_FILES([${with_java}/include], 
  [AC_SUBST([CFLAGS], ["${CFLAGS} -I${with_java}/include"])
  AC_SUBST([CPPFLAGS], ["${CPPFLAGS} -I${with_java}/include"])])

AC_SUBST([host_brief], [$(echo ${host_os} | sed s/-gnu//g)])

AC_CHECK_FILES([${with_java}/include/${host_brief}], 
  [AC_SUBST([CFLAGS], ["${CFLAGS} -I${with_java}/include/${host_brief}"])
   AC_SUBST([CPPFLAGS], ["${CPPFLAGS} -I${with_java}/include/${host_brief}"])])


AC_CHECK_HEADERS([jni.h], [], 
  [AC_MSG_ERROR([jni.h not found in -I${with_java}/include. are you sure using Sun JDK?])])

# checks for jumpshot
AC_ARG_WITH([jumpshot], 
  [AS_HELP_STRING([--with-jumpshot], [specify jumpshot install directory X, in which to find X/lib/traceTOslog2.jar])],
  [],
  [with_jumpshot=build])

AS_IF([ test "x${with_jumpshot}" = xbuild ],
  [ AC_MSG_NOTICE([--with-jumpshot not specified, going to install jumpshot to ${prefix}])
    AC_SUBST([compile_jumpshot_too], [compile_jumpshot_too])
    AC_SUBST([with_jumpshot], [${prefix}]) ],
  [ AC_CHECK_FILES([${with_jumpshot}/lib/traceTOslog2.jar], [],
      [AC_MSG_ERROR([traceTOslog2.jar not found in ${with_jumpshot}/lib])]) ])

AC_SUBST([jumpshot_dir], [${with_jumpshot}])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
