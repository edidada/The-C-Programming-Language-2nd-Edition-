# Chapter 5: Pointers and arrays
# Sources that are not built as standalone executables:
#   t.c t1.c t2.c t3.c t4.c t5.c    scratch files
#   7.alloc.test.c                  scratch test
#   helper files (no main()):
#     6.alloc.c case-convert.c getch.c mygetline.c numcmp.c readlines-writelines.c
#   multi-file programs, declared below:
#     4.getfloat.c 30.find.c 31.find.c 37.tail.c
#     38.pointers-to-functions.c 39.sort-with-r.c 40.sort-with-f.c
#     41.sort-with-d.c 42.dcl.c 43.dcl-error-handle.c 44.undcl.c
set(NOT_STANDALONE
  t.c
  t1.c
  t2.c
  t3.c
  t4.c
  t5.c
  7.alloc.test.c
  6.alloc.c
  case-convert.c
  getch.c
  mygetline.c
  numcmp.c
  readlines-writelines.c
  4.getfloat.c
  30.find.c
  31.find.c
  37.tail.c
  38.pointers-to-functions.c
  39.sort-with-r.c
  40.sort-with-f.c
  41.sort-with-d.c
  42.dcl.c
  43.dcl-error-handle.c
  44.undcl.c
)

file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  if(NOT _src IN_LIST NOT_STANDALONE)
    string(REGEX REPLACE "\\.c$" "" _name "${_src}")
    add_exercise("ch5_${_name}" "${_src}")
  endif()
endforeach()

# Exercise 5-2: getfloat needs getch()/ungetch() from getch.c.
add_exercise(ch5_4.getfloat 4.getfloat.c getch.c)

# Exercises 5-1/5-11/5-12 (find, detab, entab variants): mygetline().
add_exercise(ch5_30.find 30.find.c mygetline.c)
add_exercise(ch5_31.find 31.find.c mygetline.c)

# Exercise 5-13: tail needs alloc() and mygetline().
add_exercise(ch5_37.tail 37.tail.c mygetline.c 6.alloc.c)

# Sorting examples (5-14 ~ 5-16): numcmp(), readlines()/writelines(),
# readlines() itself uses alloc(), case-convert.c adds strtolower().
add_exercise(ch5_38.pointers-to-functions
  38.pointers-to-functions.c numcmp.c readlines-writelines.c 6.alloc.c)
add_exercise(ch5_39.sort-with-r
  39.sort-with-r.c numcmp.c readlines-writelines.c 6.alloc.c)
add_exercise(ch5_40.sort-with-f
  40.sort-with-f.c numcmp.c readlines-writelines.c 6.alloc.c case-convert.c)
add_exercise(ch5_41.sort-with-d
  41.sort-with-d.c numcmp.c readlines-writelines.c 6.alloc.c case-convert.c)

# Declaration parsing (5-18 ~ 5-19): need getch()/ungetch().
add_exercise(ch5_42.dcl 42.dcl.c getch.c)
add_exercise(ch5_43.dcl-error-handle 43.dcl-error-handle.c getch.c)
add_exercise(ch5_44.undcl 44.undcl.c getch.c)
