find_package(mimalloc 2.2 CONFIG REQUIRED)
message(STATUS "Found mimalloc installed at: ${MIMALLOC_LIBRARY_DIR} (${MIMALLOC_INCLUDE_DIR})")

file(GLOB_RECURSE COLLECTIONS_SRC CONFIGURE_DEPENDS "src/*.cpp")

add_library(collections ${COLLECTIONS_SRC})
target_include_directories(collections
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
        ${MIMALLOC_INCLUDE_DIR}
)
target_link_libraries(collections PUBLIC mimalloc)
