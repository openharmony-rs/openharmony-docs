# @ohos.app.ability.launchServiceManager

This module provides the capability of managing LaunchService.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace launchServiceManager--><!--Device-unnamed-declare namespace launchServiceManager-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [connectService](arkts-ability-launchservicemanager-connectservice-f.md#connectservice-1) | Connects to the LaunchService process for IPC communication. The target LaunchService must have declared the IPC service. If the LaunchService process is not running, the system automatically starts it before the connection is established. The target service and invoker must belong to the same developer. The connection result is delivered through callback in callback. |
| [disconnectService](arkts-ability-launchservicemanager-disconnectservice-f.md#disconnectservice-1) | Disconnect from the LaunchService process. |
| [getInformation](arkts-ability-launchservicemanager-getinformation-f.md#getinformation-1) | This method is used to obtain information about a specified LaunchService. If the application is installed but LaunchService is not registered, the status returned is NOT_REGISTERED and the pid is 0. |
| [register](arkts-ability-launchservicemanager-register-f.md#register-1) | Register the LaunchService. In the module.json5 configuration file, runAtLoad is set to true, the service is registered successfully, and the status is Enabled. The system automatically starts the LaunchService process. Only the applications that contain the launch service can be registered. You need to apply for the corresponding permission based on the application type. - Common applications(non-MDM applications): You need to apply for the ohos.permission.REGISTER_DAEMON_SERVICE permission. - MDM application: You need to apply for the ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE permission. |
| [start](arkts-ability-launchservicemanager-start-f.md#start-1) | Start the LaunchService process. Before invoking this interface, ensure that LaunchService has been registered and is in the Enabled state. |
| [stop](arkts-ability-launchservicemanager-stop-f.md#stop-1) | Stop the LaunchService process. |
| [unregister](arkts-ability-launchservicemanager-unregister-f.md#unregister-1) | Deregister LaunchService. If the LaunchService process is running, the system stops the process when you log out. Only applications that contain the launch service can be registered or deregistered. You need to apply for the corresponding permission based on the application type. - Common applications(non-MDM applications): You need to apply for the ohos.permission.REGISTER_DAEMON_SERVICE permission. - MDM application: You need to apply for the ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE permission. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAllRegisteredInformation](arkts-ability-launchservicemanager-getallregisteredinformation-f-sys.md#getallregisteredinformation-1) | This method is used to obtain information about all registered LaunchServices. |
| [offLaunchServiceObserver](arkts-ability-launchservicemanager-offlaunchserviceobserver-f-sys.md#offlaunchserviceobserver-1) | Log off the watcher used to listen for LaunchService state and process state changes. |
| [onLaunchServiceObserver](arkts-ability-launchservicemanager-onlaunchserviceobserver-f-sys.md#onlaunchserviceobserver-1) | Register an observer to listen to the LaunchService status and process status changes. |
| [setLaunchServicesEnabled](arkts-ability-launchservicemanager-setlaunchservicesenabled-f-sys.md#setlaunchservicesenabled-1) | This method is used to set the enabling status of the LaunchService application. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [LaunchServiceConnectCallback](arkts-ability-launchservicemanager-launchserviceconnectcallback-t.md) | Defines the LaunchService connection callback. |
| [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | Define the descriptor of LaunchService. |
| [LaunchServiceInformation](arkts-ability-launchservicemanager-launchserviceinformation-t.md) | Defines the LaunchService information structure. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [LaunchServiceObserver](arkts-ability-launchservicemanager-launchserviceobserver-t-sys.md) | Defines the watcher of LaunchService status and process status changes. |
| [LaunchServiceProcessStateData](arkts-ability-launchservicemanager-launchserviceprocessstatedata-t-sys.md) | Defines the LaunchService process status change data structure. |
| [LaunchServiceStateData](arkts-ability-launchservicemanager-launchservicestatedata-t-sys.md) | Defines the LaunchService status change data structure. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [LaunchServiceState](arkts-ability-launchservicemanager-launchservicestate-e.md) | Defines the enumeration type of the LaunchService status for [LaunchServiceInformation](arkts-ability-launchserviceinformation-i.md). |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [LaunchServiceProcessState](arkts-ability-launchservicemanager-launchserviceprocessstate-e-sys.md) | Defines the enumeration type of the LaunchService process status, which is used for [LaunchServiceProcessState](arkts-ability-launchserviceprocessstatedata-i-sys.md). |
<!--DelEnd-->
