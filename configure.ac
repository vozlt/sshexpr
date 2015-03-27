# -*- Autoconf -*-
#
# @file: configure.ac
# @brief: Process this file with autoconf to produce a configure script
# @author: YoungJoo.Kim <vozlt@vozlt.com>
# @version:
# @date:

AC_PREREQ(2.63)

AC_INIT([deploy], [1.0], [vozlt@vozlt.com])
AC_PREFIX_DEFAULT([/usr/local])

AC_SUBST(bashpath)
AC_SUBST(bashlib)

AC_ARG_WITH(bash,
[  --with-bash=PATH        bash path (Default: system)])

AC_ARG_WITH(bash-lib,
[  --with-bash-lib=PATH    bash lib path (Default: system)])

# Checks for programs.
AC_PROG_INSTALL


# bash
if test "x$with_bash" != "x"; then
	if test -f $with_bash ; then
		AC_MSG_CHECKING(for bash)
		AC_MSG_RESULT([$with_bash])
		bashpath=$with_bash
	else
		AC_PATH_PROG(BASH, bash)
		if test "x$ac_cv_path_BASH " != "x"; then
			bashpath=$ac_cv_path_BASH
		else
			AC_MSG_ERROR(Can't not found bash)
		fi
	fi
else
	AC_PATH_PROG(BASH, bash)
	if test "x$ac_cv_path_BASH " != "x"; then
		bashpath=$ac_cv_path_BASH
	else
		AC_MSG_ERROR(Can't not found bash)
	fi
fi

# bashlib
if test "x$with_bash_lib" != "x"; then
	AC_MSG_CHECKING(for bashlib)
	if test "x$with_bash_lib" = "xyes"; then
		bashlib=/usr/share/sshexpr/common/bash
	else
		bashlib=$with_vendor_lib
	fi
	AC_MSG_RESULT([$bashlib])
fi


AC_PATH_PROG(MAKE, make)
if test ! -f "$ac_cv_path_MAKE"; then
	AC_MSG_ERROR(Can't not found make)
fi

AC_PATH_PROG(RM, rm)
if test ! -f "$ac_cv_path_RM"; then
	AC_MSG_ERROR(Can't not found rm)
fi

AC_PATH_PROG(SED, sed)
if test ! -f "$ac_cv_path_SED"; then
	AC_MSG_ERROR(Can't found sed)
fi

AC_PATH_PROG(SSH, ssh)
if test ! -f "$ac_cv_path_SSH"; then
	AC_MSG_ERROR(Can't found ssh)
fi

AC_PATH_PROG(SCP, scp)
if test ! -f "$ac_cv_path_SCP"; then
	SCP=
	#AC_MSG_ERROR(Can't found scp)
fi

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
