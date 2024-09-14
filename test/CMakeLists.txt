add_executable(unit-tests)

target_link_libraries(
    unit-tests
    PRIVATE
    netpbmEditorlib
        Catch2::Catch2WithMain
)

target_sources(
    unit-tests
    PRIVATE
        "test-BoolVector.cpp"
)

catch_discover_tests(unit-tests)