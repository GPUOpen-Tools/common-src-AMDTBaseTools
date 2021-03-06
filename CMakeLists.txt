cmake_minimum_required (VERSION 2.6)
project (AMDTBaseTools)

# The version number
set (AMDTBASETOOLS_VERSION_MAJOR 1)
set (AMDTBASETOOLS_VERSION_MINOR 0)

# Project-specific preprocessor directives
add_definitions(-DAMDTBASETOOLS_EXPORTS)

# Configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/AMDTBaseToolsConfig.h.in"
  "${PROJECT_BINARY_DIR}/AMDTBaseToolsConfig.h"
  ) 

# Include directories
include_directories("${PROJECT_SOURCE_DIR}/Include")
include_directories("${PROJECT_SOURCE_DIR}/src")
include_directories("${PROJECT_SOURCE_DIR}/../")
include_directories("${PROJECT_SOURCE_DIR}/../../")

# Add the library (change STATIC to SHARED for dynamic library build)
add_library(AMDTBaseTools STATIC src/gtASCIIString.cpp src/gtASCIIStringTokenizer.cpp src/gtAssert.cpp src/gtErrorString.cpp src/gtIAllocationFailureObserver.cpp src/gtIAssertionFailureHandler.cpp src/gtList.cpp src/gtRedBlackTree.cpp src/gtSingeltonsDelete.cpp src/gtString.cpp src/gtStringTokenizer.cpp src/gtVector.cpp)

# Set binary suffix
set_target_properties(AMDTBaseTools PROPERTIES DEBUG_POSTFIX -d CXX_STANDARD 11)
