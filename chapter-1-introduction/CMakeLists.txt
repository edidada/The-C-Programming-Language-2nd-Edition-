# Chapter 1: Introduction to C
# Sources that are not built as standalone executables:
#   t.c                         scratch file
#  28.print-input-line-and-text.c      broken: stray "char" line before main()
#  29.print-length-80-line.c           broken: incomplete line before main()
#  30.remove-line-end-space-and-tab.c  broken: incomplete line before main()
#  34.entab.c                          broken: "spaceCount" undeclared
set(NOT_STANDALONE
  t.c
  28.print-input-line-and-text.c
  29.print-length-80-line.c
  30.remove-line-end-space-and-tab.c
  34.entab.c
)

file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  if(NOT _src IN_LIST NOT_STANDALONE)
    string(REGEX REPLACE "\\.c$" "" _name "${_src}")
    add_exercise("ch1_${_name}" "${_src}")
  endif()
endforeach()
