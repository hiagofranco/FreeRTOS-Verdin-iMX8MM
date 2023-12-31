# CROSS COMPILER SETTING
SET(CMAKE_SYSTEM_NAME Generic)
CMAKE_MINIMUM_REQUIRED (VERSION 3.10.0)

# THE VERSION NUMBER
SET (Tutorial_VERSION_MAJOR 1)
SET (Tutorial_VERSION_MINOR 0)

# ENABLE ASM
ENABLE_LANGUAGE(ASM)

SET(CMAKE_STATIC_LIBRARY_PREFIX)
SET(CMAKE_STATIC_LIBRARY_SUFFIX)

SET(CMAKE_EXECUTABLE_LIBRARY_PREFIX)
SET(CMAKE_EXECUTABLE_LIBRARY_SUFFIX)

# CURRENT DIRECTORY
SET(ProjDirPath ${CMAKE_CURRENT_SOURCE_DIR})

SET(EXECUTABLE_OUTPUT_PATH ${ProjDirPath}/${CMAKE_BUILD_TYPE})
SET(LIBRARY_OUTPUT_PATH ${ProjDirPath}/${CMAKE_BUILD_TYPE})


project(low_power_wakeword)

set(MCUX_BUILD_TYPES release)

set(MCUX_SDK_PROJECT_NAME low_power_wakeword.elf)

if (NOT DEFINED SdkRootDirPath)
    SET(SdkRootDirPath ${ProjDirPath}/../../../../..)
endif()

include(${ProjDirPath}/flags.cmake)

include(${ProjDirPath}/config.cmake)

add_executable(${MCUX_SDK_PROJECT_NAME} 
"${ProjDirPath}/../low_power_voice_common.c"
"${ProjDirPath}/../low_power_voice_common.h"
"${ProjDirPath}/../voice_engine_common.c"
"${ProjDirPath}/../voice_engine_common.h"
"${ProjDirPath}/../voice_engine_voiceseeker_voicespot.c"
"${ProjDirPath}/../lpm.c"
"${ProjDirPath}/../lpm.h"
"${ProjDirPath}/../FreeRTOSConfig.h"
"${ProjDirPath}/../pin_mux.c"
"${ProjDirPath}/../pin_mux.h"
"${ProjDirPath}/../rpmsg_config.h"
"${ProjDirPath}/../rsc_table.c"
"${ProjDirPath}/../rsc_table.h"
"${ProjDirPath}/../remoteproc.h"
"${ProjDirPath}/../board.c"
"${ProjDirPath}/../board.h"
"${ProjDirPath}/../clock_config.c"
"${ProjDirPath}/../clock_config.h"
"${ProjDirPath}/../fsl_iomuxc.h"
"${ProjDirPath}/../empty_rsc_table.c"
"${ProjDirPath}/../srtm_config.h"
"${ProjDirPath}/../app_srtm.c"
"${ProjDirPath}/../app_srtm.h"
"${SdkRootDirPath}/components/srtm/channels/srtm_rpmsg_endpoint.h"
"${SdkRootDirPath}/components/srtm/channels/srtm_rpmsg_endpoint.c"
"${SdkRootDirPath}/components/srtm/services/srtm_audio_service.h"
"${SdkRootDirPath}/components/srtm/services/srtm_audio_service.c"
"${SdkRootDirPath}/components/srtm/services/srtm_sai_sdma_adapter.h"
"${SdkRootDirPath}/components/srtm/services/srtm_sai_sdma_adapter.c"
"${SdkRootDirPath}/components/srtm/services/srtm_pdm_sdma_adapter.h"
"${SdkRootDirPath}/components/srtm/services/srtm_pdm_sdma_adapter.c"
"${SdkRootDirPath}/components/srtm/services/srtm_i2c_codec_adapter.h"
"${SdkRootDirPath}/components/srtm/services/srtm_i2c_codec_adapter.c"
"${SdkRootDirPath}/components/srtm/services/srtm_wm8524_adapter.h"
"${SdkRootDirPath}/components/srtm/services/srtm_wm8524_adapter.c"
)

target_include_directories(${MCUX_SDK_PROJECT_NAME} PUBLIC
    ${ProjDirPath}/..
    ${SdkRootDirPath}/components/srtm/channels
    ${SdkRootDirPath}/components/srtm/services
)

set(CMAKE_MODULE_PATH
    ${SdkRootDirPath}/devices/MIMX8MM6/utilities
    ${SdkRootDirPath}/devices/MIMX8MM6/utilities/debug_console_lite
    ${SdkRootDirPath}/middleware/voice_spot
    ${SdkRootDirPath}/middleware/voice_seeker
    ${SdkRootDirPath}/CMSIS/DSP
    ${SdkRootDirPath}/devices/MIMX8MM6/drivers
    ${SdkRootDirPath}/components/codec
    ${SdkRootDirPath}/components/codec/
    ${SdkRootDirPath}/components/codec/i2c
    ${SdkRootDirPath}/components/i2c
    ${SdkRootDirPath}/middleware/multicore
    ${SdkRootDirPath}/rtos/freertos/freertos-kernel
    ${SdkRootDirPath}/devices/MIMX8MM6
    ${SdkRootDirPath}/components/uart
    ${SdkRootDirPath}/components/serial_manager
    ${SdkRootDirPath}/components/lists
    ${SdkRootDirPath}/CMSIS/Core/Include
    ${SdkRootDirPath}/middleware/voice_seeker/rdsp_utilities_public
    ${SdkRootDirPath}/components/codec/ak4497
    ${SdkRootDirPath}/components/srtm/port
    ${SdkRootDirPath}/components/srtm
    ${SdkRootDirPath}/components/codec/wm8524
)

# include modules
include(utility_debug_console_lite_MIMX8MM6)

include(utility_assert_lite_MIMX8MM6)

include(middleware_voice_spot_cm4_iMX8MM_MIMX8MM6)

include(middleware_voice_seeker_cm4_MIMX8MM6)

include(CMSIS_DSP_Source_MIMX8MM6)

include(driver_igpio_MIMX8MM6)

include(driver_iuart_MIMX8MM6)

include(driver_gpc_2_MIMX8MM6)

include(driver_gpt_MIMX8MM6)

include(driver_codec_MIMX8MM6)

include(driver_common_MIMX8MM6)

include(component_codec_adapters_MIMX8MM6)

include(driver_pdm_sdma_MIMX8MM6)

include(component_codec_i2c_MIMX8MM6)

include(component_ii2c_adapter_MIMX8MM6)

include(component_ak4497_adapter_MIMX8MM6)

include(component_wm8524_adapter_MIMX8MM6)

include(middleware_multicore_rpmsg_lite_imx8mm_m4_freertos_MIMX8MM6)

include(middleware_multicore_rpmsg_lite_MIMX8MM6)

include(middleware_multicore_rpmsg_lite_freertos_MIMX8MM6)

include(middleware_freertos-kernel_heap_4_MIMX8MM6)

include(driver_pdm_MIMX8MM6)

include(driver_clock_MIMX8MM6)

include(driver_rdc_MIMX8MM6)

include(device_MIMX8MM6_CMSIS_MIMX8MM6)

include(component_iuart_adapter_MIMX8MM6)

include(component_serial_manager_MIMX8MM6)

include(component_lists_MIMX8MM6)

include(component_serial_manager_uart_MIMX8MM6)

include(device_MIMX8MM6_startup_MIMX8MM6)

include(CMSIS_Include_core_cm_MIMX8MM6)

include(middleware_voice_spot_model_MIMX8MM6)

include(middleware_voice_seeker_rdsp_utilities_public_MIMX8MM6)

include(driver_sdma_MIMX8MM6)

include(driver_memory_MIMX8MM6)

include(driver_mu_MIMX8MM6)

include(driver_sai_MIMX8MM6)

include(driver_sai_sdma_MIMX8MM6)

include(driver_ak4497_MIMX8MM6)

include(driver_srtm_freertos_MIMX8MM6)

include(driver_srtm_MIMX8MM6)

include(driver_ii2c_freertos_MIMX8MM6)

include(driver_ii2c_MIMX8MM6)

include(middleware_freertos-kernel_MIMX8MM6)

include(middleware_freertos-kernel_extension_MIMX8MM6)

include(driver_wm8524_MIMX8MM6)

include(utilities_misc_utilities_MIMX8MM6)

include(device_MIMX8MM6_system_MIMX8MM6)


IF(NOT DEFINED TARGET_LINK_SYSTEM_LIBRARIES)  
    SET(TARGET_LINK_SYSTEM_LIBRARIES "-lm -lc -lgcc -lnosys")  
ENDIF()  

TARGET_LINK_LIBRARIES(${MCUX_SDK_PROJECT_NAME} PRIVATE -Wl,--start-group)

target_link_libraries(${MCUX_SDK_PROJECT_NAME} PRIVATE ${TARGET_LINK_SYSTEM_LIBRARIES})

if(CMAKE_BUILD_TYPE STREQUAL release)
    target_link_libraries(${MCUX_SDK_PROJECT_NAME} PRIVATE ${ProjDirPath}/../../../../../middleware/voice_spot/iMX8M_CortexM4/Lib/librdsp_libvoicespot.a)
endif(CMAKE_BUILD_TYPE STREQUAL release)

if(CMAKE_BUILD_TYPE STREQUAL release)
    target_link_libraries(${MCUX_SDK_PROJECT_NAME} PRIVATE ${ProjDirPath}/../../../../../middleware/voice_seeker/ARM_CortexM4/Lib/libvoiceseeker_no_aec.a)
endif(CMAKE_BUILD_TYPE STREQUAL release)

TARGET_LINK_LIBRARIES(${MCUX_SDK_PROJECT_NAME} PRIVATE -Wl,--end-group)

ADD_CUSTOM_COMMAND(TARGET ${MCUX_SDK_PROJECT_NAME} POST_BUILD COMMAND ${CMAKE_OBJCOPY}
-Obinary ${EXECUTABLE_OUTPUT_PATH}/${MCUX_SDK_PROJECT_NAME} ${EXECUTABLE_OUTPUT_PATH}/low_power_wakeword.bin)

