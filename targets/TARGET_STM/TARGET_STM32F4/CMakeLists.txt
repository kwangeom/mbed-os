# Copyright (c) 2020 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

if("STM32F401xE" IN_LIST MBED_TARGET_LABELS)
    add_subdirectory(TARGET_STM32F401xE)
elseif("STM32F439xI" IN_LIST MBED_TARGET_LABELS)
    add_subdirectory(TARGET_STM32F439xI)    
endif()

target_sources(mbed-core
    INTERFACE
        analogin_device.c
        analogout_device.c
        flash_api.c
        gpio_irq_device.c
        pwmout_device.c
        serial_device.c
        spi_api.c
)

add_subdirectory(STM32Cube_FW)

target_include_directories(mbed-core
    INTERFACE
        ${CMAKE_CURRENT_SOURCE_DIR}
        ${CMAKE_CURRENT_SOURCE_DIR}/STM32Cube_FW
        ${CMAKE_CURRENT_SOURCE_DIR}/STM32Cube_FW/CMSIS
        ${CMAKE_CURRENT_SOURCE_DIR}/STM32Cube_FW/STM32F4xx_HAL_Driver
        ${CMAKE_CURRENT_SOURCE_DIR}/STM32Cube_FW/STM32F4xx_HAL_Driver/Legacy
)
