# @ohos.app.ability.autoStartupManager(Auto-Startup Management)

The autoStartupManager module provides APIs for an application to query whether it is configured to start automatically at boot time.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAutoStartupStatusForSelf](arkts-ability-autostartupmanager-getautostartupstatusforself-f.md) | Checks whether the current application is enabled for automatic startup at boot time. This API uses a promise to return the result. This API can be properly called only on phones, PC/2-in-1 devices, tablets, and wearables. On other devices, it returns the error code 801. |
| [isAutoStartupSupported](arkts-ability-autostartupmanager-isautostartupsupported-f.md) | Check whether the current device supports auto startup on this device. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [cancelApplicationAutoStartup](arkts-ability-autostartupmanager-cancelapplicationautostartup-f-sys.md#cancelapplicationautostartup) | Cancels the auto-startup setting for an application component. This API uses an asynchronous callback to return the result. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
| [cancelApplicationAutoStartup](arkts-ability-autostartupmanager-cancelapplicationautostartup-f-sys.md#cancelapplicationautostartup-1) | Cancels the auto-startup setting for an application component. This API uses a promise to return the result. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
| [off](arkts-ability-autostartupmanager-off-f-sys.md#offsystemautostartup) | Unregisters the callback used to listen for auto-startup status changes of an application component. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
| [on](arkts-ability-autostartupmanager-on-f-sys.md#onsystemautostartup) | Registers a callback to listen for auto-startup status changes of an application component. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
| [queryAllAutoStartupApplications](arkts-ability-autostartupmanager-queryallautostartupapplications-f-sys.md#queryallautostartupapplications) | Obtains information about all auto-startup application components. This API uses an asynchronous callback to return the result. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
| [queryAllAutoStartupApplications](arkts-ability-autostartupmanager-queryallautostartupapplications-f-sys.md#queryallautostartupapplications-1) | Obtains information about all auto-startup application components. This API uses a promise to return the result. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
| [setApplicationAutoStartup](arkts-ability-autostartupmanager-setapplicationautostartup-f-sys.md#setapplicationautostartup) | Sets an application component to automatically start upon system boot. This API uses an asynchronous callback to return the result. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
| [setApplicationAutoStartup](arkts-ability-autostartupmanager-setapplicationautostartup-f-sys.md#setapplicationautostartup-1) | Sets an application component to automatically start upon system boot. This API uses a promise to return the result. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned. |
<!--DelEnd-->
