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

AM_CPPFLAGS = @AM_CPPFLAGS@ @ENGINE_CPPFLAGS@
AM_LDFLAGS = @AM_LDFLAGS@ @ENGINE_LDFLAGS@

bin_PROGRAMS = Jyuzau

Jyuzau_SOURCES = p_app.hh \
	main.cc app.cc

Jyuzau_LDADD = @ENGINE_LIBS@

EXTRA_DIST = Info.plist.in

noinst_DATA = plugins.cfg Info.plist

CLEANFILES = plugins.cfg Resources Frameworks assets

DISTCLEANFILES = Info.plist

plugins.cfg: ${top_builddir}/engine/sdk/bin/plugins.cfg
	rm -f $@ && cp $< $@

# For Mac OS X: fix up .libs/Contents to be a symlink back here
# For Mac OS X: link Resources to this directory
# For Mac OS X: link Frameworks to ${top_builddir}/engine/sdk/Frameworks
# Link assets to ${top_builddir}/assets
all-local:
	test -d .libs || mkdir .libs
	cd .libs && rm -f Contents && ln -s .. Contents
	rm -f Resources
	ln -s . Resources
	rm -f Frameworks
	ln -s ${top_builddir}/engine/sdk/Frameworks Frameworks
	rm -f assets
	ln -s ${top_builddir}/assets assets
