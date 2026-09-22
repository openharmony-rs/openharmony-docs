# @ohos.app.ability.appManager(Application Management)

The appManager module implements application management. You can use the APIs of this module to query whether the application is undergoing a stability test, whether the application is running on a RAM constrained device, the memory size of the application, and information about the running process.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-f.md#getappmemorysize) | Obtains the maximum memory (RAM allocation) available to the current application. This API uses a promise to return the result. |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-f.md#getappmemorysize-1) | Obtains the maximum memory (RAM allocation) available to the current application. This API uses an asynchronous callback to return the result. |
| [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md#getrunningprocessinformation) | Obtains information about the running processes of the current application. This API uses a promise to return the result. |
| [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md#getrunningprocessinformation-1) | Obtains information about the running processes of the current application. This API uses an asynchronous callback to return the result. |
| [isAppRunning](arkts-ability-appmanager-isapprunning-f.md) | Checks whether the application with the specified bundle name and application clone index is running across all users. This API uses a promise to return the result. |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-f.md#isramconstraineddevice) | Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses a promise to return the result. |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-f.md#isramconstraineddevice-1) | Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses an asynchronous callback to return the result. |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-f.md#isrunninginstabilitytest) | Checks whether the system is undergoing a stability test. This API uses an asynchronous callback to return the result. |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-f.md#isrunninginstabilitytest-1) | Checks whether the system is undergoing a stability test. This API uses a promise to return the result. |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f.md#killprocessesbybundlename-1) | Kills a process by bundle name. This API uses a promise to return the result. |
| [off](arkts-ability-appmanager-off-f.md#offapplicationstate) | Unregisters the observer used to listen for application state changes. This API uses an asynchronous callback to return the result. |
| [off](arkts-ability-appmanager-off-f.md#offapplicationstate) | Unregisters the observer used to listen for application state changes. This API uses a promise to return the result. |
| [on](arkts-ability-appmanager-on-f.md#onapplicationstate) | Registers an observer to listen for lifecycle changes of all applications. |
| [on](arkts-ability-appmanager-on-f.md#onapplicationstate) | Registers an observer to listen for lifecycle changes of the specified application. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [clearUpAppData](arkts-ability-appmanager-clearupappdata-f-sys.md) | Clears data of a specified application based on the bundle name and application clone index. This API uses a promise to return the result. |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-f-sys.md#clearupapplicationdata) | Clears application data by bundle name. This API uses a promise to return the result. |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-f-sys.md#clearupapplicationdata-1) | Clears application data by bundle name. This API uses an asynchronous callback to return the result. |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-f-sys.md#getforegroundapplications) | Obtains applications that are running in the foreground. The application information is defined by [AppStateData](arkts-ability-appstatedata-c.md). This API uses an asynchronous callback to return the result. |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-f-sys.md#getforegroundapplications-1) | Obtains applications that are running in the foreground. The application information is defined by [AppStateData](arkts-ability-appstatedata-c.md). This API uses a promise to return the result. |
| [getKeepAliveAppServiceExtensions](arkts-ability-appmanager-getkeepaliveappserviceextensions-f-sys.md) | Obtains information about all AppServiceExtensionAbility components that are kept alive. The information is defined by [KeepAliveBundleInfo](arkts-ability-appmanager-keepalivebundleinfo-i-sys.md). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned. |
| [getKeepAliveBundles](arkts-ability-appmanager-getkeepalivebundles-f-sys.md) | Obtains information about a specified type of keep-alive application of a user. The application information is defined by [KeepAliveBundleInfo](arkts-ability-appmanager-keepalivebundleinfo-i-sys.md). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned. **Required permissions**: ohos.permission.MANAGE_APP_KEEP_ALIVE |
| [getProcessMemoryByPid](arkts-ability-appmanager-getprocessmemorybypid-f-sys.md#getprocessmemorybypid) | Obtains the memory size of a process. This API uses a promise to return the result. |
| [getProcessMemoryByPid](arkts-ability-appmanager-getprocessmemorybypid-f-sys.md#getprocessmemorybypid-1) | Obtains the memory size of a process. This API uses an asynchronous callback to return the result. |
| [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-f-sys.md#getprocessrunninginfos) | Obtains information about the running processes of the current application. This API uses a promise to return the result. |
| [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-f-sys.md#getprocessrunninginfos-1) | Obtains information about the running processes of the current application. This API uses an asynchronous callback to return the result. |
| [getRunningMultiAppInfo](arkts-ability-appmanager-getrunningmultiappinfo-f-sys.md) | Obtains the information about running applications in multi-app mode. The multi-app mode means that an application can be simultaneously logged in with different accounts on the same device. This API uses a promise to return the result. |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename) | Obtains information about the running processes by bundle name. This API uses an asynchronous callback to return the result. |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename-1) | Obtains information about the running processes by bundle name and user ID. This API uses an asynchronous callback to return the result. |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename-2) | Obtains information about the running processes by bundle name. This API uses a promise to return the result. |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename-3) | Obtains information about the running processes by bundle name and user ID. This API uses a promise to return the result. |
| [getRunningProcessInformationByBundleType](arkts-ability-appmanager-getrunningprocessinformationbybundletype-f-sys.md) | Obtains the information about the running process based on the bundle type. This API uses a promise to return the result. |
| [getSupportedProcessCachePids](arkts-ability-appmanager-getsupportedprocesscachepids-f-sys.md) | Obtains the PIDs of processes that support quick startup after caching in a specified application. This API uses a promise to return the result. |
| [isApplicationRunning](arkts-ability-appmanager-isapplicationrunning-f-sys.md#isapplicationrunning) | Checks whether the application with the specified bundle name is running across all users. This API uses a promise to return the result. |
| [isApplicationRunning](arkts-ability-appmanager-isapplicationrunning-f-sys.md#isapplicationrunning-1) | Checks whether the application with the specified bundle name is running across all users. This API uses an asynchronous callback to return the result. |
| [isSharedBundleRunning](arkts-ability-appmanager-issharedbundlerunning-f-sys.md#issharedbundlerunning) | Checks whether the shared library is in use. This API uses a promise to return the result. |
| [isSharedBundleRunning](arkts-ability-appmanager-issharedbundlerunning-f-sys.md#issharedbundlerunning-1) | Checks whether the shared library is in use. This API uses an asynchronous callback to return the result. |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f-sys.md) | Kills a process by bundle name. This API uses a promise to return the result. |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f-sys.md#killprocessesbybundlename-2) | Kills a process by bundle name. This API uses an asynchronous callback to return the result. |
| [killProcessesInBatch](arkts-ability-appmanager-killprocessesinbatch-f-sys.md) | Kills processes in batches. This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned. **Required permissions**: ohos.permission.KILL_APP_PROCESSES |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md#killprocesswithaccount) | Kills a process by bundle name and account ID. This API uses a promise to return the result. |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md#killprocesswithaccount-1) | Kills a process by bundle name and account ID. This API uses a promise to return the result. |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md#killprocesswithaccount-2) | Kills a process by bundle name and account ID. This API uses an asynchronous callback to return the result. |
| [off](arkts-ability-appmanager-off-f-sys.md#offappforegroundstate) | Unregisters the observer used to listen for application start or exit events. |
| [off](arkts-ability-appmanager-off-f-sys.md#offabilityfirstframestate) | Deregisters the observer used to listen for the complete of the first frame rendering of a given ability. |
| [on](arkts-ability-appmanager-on-f-sys.md#onapplicationstate) | Registers an application state observer, which allows you to filter for specific application lifecycle changes by setting filter criteria. |
| [on](arkts-ability-appmanager-on-f-sys.md#onappforegroundstate) | Registers an observer to listen for application start or exit events. The observer can be used by a system application to observe the start or event events of all applications. |
| [on](arkts-ability-appmanager-on-f-sys.md#onabilityfirstframestate) | Registers an observer to listen for the complete of the first frame rendering of a given ability. |
| [preloadApplication](arkts-ability-appmanager-preloadapplication-f-sys.md) | Preloads an application process. A successful call does not always mean that the preloading is successful. In other words, the target application process may not be created even if the API is successfully called. This API uses a promise to return the result. |
| [setKeepAliveForAppServiceExtension](arkts-ability-appmanager-setkeepaliveforappserviceextension-f-sys.md) | Sets or cancels the keep-alive status for an AppServiceExtensionAbility. This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned. |
| [setKeepAliveForBundle](arkts-ability-appmanager-setkeepaliveforbundle-f-sys.md) | Sets or cancels the keep-alive status for an application that belongs to a specified user. This API uses a promise to return the result. Starting from API version 18, this API can be properly called only on 2-in-1 devices and wearables. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 801 is returned. |
| [terminateMission](arkts-ability-appmanager-terminatemission-f-sys.md) | Terminates a mission. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) | Describes the filter for application lifecycle change events. It can be used as a parameter of [on](arkts-ability-appmanager-on-f-sys.md#onapplicationstate) to filter application lifecycle change events you want to listen for. |
| [KeepAliveBundleInfo](arkts-ability-appmanager-keepalivebundleinfo-i-sys.md) | Describes the keep-alive application information, which can be obtained by calling [getKeepAliveBundles](arkts-ability-appmanager-getkeepalivebundles-f-sys.md) or [getKeepAliveAppServiceExtensions](arkts-ability-appmanager-getkeepaliveappserviceextensions-f-sys.md). |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ProcessState](arkts-ability-appmanager-processstate-e.md) | Enumerates the processes states. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ApplicationState](arkts-ability-appmanager-applicationstate-e-sys.md) | Enumerates the application states. This enum can be used together with [AbilityStateData](arkts-ability-abilitystatedata-c.md) to return the application state. |
| [FilterAbilityStateType](arkts-ability-appmanager-filterabilitystatetype-e-sys.md) | Enumerates the types of ability states to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the ability state types you want to listen for. |
| [FilterAppStateType](arkts-ability-appmanager-filterappstatetype-e-sys.md) | Enumerates the types of application states to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the application state types you want to listen for. |
| [FilterBundleType](arkts-ability-appmanager-filterbundletype-e-sys.md) | Enumerates the types of applications to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the application types you want to listen for. |
| [FilterCallback](arkts-ability-appmanager-filtercallback-e-sys.md) | Enumerates the callbacks to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the callbacks you want to listen for. |
| [FilterProcessStateType](arkts-ability-appmanager-filterprocessstatetype-e-sys.md) | Enumerates the types of process states to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the process state types you want to listen for. |
| [KeepAliveAppType](arkts-ability-appmanager-keepaliveapptype-e-sys.md) | Enumerates the types of applications to be kept alive. |
| [KeepAliveSetter](arkts-ability-appmanager-keepalivesetter-e-sys.md) | Enumerates the types of parties that set to keep applications alive. |
| [PreloadMode](arkts-ability-appmanager-preloadmode-e-sys.md) | Enumerates the modes used for preloading an application process. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [AbilityStateData](arkts-ability-appmanager-abilitystatedata-t.md) | Defines the ability state data. |
| [ApplicationStateObserver](arkts-ability-appmanager-applicationstateobserver-t.md) | Defines the observer used to listen for application state changes. |
| [AppStateData](arkts-ability-appmanager-appstatedata-t.md) | Defines the application state data. |
| [ProcessData](arkts-ability-appmanager-processdata-t.md) | Defines the process data. |
| [ProcessInformation](arkts-ability-appmanager-processinformation-t.md) | Defines the process information. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [AbilityFirstFrameStateData](arkts-ability-appmanager-abilityfirstframestatedata-t-sys.md) | Defines the data structure reported when the first frame rendering of the UIAbility is complete. |
| [AbilityFirstFrameStateObserver](arkts-ability-appmanager-abilityfirstframestateobserver-t-sys.md) | Defines the listener for the completion of the first frame rendering of the UIAbility. |
| [AppForegroundStateObserver](arkts-ability-appmanager-appforegroundstateobserver-t-sys.md) | Defines the listener for the state of application launch and exit. |
| [RunningMultiAppInfo](arkts-ability-appmanager-runningmultiappinfo-t-sys.md) | Defines the information of an application in multi-app mode in the running state. |
<!--DelEnd-->
