# @ohos.application.appManager(appManager)

The appManager module provides APIs for application management. For example, you can query whether the system is undergoing a stability test, determine whether the device is RAM-constrained, obtain the maximum memory available to the current application, and retrieve information about running processes.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [appManager/appManager](arkts-ability-app-ability-appmanager.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-depr-f.md#getappmemorysize) | Obtains the maximum memory (RAM allocation) available to the current application. This API uses a promise to return the result. |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-depr-f.md#getappmemorysize) | Obtains the maximum memory (RAM allocation) available to the current application. This API uses an asynchronous callback to return the result. |
| [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-depr-f.md#getprocessrunninginfos) | Obtains information about the running processes. This API uses a promise to return the result. |
| [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-depr-f.md#getprocessrunninginfos) | Obtains information about the running processes. This API uses an asynchronous callback to return the result. |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-depr-f.md#isramconstraineddevice) | Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses a promise to return the result. |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-depr-f.md#isramconstraineddevice) | Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses an asynchronous callback to return the result. |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-depr-f.md#isrunninginstabilitytest) | Checks whether the system is undergoing a stability test. This API uses an asynchronous callback to return the result. |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-depr-f.md#isrunninginstabilitytest) | Checks whether the system is undergoing a stability test. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-depr-f-sys.md#clearupapplicationdata) | Clear up application data by bundle name |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-depr-f-sys.md#clearupapplicationdata) | Clear up application data by bundle name |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-depr-f-sys.md#getforegroundapplications) | getForegroundApplications. |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-depr-f-sys.md#getforegroundapplications) | getForegroundApplications. |
| [getProcessRunningInformation](arkts-ability-appmanager-getprocessrunninginformation-depr-f-sys.md#getprocessrunninginformation) | Obtains information about the running processes. This API uses a promise to return the result. |
| [getProcessRunningInformation](arkts-ability-appmanager-getprocessrunninginformation-depr-f-sys.md#getprocessrunninginformation) | Obtains information about the running processes. This API uses an asynchronous callback to return the result. |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-depr-f-sys.md#killprocessesbybundlename) | Kill processes by bundle name |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-depr-f-sys.md#killprocessesbybundlename) | Kill processes by bundle name |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-depr-f-sys.md#killprocesswithaccount) | Kill process with account. |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-depr-f-sys.md#killprocesswithaccount) | Kill process with account. |
| [registerApplicationStateObserver](arkts-ability-appmanager-registerapplicationstateobserver-depr-f-sys.md#registerapplicationstateobserver) | Register application state observer. |
| [unregisterApplicationStateObserver](arkts-ability-appmanager-unregisterapplicationstateobserver-depr-f-sys.md#unregisterapplicationstateobserver) | Unregister application state observer. |
| [unregisterApplicationStateObserver](arkts-ability-appmanager-unregisterapplicationstateobserver-depr-f-sys.md#unregisterapplicationstateobserver) | Unregister application state observer. |
<!--DelEnd-->
