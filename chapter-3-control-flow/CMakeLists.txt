# Chapter 3: Control flow
# Sources that are not built as standalone executables:
#   t.c    scratch file
set(NOT_STANDALONE
  t.c
)

file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  if(NOT _src IN_LIST NOT_STANDALONE)
    string(REGEX REPLACE "\\.c$" "" _name "${_src}")
    add_exercise("ch3_${_name}" "${_src}")
  endif()
endforeach()
