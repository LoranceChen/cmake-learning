cmake_minimum_required(VERSION 3.10)
project(cmake_learning)
set(CMAKE_CXX_STANDARD 11)

set(Tutorial_VERSION_MAJOR 1)
set(Tutorial_VERSION_MINOR 0)

configure_file(
        "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
        "${PROJECT_BINARY_DIR}/TutorialConfig.h"
)

include_directories("${PROJECT_BINARY_DIR}")


# sub library
#include_directories("${PROJECT_SOURCE_DIR}/MathFunctions")
#add_subdirectory(MathFunctions)
#target_link_libraries(cmake_learning MathFunctions)

# should we use our own math functions?
option (USE_MYMATH
        "Use tutorial provided math implementation" ON)

# 添加 MathFunctions 库吗？
#
if (USE_MYMATH)
    include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
    add_subdirectory (MathFunctions)
    set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)

# 添加可执行文件
add_executable (cmake_learning main.cpp)
target_link_libraries (cmake_learning  ${EXTRA_LIBS})

# 添加安装目标
install (TARGETS cmake_learning DESTINATION bin)
install (FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"
        DESTINATION include)


include (InstallRequiredSystemLibraries)
set (CPACK_RESOURCE_FILE_LICENSE
        "${CMAKE_CURRENT_SOURCE_DIR}/License.txt")
set (CPACK_PACKAGE_VERSION_MAJOR "${Tutorial_VERSION_MAJOR}")
set (CPACK_PACKAGE_VERSION_MINOR "${Tutorial_VERSION_MINOR}")
include (CPack)