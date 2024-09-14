add_library(netpbmEditorlib STATIC)

target_sources(
    netpbmEditorlib
    PRIVATE
    "BoolVector.hpp"
    "BoolVector.cpp"
)

add_executable(NetpbmEditor)

target_sources(
    NetpbmEditor
    PRIVATE
        "NetpbmEditor.cpp"
)

target_link_libraries(
    NetpbmEditor
    PRIVATE
        netpbmEditorlib
)