add_executable(demo main.cpp)
target_link_libraries(demo PRIVATE collections)
target_include_directories(demo PUBLIC ../collections/include)
