file(GLOB srcs ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
include_directories(../..)
# Build each source file independently
foreach(source ${srcs})
    get_filename_component(name ${source} NAME_WE)

    # target
    add_executable(${name} ${source})
    target_link_libraries(${name} ${faiss_lib})

    # Install
    install(TARGETS ${name} DESTINATION bin)
endforeach(source)
