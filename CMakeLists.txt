# Set  the minimum  required version  of cmake  for a  project.
cmake_minimum_required(VERSION 2.8.12)

# Add an executable to the project using the specified source files.
#add_executable(tetgen tetgen.cxx predicates.cxx)

#Add a library to the project using the specified source files.
# In Linux/Unix, it will creates the libtet.a
add_library(TetGen SHARED tetgen.cxx predicates.cxx)

#Set properties on a target.
#We use this here to set -DTETLIBRARY for when compiling the
#library
set_target_properties(TetGen PROPERTIES "COMPILE_DEFINITIONS" TETLIBRARY)
set_target_properties(TetGen PROPERTIES PUBLIC_HEADER "tetgen.h")
install(TARGETS TetGen EXPORT tetTargets)
install(EXPORT tetTargets
  FILE TetGen.cmake
  NAMESPACE TetGen::
  DESTINATION lib/cmake/TetGen
 )
