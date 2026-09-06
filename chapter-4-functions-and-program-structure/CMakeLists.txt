# Chapter 4: Functions and program structure
# Sources that are not built as standalone executables:
#   t.c                                     scratch file
#   atof.c getch.c getop.c mygetline.c stack.c   helper files (no main())
#   4.reverse-polish-calculator.c           multi-file program, built below
#   5.getop-with-static.c                   broken: "int void main()"
#   6.register-variable.c                   broken: "int void main()"
#   10.reverse.recursive.c                  broken: "int void main()"
#   11.swap-macro.c                         broken: "int void main()"
#   12.conditional-inclusion.c              broken: "int void main()"
set(NOT_STANDALONE
  t.c
  atof.c
  getch.c
  getop.c
  mygetline.c
  stack.c
  4.reverse-polish-calculator.c
  5.getop-with-static.c
  6.register-variable.c
  10.reverse.recursive.c
  11.swap-macro.c
  12.conditional-inclusion.c
)

file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  if(NOT _src IN_LIST NOT_STANDALONE)
    string(REGEX REPLACE "\\.c$" "" _name "${_src}")
    add_exercise("ch4_${_name}" "${_src}")
  endif()
endforeach()

# Reverse polish calculator (exercises 4-3 ~ 4-6):
# compile together with stack.c, getop.c and getch.c, needs libm.
add_exercise(ch4_calc
  4.reverse-polish-calculator.c stack.c getop.c getch.c)
if(UNIX)
  target_link_libraries(ch4_calc m)
endif()
