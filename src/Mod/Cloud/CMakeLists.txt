
add_subdirectory(App)
if(BUILD_GUI)
    add_subdirectory(Gui)
endif(BUILD_GUI)

set(Cloud_Scripts
    Init.py
)

if(BUILD_GUI)
    list (APPEND Cloud_Scripts InitGui.py)
endif(BUILD_GUI)

add_custom_target(CloudScripts ALL
    SOURCES ${Cloud_Scripts}
)

fc_target_copy_resource_flat(CloudScripts
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_BINARY_DIR}/Mod/Cloud
    ${Cloud_Scripts}
)

install(
    FILES
        ${Cloud_Scripts}
    DESTINATION
        Mod/Cloud
)
