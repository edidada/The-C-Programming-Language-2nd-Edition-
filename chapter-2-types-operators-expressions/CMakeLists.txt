# Chapter 2: Types, operators and expressions
# Sources that are not built as standalone executables:
#   7.strcat.c    broken: typo "cahr" in the parameter declaration
set(NOT_STANDALONE
  7.strcat.c
)

file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  if(NOT _src IN_LIST NOT_STANDALONE)
    string(REGEX REPLACE "\\.c$" "" _name "${_src}")
    add_exercise("ch2_${_name}" "${_src}")
  endif()
endforeach()
