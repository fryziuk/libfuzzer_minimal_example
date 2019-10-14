cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
project(libfuzzer_minimal_example VERSION 0.0.1 LANGUAGES C)

macro(_add_test test)
    add_executable(${test} src/${test}.c)
    set_target_properties(${test} PROPERTIES C_STANDARD "99")
    set_target_properties(${test} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${test})
    add_test (NAME ${test} COMMAND ${test})

    target_compile_options(${test}
            PRIVATE
            $<$<C_COMPILER_ID:Clang>: -Wall -fsanitize=address -fsanitize=fuzzer>
            )

    target_link_libraries(${test}
            PRIVATE
            $<$<C_COMPILER_ID:Clang>:-fsanitize=address,fuzzer>
            )
endmacro()
_add_test(main)