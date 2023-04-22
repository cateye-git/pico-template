cmake_minimum_required(VERSION 3.13)

    # initialize the SDK based on PICO_SDK_PATH
    # note: this must happen before project()
    include(pico_sdk_import.cmake)

    project(my_project)

    # initialize the Raspberry Pi Pico SDK
    pico_sdk_init()

    add_compile_options(
	-Wall
	-Wno-format
	-Wno-unused-function
	-Wno-maybe-uninitialized
	-Wextra    			# optional
)

add_executable(my_project    
    main.c
)

# pico_enable_stdio_usb(my_project 1)
pico_enable_stdio_uart(my_project 1)

pico_add_extra_outputs(my_project)

target_link_libraries(my_project pico_stdlib)
