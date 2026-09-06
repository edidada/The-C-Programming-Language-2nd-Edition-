cmake_minimum_required(VERSION 3.16)

project(The-C-Programming-Language-2nd-Edition C)

# ---------------------------------------------------------------------------
# Builds each self-contained exercise / example of the book
# "The C Programming Language" (2nd Edition) into its own executable under
# ${CMAKE_BINARY_DIR}/bin.
#
# Every chapter is added through add_subdirectory() and declares which of its
# sources must NOT be compiled standalone (helpers that only provide
# functions, multi-file programs that need extra sources, or files that
# intentionally contain broken/incomplete code).  Multi-file programs are
# declared explicitly as grouped executables in the chapter files.
# ---------------------------------------------------------------------------

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED OFF)
set(CMAKE_C_EXTENSIONS ON)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
endif()

# Many solutions are written in old K&R style (implicit int, implicit
# function declarations).  GCC >= 14 and newer Clang turn those into hard
# errors by default, so relax them back to warnings here.
if(CMAKE_C_COMPILER_ID MATCHES "GNU|Clang")
  add_compile_options(
    -Wno-implicit-int
    -Wno-implicit-function-declaration
  )
endif()

# ---------------------------------------------------------------------------
# add_exercise(<target> <src> [more srcs ...])
# Creates an executable whose binary is placed in ${CMAKE_BINARY_DIR}/bin.
# ---------------------------------------------------------------------------
function(add_exercise target_name)
  add_executable(${target_name} ${ARGN})
  set_target_properties(${target_name} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
endfunction()

add_subdirectory(chapter-1-introduction)
add_subdirectory(chapter-2-types-operators-expressions)
add_subdirectory(chapter-3-control-flow)
add_subdirectory(chapter-4-functions-and-program-structure)
add_subdirectory(chapter-5-pointers-and-arrays)
add_subdirectory(chapter-6-structures)
add_subdirectory(chapter-7-input-and-output)
add_subdirectory(chapter-8-the-unix-system-interface)
