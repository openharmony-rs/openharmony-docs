# @ohos.distributedMissionManager

The distributedMissionManager module implements mission management across devices. You can use the APIs provided by this module to register or unregister a mission status listener, start or stop synchronizing a remote mission list, and continue a mission on a remote device by mission ID or bundle name.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | Continues a mission on a remote device, with the mission ID specified. This API uses an asynchronous callback to return the result. |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | Continues a mission on a remote device, with the mission ID specified. This API uses a promise to return the result. |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | Continues a mission on a remote device, with the bundle name specified. This API uses an asynchronous callback to return the result. |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | Continues a mission on a remote device, with the bundle name specified. This API uses a promise to return the result. |
| [off](arkts-ability-distributedmissionmanager-off-f-sys.md#offcontinuestatechange) | Unsubscribes from continuation state change events of the current mission. |
| [on](arkts-ability-distributedmissionmanager-on-f-sys.md#oncontinuestatechange) | Subscribes to continuation state change events of the current mission. |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md) | Registers a mission status listener. This API uses an asynchronous callback to return the result. |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md) | Registers a mission status listener. This API uses a promise to return the result. |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md) | Starts to synchronize the remote mission list. This API uses an asynchronous callback to return the result. |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md) | Starts to synchronize the remote mission list. This API uses a promise to return the result. |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md) | Stops synchronizing the remote mission list. This API uses an asynchronous callback to return the result. |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md) | Stops synchronizing the remote mission list. This API uses a promise to return the result. |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md) | Unregisters a mission status listener. This API uses an asynchronous callback to return the result. |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md) | Unregisters a mission status listener. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ContinueCallbackInfo](arkts-ability-distributedmissionmanager-continuecallbackinfo-i-sys.md) | Defines the information about the callback that is triggered for mission continuation state changes. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ContinueState](arkts-ability-distributedmissionmanager-continuestate-e-sys.md) | Enumerates the mission continuation states. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ContinuableInfo](arkts-ability-distributedmissionmanager-continuableinfo-t-sys.md) | Continuable information corresponding to ability. |
| [ContinueCallback](arkts-ability-distributedmissionmanager-continuecallback-t-sys.md) | ContinueCallback registered for notify continue result. |
| [ContinueDeviceInfo](arkts-ability-distributedmissionmanager-continuedeviceinfo-t-sys.md) | Parameters corresponding to continue mission. |
| [ContinueMissionInfo](arkts-ability-distributedmissionmanager-continuemissioninfo-t-sys.md) | Parameters corresponding to continue mission. |
| [MissionCallback](arkts-ability-distributedmissionmanager-missioncallback-t-sys.md) | Defines the callback invoked after synchronization starts. It is used as an input parameter in [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md). |
| [MissionDeviceInfo](arkts-ability-distributedmissionmanager-missiondeviceinfo-t-sys.md) | Defines the parameters required for registering a listener. It is used as an input parameter in [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md). |
| [MissionParameter](arkts-ability-distributedmissionmanager-missionparameter-t-sys.md) | Defines the parameters required for mission synchronization. It is used an input parameter in [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md). |
<!--DelEnd-->
