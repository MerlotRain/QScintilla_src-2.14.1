cmake_minimum_required(VERSION 3.12.0)
set(CMAKE_COLOR_MAKEFILE ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)

if(APPLE)
    set(CMAKE_PREFIX_PATH "/opt/homebrew/Cellar/qt@5/5.15.10_1/lib/cmake")
endif(APPLE)


# POLICIES
cmake_policy(SET CMP0048 NEW)
cmake_policy(SET CMP0053 NEW)
cmake_policy(SET CMP0071 NEW)
cmake_policy(SET CMP0094 NEW)
if(NOT "${CMAKE_VERSION}" VERSION_LESS "3.27")
  cmake_policy(SET CMP0144 NEW)
  # include(Dart) still used, as is the "Experimental" target
  cmake_policy(SET CMP0145 OLD)
endif()

# don't relink it only the shared object changes
set(CMAKE_LINK_DEPENDS_NO_SHARED ON)


set(CMAKE_DEBUG_POSTFIX "d" CACHE STRING "add a postfix, usually d on windows")
set(CMAKE_RELEASE_POSTFIX "" CACHE STRING "add a postfix, usually empty on windows")
set(CMAKE_RELWITHDEBINFO_POSTFIX "rd" CACHE STRING "add a postfix, usually empty on windows")
set(CMAKE_MINSIZEREL_POSTFIX "s" CACHE STRING "add a postfix, usually empty on windows")
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib)

project(QSci)

add_subdirectory(src)