#
# COPYRIGHT 2023 CONNECTED DEVELOPMENT, A DIVISION OF
# EXPONENTIAL TECHNOLOGY GROUP.
#
# SPDX-License-Identifier: Apache-2.0

message(INFO ": LoRaBasicsModem_SWL2001 Dir: ${CMAKE_CURRENT_LIST_DIR}")

# Macro to create the source FILES list in a subdir.
macro(CollectSubdirFiles subdir varname)
   include(${subdir}/CMakeLists.txt)
   foreach(FILE ${FILES})
     set(${varname} ${${varname}} ${subdir}/${FILE})
   endforeach()
   message(VERBOSE ": ${varname}: ${${varname}}")
endmacro()

# Collect the source files in each subdir.
CollectSubdirFiles(${CMAKE_CURRENT_LIST_DIR}/../RadioDriverHAL  RadioDriverHALFiles)
CollectSubdirFiles(${CMAKE_CURRENT_LIST_DIR}/../RALBSP          RALBSPFiles)
CollectSubdirFiles(${CMAKE_CURRENT_LIST_DIR}/../ModemHAL        ModemHALFiles)

# Collect the source files in the LoRa Basics Modem core folder.
CollectSubdirFiles(${CMAKE_CURRENT_LIST_DIR}/../LoRaBasicsModem_SWL2001/smtc_modem_core  LBMFiles)

# Add all subdir source files to the target.
target_sources(app PRIVATE
   ${RadioDriverHALFiles}
   ${RALBSPFiles}
   ${ModemHALFiles}
   ${LBMFiles}
)

if (CONFIG_LBM_HAL_DBG)
   target_compile_definitions(app PRIVATE MODEM_HAL_DBG_TRACE=1)
else()
   target_compile_definitions(app PRIVATE MODEM_HAL_DBG_TRACE=0)
endif()

if (CONFIG_LBM_HAL_DBG_DEEP)
   target_compile_definitions(app PRIVATE MODEM_HAL_DEEP_DBG_TRACE=1)
else()
   target_compile_definitions(app PRIVATE MODEM_HAL_DEEP_DBG_TRACE=0)
endif()

