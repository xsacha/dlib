# Copyright (C) 2015-2018 Ruslan Baratov
# License: Boost Software License
# See LICENSE.txt for the full license.

cmake_minimum_required(VERSION 3.2)

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.19.84.tar.gz"
    SHA1 "9086d4b3c32784effdd6f83f45125b55cf95aae8"
)

project(dlib VERSION 19.8)

get_directory_property(has_parent PARENT_DIRECTORY)
if(NOT has_parent)
   # Set this so that the dlib subfolder will build both a static and shared
   # library, since the only reason to build this CMakeLists.txt by itself is
   # if you want to install dlib.  It should be noted however that installing
   # dlib is not necessary.  A simpler approach is to use it the way shown in
   # examples/CMakeLists.txt 
   set(DLIB_IN_PROJECT_BUILD false)
endif()

add_subdirectory(dlib)
