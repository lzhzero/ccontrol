# fetch version number
m4_include([version.m4])
# init autoconf
AC_INIT([ccontrol],[VERSION_NUMBER],[ccontrol-comits@ligforge.imag.fr])
# are we in the right source dir ?
AC_CONFIG_SRCDIR([src/commons/colorset.h])
# build tools in separate dir
AC_CONFIG_AUX_DIR([build-aux])
# macro in srcdir/m4
AC_CONFIG_MACRO_DIR([m4])

# automake should fail on any error
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
# check for programs
AC_LANG_C
AC_GNU_SOURCE
AC_PROG_CC
AC_PROG_CC_C_O
AM_PROG_CC_C_O
AC_PROG_CC_STDC
AC_PROG_CPP
AC_PROG_LIBTOOL

# support for testing with valgrind
AC_ARG_ENABLE(valgrind,
[AC_HELP_STRING([--enable-valgrind],[Also valgrind on checks (default is no).])],
[valgrind=true],[valgrind=false])

if [[ "x$valgrind" = xtrue ]]; then
	AC_PATH_PROG(VALGRIND, valgrind, no)
	if [[  "x$HAVE_VALGRIND" = xno ]]; then
		AC_MSG_ERROR([Valgrind not found in PATH. ])
	fi
fi
AM_CONDITIONAL([TEST_VALGRIND],[test "x$valgrind" = xtrue])

# configuration output in config.h
AC_CONFIG_HEADERS([config.h])
# output makefiles
AC_CONFIG_FILES([Makefile src/Makefile src/module/Makefile src/commons/Makefile src/lib/Makefile tests/Makefile src/utils/Makefile ccontrol.pc])
# do the output
AC_OUTPUT
