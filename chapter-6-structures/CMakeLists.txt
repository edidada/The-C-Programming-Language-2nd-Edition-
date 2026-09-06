# Chapter 6: Structures
# Sources that are not built as standalone executables:
#   getch.c    helper file (no main())
#   2 ~ 7      multi-file programs (they call getch()/ungetch()), built below
set(NOT_STANDALONE
  getch.c
  2.keywords-count.c
  3.getword.c
  4.keywords-count-pointer.c
  5.words-count-binary-tree.c
  6.variables-group.c
  7.words-appear-lines.c
)

file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  if(NOT _src IN_LIST NOT_STANDALONE)
    string(REGEX REPLACE "\\.c$" "" _name "${_src}")
    add_exercise("ch6_${_name}" "${_src}")
  endif()
endforeach()

# Exercises 6-1 ~ 6-3 all rely on getch()/ungetch() from getch.c.
add_exercise(ch6_2.keywords-count 2.keywords-count.c getch.c)
add_exercise(ch6_3.getword 3.getword.c getch.c)
add_exercise(ch6_4.keywords-count-pointer 4.keywords-count-pointer.c getch.c)
add_exercise(ch6_5.words-count-binary-tree 5.words-count-binary-tree.c getch.c)
add_exercise(ch6_6.variables-group 6.variables-group.c getch.c)
add_exercise(ch6_7.words-appear-lines 7.words-appear-lines.c getch.c)
