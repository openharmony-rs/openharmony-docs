# general

Provides methods for setting general information about devices, including the device name, startup wizard, airplane mode, debugging information, accessibility feature switch, and touch exploration status.

@namespace general

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## Summary

### Constants

| Name | Description |
| --- | --- |
| [SETUP_WIZARD_FINISHED](arkts-basicservices-general-con.md#setup_wizard_finished) | Specifies whether the startup wizard has been run. |
| [END_BUTTON_ACTION](arkts-basicservices-general-con.md#end_button_action) | Specifies what happens after the user presses the call end button if the user is not in a call. |
| [ACCELEROMETER_ROTATION_STATUS](arkts-basicservices-general-con.md#accelerometer_rotation_status) | Specifies whether the accelerometer is used to change screen orientation, that is, whether auto-rotation is enabled. |
| [AIRPLANE_MODE_STATUS](arkts-basicservices-general-con.md#airplane_mode_status) | Specifies whether airplane mode is enabled. |
| [DEVICE_PROVISION_STATUS](arkts-basicservices-general-con.md#device_provision_status) | Specifies whether the device is provisioned. |
| [HDC_STATUS](arkts-basicservices-general-con.md#hdc_status) | Specifies whether the hard disk controller (HDC) on USB devices is enabled. |
| [BOOT_COUNTING](arkts-basicservices-general-con.md#boot_counting) | Indicates the number of boot operations after the device is powered on. |
| [CONTACT_METADATA_SYNC_STATUS](arkts-basicservices-general-con.md#contact_metadata_sync_status) | Specifies whether contact metadata synchronization is enabled. |
| [DEVELOPMENT_SETTINGS_STATUS](arkts-basicservices-general-con.md#development_settings_status) | Specifies whether developer options are enabled. |
| [DEVICE_NAME](arkts-basicservices-general-con.md#device_name) | Indicates the device name. |
| [USB_STORAGE_STATUS](arkts-basicservices-general-con.md#usb_storage_status) | Specifies whether USB mass storage is enabled. |
| [DEBUGGER_WAITING](arkts-basicservices-general-con.md#debugger_waiting) | Specifies whether the device waits for the debugger when starting an application to debug. |
| [DEBUG_APP_PACKAGE](arkts-basicservices-general-con.md#debug_app_package) | Indicates the bundle name of the application to debug. |
| [ACCESSIBILITY_STATUS](arkts-basicservices-general-con.md#accessibility_status) | Specifies whether any accessibility feature is enabled. |
| [ACTIVATED_ACCESSIBILITY_SERVICES](arkts-basicservices-general-con.md#activated_accessibility_services) | Indicates the list of accessibility features that have been activated. |
| [GEOLOCATION_ORIGINS_ALLOWED](arkts-basicservices-general-con.md#geolocation_origins_allowed) | Indicates the default geographical location that can be used by the browser. Multiple geographical locations are separated by spaces. |
| [SKIP_USE_HINTS](arkts-basicservices-general-con.md#skip_use_hints) | Specifies whether an application should attempt to skip all introductory hints at the first startup. This is intended for temporary users or users who are familiar with the environment. |
| [TOUCH_EXPLORATION_STATUS](arkts-basicservices-general-con.md#touch_exploration_status) | Indicates whether touch exploration is enabled. |
