# @ohos.application.missionManager

The missionManager module provides APIs to lock, unlock, and clear missions, and switch a mission to the foreground.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [missionManager/missionManager](arkts-ability-app-ability-missionmanager.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

<!--Device-unnamed-declare namespace missionManager--><!--Device-unnamed-declare namespace missionManager-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-depr-f-sys.md#clearallmissions1) | Clears all unlocked missions. This API uses an asynchronous callback to return the result. |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-depr-f-sys.md#clearallmissions2) | Clears all unlocked missions. This API uses a promise to return the result. |
| [clearMission](arkts-ability-missionmanager-clearmission-depr-f-sys.md#clearmission1) | Clears a given mission, regardless of whether it is locked. This API uses an asynchronous callback to return the result. |
| [clearMission](arkts-ability-missionmanager-clearmission-depr-f-sys.md#clearmission2) | Clears a given mission, regardless of whether it is locked. This API uses a promise to return the result. |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-depr-f-sys.md#getmissioninfo1) | Obtains the information about a given mission. This API uses an asynchronous callback to return the result. |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-depr-f-sys.md#getmissioninfo2) | Obtains the information about a given mission. This API uses a promise to return the result. |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-depr-f-sys.md#getmissioninfos1) | Obtains information about all missions. This API uses an asynchronous callback to return the result. |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-depr-f-sys.md#getmissioninfos2) | Obtains information about all missions. This API uses a promise to return the result. |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-depr-f-sys.md#getmissionsnapshot1) | Obtains the snapshot of a given mission. This API uses an asynchronous callback to return the result. |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-depr-f-sys.md#getmissionsnapshot2) | Obtains the snapshot of a given mission. This API uses a promise to return the result. |
| [lockMission](arkts-ability-missionmanager-lockmission-depr-f-sys.md#lockmission1) | Locks a given mission. This API uses an asynchronous callback to return the result. |
| [lockMission](arkts-ability-missionmanager-lockmission-depr-f-sys.md#lockmission2) | Locks a given mission. This API uses a promise to return the result. |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-depr-f-sys.md#movemissiontofront1) | Switches a given mission to the foreground. This API uses an asynchronous callback to return the result. |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-depr-f-sys.md#movemissiontofront2) | Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses an asynchronous callback to return the result. |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-depr-f-sys.md#movemissiontofront3) | Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses a promise to return the result. |
| [registerMissionListener](arkts-ability-missionmanager-registermissionlistener-depr-f-sys.md#registermissionlistener) | Registers a listener to observe the mission status. |
| [unlockMission](arkts-ability-missionmanager-unlockmission-depr-f-sys.md#unlockmission1) | Unlocks a given mission. This API uses an asynchronous callback to return the result. |
| [unlockMission](arkts-ability-missionmanager-unlockmission-depr-f-sys.md#unlockmission2) | Unlocks a given mission. This API uses a promise to return the result. |
| [unregisterMissionListener](arkts-ability-missionmanager-unregistermissionlistener-depr-f-sys.md#unregistermissionlistener1) | Unregisters a mission status listener. This API uses an asynchronous callback to return the result. |
| [unregisterMissionListener](arkts-ability-missionmanager-unregistermissionlistener-depr-f-sys.md#unregistermissionlistener2) | Unregisters a mission status listener. This API uses a promise to return the result. |
<!--DelEnd-->
