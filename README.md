nginx-cmake
-----------

Sometimes you need to integrate Nginx build into a larger project.  If
that project uses CMake, you have two options. Either try to wrap
native Nginx build system using ExternalProject_Add(), or to rewrite
build steps in CMake language.

Former is easier at start, but you lose control over that build part.
Incremental builds become fragile, as CMake dependency extractor is
not working for external projects.

Latter is a lot harder, but what you get is uniform build scripts, all
in CMake. It's more reliable, and produces way less of clutter on a
screen during build.

This repository contains solution in the second way. Scripts in
CMake. There are:

* (outdated) direct rewrite of Nginx's build system in
  [/direct-rewrite](/direct-rewrite);
* tracing script approach in [/tracing-script](/tracing-script).

Direct rewrite was a first attempt to make a CMake build script by
manually reimplementing Nginx's build scripts. It targeted Nginx
1.11.6 and Linux, with other OS support dropped right away. That
script most probably won't work for other Nginx versions, and
definitely won't work on an OS other than GNU/Linux. There is also no
dynamic modules support code.

Tracing script is a hack that by intercepting compiler (`CC` and `CXX`
variables) learns what files to compile and what objects and libraries
to link. There are more detailed explanations inside the script.
