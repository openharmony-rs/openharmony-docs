# @ohos.app.ability.missionManager(missionManager)

The missionManager module provides APIs to lock, unlock, and clear missions, and switch a mission to the foreground.

**Since:** 9

<!--Device-unnamed-declare namespace missionManager--><!--Device-unnamed-declare namespace missionManager-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md#clearallmissions1) | Clears all unlocked missions. This API uses an asynchronous callback to return the result. |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md#clearallmissions2) | Clears all unlocked missions. This API uses a promise to return the result. |
| [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md#clearmission1) | Clears a given mission, regardless of whether it is locked. This API uses an asynchronous callback to return the result. |
| [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md#clearmission2) | Clears a given mission, regardless of whether it is locked. This API uses a promise to return the result. |
| [getLowResolutionMissionSnapShot](arkts-ability-missionmanager-getlowresolutionmissionsnapshot-f-sys.md#getlowresolutionmissionsnapshot1) | Obtains the low-resolution snapshot of a given mission. This API uses an asynchronous callback to return the result. |
| [getLowResolutionMissionSnapShot](arkts-ability-missionmanager-getlowresolutionmissionsnapshot-f-sys.md#getlowresolutionmissionsnapshot2) | Obtains the low-resolution snapshot of a given mission. This API uses a promise to return the result. |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md#getmissioninfo1) | Obtains the mission information. This API uses an asynchronous callback to return the result. |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md#getmissioninfo2) | Obtains the mission information. This API uses a promise to return the result. |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getmissioninfos1) | Obtains information about all missions. This API uses an asynchronous callback to return the result. |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getmissioninfos2) | Obtains information about all missions. This API uses a promise to return the result. |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md#getmissionsnapshot1) | Obtains the snapshot of a given mission. This API uses an asynchronous callback to return the result. |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md#getmissionsnapshot2) | Obtains the snapshot of a given mission. This API uses a promise to return the result. |
| [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md#lockmission1) | Locks a given mission. This API is applicable to scenarios where a mission needs to be kept from being cleaned up, such as when a system management application needs to keep key missions running in the background. This API uses an asynchronous callback to return the result. |
| [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md#lockmission2) | Locks a given mission. This API is applicable to scenarios where a mission needs to be kept from being cleaned up, such as when a system management application needs to keep key missions running in the background. This API uses a promise to return the result. |
| [moveMissionsToBackground](arkts-ability-missionmanager-movemissionstobackground-f-sys.md#movemissionstobackground1) | Switches a batch of missions to the background. The mission IDs returned are sorted by mission level when the missions are switched. This API uses an asynchronous callback to return the result. |
| [moveMissionsToBackground](arkts-ability-missionmanager-movemissionstobackground-f-sys.md#movemissionstobackground2) | Switches a batch of missions to the background. The mission IDs returned are sorted by mission level when the missions are switched. This API uses a promise to return the result. |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#movemissionstoforeground1) | Switches a batch of missions to the foreground. This API uses an asynchronous callback to return the result. |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#movemissionstoforeground2) | Switches a batch of missions to the foreground, and moves the mission with the specified ID to the top. This API uses an asynchronous callback to return the result. |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#movemissionstoforeground3) | Switches a batch of missions to the foreground, and moves the mission with the specified ID to the top. This API uses a promise to return the result. |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#movemissiontofront1) | Switches a given mission to the foreground. This API uses an asynchronous callback to return the result. |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#movemissiontofront2) | Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses an asynchronous callback to return the result. |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#movemissiontofront3) | Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses a promise to return the result. |
| [off('mission')](arkts-ability-missionmanager-off-f-sys.md#offmission) | Deregisters a mission status listener. This API uses an asynchronous callback to return the result. |
| [off('mission')](arkts-ability-missionmanager-off-f-sys.md#offmission) | Unregisters a mission status listener. This API uses a promise to return the result. |
| [on('mission')](arkts-ability-missionmanager-on-f-sys.md#onmission) | Registers a listener to observe the mission status. |
| [unlockMission](arkts-ability-missionmanager-unlockmission-f-sys.md#unlockmission1) | Unlocks a given mission. This API is applicable to scenarios where a locked mission is allowed to be cleaned up by the system, such as when a system management application no longer needs to keep a mission running in the background. This API uses an asynchronous callback to return the result. |
| [unlockMission](arkts-ability-missionmanager-unlockmission-f-sys.md#unlockmission2) | Unlocks a given mission. This API is applicable to scenarios where a locked mission is allowed to be cleaned up by the system, such as when a system management application no longer needs to keep a mission running in the background. This API uses a promise to return the result. |
| [off('missionEvent')](arkts-ability-missionmanager-off-f-sys.md#offmissionevent) | Deregisters a mission status listener. This API uses an asynchronous callback to return the result. |
| [off('missionEvent')](arkts-ability-missionmanager-off-f-sys.md#offmissionevent) | Unregisters a mission status listener. This API uses a promise to return the result. |
| [on('missionEvent')](arkts-ability-missionmanager-on-f-sys.md#onmissionevent) | Registers a listener to observe the mission status. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [MissionInfo](arkts-ability-missionmanager-missioninfo-t-sys.md) | Mission information corresponding to ability. |
| [MissionListener](arkts-ability-missionmanager-missionlistener-t-sys.md) | MissionListener registered by app. |
| [MissionSnapshot](arkts-ability-missionmanager-missionsnapshot-t-sys.md) | Mission snapshot corresponding to mission. |
<!--DelEnd-->
