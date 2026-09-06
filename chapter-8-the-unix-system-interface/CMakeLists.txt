# Chapter 8: The UNIX system interface
# Sources that are not built:
#   malloc.c    storage allocator, no main() and needs NULL/standard headers
#   fsize.c     depends on the book's own dirent.h which requires NAME_MAX
#               (kept for reference; not compilable out of the box)
set(NOT_STANDALONE
  malloc.c
  fsize.c
)

file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  if(NOT _src IN_LIST NOT_STANDALONE)
    string(REGEX REPLACE "\\.c$" "" _name "${_src}")
    add_exercise("ch8_${_name}" "${_src}")
  endif()
endforeach()
