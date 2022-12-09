#
# COPYRIGHT 2022 CONNECTED DEVELOPMENT, A DIVISION OF
# EXPONENTIAL TECHNOLOGY GROUP.
#
# SPDX-License-Identifier: Apache-2.0

# Set the source files for this directory.
set(FILES
   device_management/dm_downlink.c
   device_management/modem_context.c
   lorawan_api/lorawan_api.c
   lr1mac/src/lr1_stack_mac_layer.c
   lr1mac/src/lr1mac_class_b/smtc_beacon_sniff.c
   lr1mac/src/lr1mac_class_b/smtc_d2d.c
   lr1mac/src/lr1mac_class_b/smtc_ping_slot.c
   lr1mac/src/lr1mac_class_c/lr1mac_class_c.c
   lr1mac/src/lr1mac_core.c
   lr1mac/src/lr1mac_utilities.c
   lr1mac/src/services/smtc_duty_cycle.c
   lr1mac/src/services/smtc_lbt.c
   lr1mac/src/services/smtc_multicast.c
   lr1mac/src/smtc_real/src/smtc_real.c
   modem_core/smtc_modem.c
   modem_core/smtc_modem_test.c
   modem_services/fifo_ctrl.c
   modem_services/lorawan_certification.c
   modem_services/modem_utilities.c
   modem_services/smtc_clock_sync.c
   modem_services/smtc_modem_services_hal.c
   modem_supervisor/modem_supervisor.c
   radio_drivers/sx126x_driver/src/lr_fhss_mac.c
   radio_drivers/sx126x_driver/src/sx126x.c
   radio_drivers/sx126x_driver/src/sx126x_lr_fhss.c
   radio_planner/src/radio_planner.c
   radio_planner/src/radio_planner_hal.c
   smtc_modem_crypto/smtc_modem_crypto.c
   smtc_modem_crypto/soft_secure_element/aes.c
   smtc_modem_crypto/soft_secure_element/cmac.c
   smtc_modem_crypto/soft_secure_element/soft_se.c
   smtc_modem_services/src/alc_sync/alc_sync.c
   smtc_modem_services/src/file_upload/file_upload.c
   smtc_modem_services/src/stream/rose.c
   smtc_modem_services/src/stream/stream.c
   smtc_ral/src/ral_sx126x.c
   smtc_ralf/src/ralf_sx126x.c
   )

# Append the configured region source files.
if (CONFIG_REGION_US_915)
    set(FILES ${FILES} lr1mac/src/smtc_real/src/region_us_915.c)
    target_compile_definitions(app PRIVATE REGION_US_915)
endif()
