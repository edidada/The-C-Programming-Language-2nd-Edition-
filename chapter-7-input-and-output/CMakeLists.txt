# Chapter 7: Input and output
# Every *.c file in this chapter is a self-contained program.
file(GLOB _all RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.c")

foreach(_src IN LISTS _all)
  string(REGEX REPLACE "\\.c$" "" _name "${_src}")
  add_exercise("ch7_${_name}" "${_src}")
endforeach()
