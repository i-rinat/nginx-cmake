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
CMake. There is direct rewrite of Nginx's build system in
*/direct-rewrite* directory. And also tracing script approach in
directory */tracing-script*.
