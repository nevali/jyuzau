## Copyright 2014 Mo McRoberts.
##
##  Licensed under the Apache License, Version 2.0 (the "License");
##  you may not use this file except in compliance with the License.
##  You may obtain a copy of the License at
##
##      http://www.apache.org/licenses/LICENSE-2.0
##
##  Unless required by applicable law or agreed to in writing, software
##  distributed under the License is distributed on an "AS IS" BASIS,
##  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
##  See the License for the specific language governing permissions and
##  limitations under the License.

AC_INIT([jyuzau],m4_esyscmd([/bin/sh engine/m4/get-version.sh]),)
AC_CONFIG_MACRO_DIR([engine/m4])
AC_CONFIG_AUX_DIR([engine])

orig_CFLAGS="$CFLAGS"
orig_CXXFLAGS="$CXXFLAGS"
orig_OBJCFLAGS="$OBJCFLAGS"
orig_OBJCXXFLAGS="$OBJCCXXFLAGS"

AM_INIT_AUTOMAKE([foreign])
AM_MAINTAINER_MODE

BT_PROG_XCODE
AC_PROG_CC
AC_PROG_CXX
AC_PROG_OBJC
AC_PROG_OBJCXX

# If autoconf magic set CFLAGS to include -O2, change it to -O0
if test x"$orig_CFLAGS" = x"" ; then
	if test x"$CFLAGS" = x"-g -O2" ; then
		CFLAGS="-g -O0"
	elif test x"$CFLAGS" = x"-O2" ; then
		CFLAGS="-O0"
	fi
fi
if test x"$orig_CXXFLAGS" = x"" ; then
	if test x"$CXXFLAGS" = x"-g -O2" ; then
		CXXFLAGS="-g -O0"
	elif test x"$CXFLAGS" = x"-O2" ; then
		CXXFLAGS="-O0"
	fi
fi
if test x"$orig_OBJCFLAGS" = x"" ; then
	if test x"$OBJCFLAGS" = x"-g -O2" ; then
		OBJCFLAGS="-g -O0"
	elif test x"$OBJCFLAGS" = x"-O2" ; then
		OBJCFLAGS="-O0"
	fi
fi
if test x"$orig_OBJCXXFLAGS" = x"" ; then
	if test x"$OBJCXXFLAGS" = x"-g -O2" ; then
		OBJCXXFLAGS="-g -O0"
	elif test x"$OBJCXXFLAGS" = x"-O2" ; then
		OBJCXXFLAGS="-O0"
	fi
fi


LT_INIT

AC_SUBST([AM_CPPFLAGS])
AC_SUBST([AM_CFLAGS])
AC_SUBST([AM_CXXFLAGS])
AC_SUBST([AM_LDFLAGS])

AC_CONFIG_SUBDIRS([engine])

BT_REQUIRE_LIBXML2

ENGINE_CPPFLAGS="-I\${top_builddir}/engine/libjyuzau -I\${top_builddir}/engine/sdk/include -I\${top_builddir}/engine/sdk/include/OGRE -I\${top_builddir}/sdk/include/OGRE/Overlay -I\${top_builddir}/engine/sdk/include/bullet -F\${top_builddir}/engine/sdk/Frameworks"
ENGINE_LDFLAGS="-L\${top_builddir}/engine/sdk/lib -F\${top_builddir}/engine/sdk/Frameworks"
ENGINE_LIBS="\${top_builddir}/engine/libjyuzau/libjyuzau.la -framework Cocoa -framework Foundation"

AC_SUBST([ENGINE_CPPFLAGS])
AC_SUBST([ENGINE_LDFLAGS])
AC_SUBST([ENGINE_LIBS])

AC_CONFIG_FILES([
Makefile
app/Makefile
app/Info.plist
])

AC_OUTPUT
