
add_executable(check_gbe check_gbe.c)

target_link_libraries(check_gbe PRIVATE emu $<IF:$<TARGET_EXISTS:Check::check>,Check::check,Check::checkShared>)

target_include_directories(check_gbe 
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
        ${CHECK_INCLUDE_DIRS}
)