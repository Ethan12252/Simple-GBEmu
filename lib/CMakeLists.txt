# Collect source files
file(GLOB sources CONFIGURE_DEPENDS "${PROJECT_SOURCE_DIR}/lib/*.c")
file(GLOB headers CONFIGURE_DEPENDS "${PROJECT_SOURCE_DIR}/include/*.h")

# Create library
add_library(emu STATIC ${sources} ${headers})

# Set include directories
target_include_directories(emu 
    PUBLIC ${PROJECT_SOURCE_DIR}/include
)

# Link dependencies with correct target names from vcpkg output
target_link_libraries(emu 
    PUBLIC
        $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static>
        $<IF:$<TARGET_EXISTS:SDL2_ttf::SDL2_ttf>,SDL2_ttf::SDL2_ttf,SDL2_ttf::SDL2_ttf-static>
)