add_library(MathFunctions mysqrt.cpp MathFunctions.h)

install (TARGETS MathFunctions DESTINATION bin)
install (FILES MathFunctions.h DESTINATION include)