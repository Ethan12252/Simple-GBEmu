add_executable(gbemu main.c)

target_link_libraries(gbemu 
  PRIVATE 
    emu
    $<TARGET_NAME_IF_EXISTS:SDL2::SDL2main>
    $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static>
    $<IF:$<TARGET_EXISTS:SDL2_ttf::SDL2_ttf>,SDL2_ttf::SDL2_ttf,SDL2_ttf::SDL2_ttf-static>
)

target_include_directories(gbemu PRIVATE ${PROJECT_SOURCE_DIR}/include)

# Copy font file
add_custom_command(TARGET gbemu POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${PROJECT_SOURCE_DIR}/NotoSansMono-Medium.ttf
    $<TARGET_FILE_DIR:gbemu>
)