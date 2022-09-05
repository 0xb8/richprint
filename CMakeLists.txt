cmake_minimum_required( VERSION 2.8 )
project( RichPrint )
set( CMAKE_BUILD_TYPE Release )
include(third_party/cmrc/CMakeRC.cmake)

string(REPLACE "/MD" "/MT" CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE}"  )
message(STATUS "${CMAKE_CXX_FLAGS_RELEASE} " CMAKE_CXX_FLAGS_RELEASE)
add_executable( richprint richprint.cpp )

cmrc_add_resource_library( richprint_rc ALIAS richprint::rc "comp_id.txt")
target_link_libraries(richprint PRIVATE richprint::rc)

install(TARGETS richprint DESTINATION bin)

INCLUDE(CPack)
