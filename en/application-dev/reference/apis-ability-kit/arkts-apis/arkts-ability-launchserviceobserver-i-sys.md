# LaunchServiceObserver (System API)

```TypeScript
declare interface LaunchServiceObserver
```

Defines the watcher of LaunchService status and process status changes.

**Since:** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceObserver--><!--Device-unnamed-declare interface LaunchServiceObserver-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## onLaunchServiceProcessStateChanged

```TypeScript
onLaunchServiceProcessStateChanged(processStateData: LaunchServiceProcessStateData): void
```

This interface is invoked when the LaunchService process status changes, including process start and stop events.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceObserver-onLaunchServiceProcessStateChanged(processStateData: LaunchServiceProcessStateData): void--><!--Device-LaunchServiceObserver-onLaunchServiceProcessStateChanged(processStateData: LaunchServiceProcessStateData): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| processStateData | [LaunchServiceProcessStateData](arkts-ability-launchserviceprocessstatedata-i-sys.md) | Yes | Process state change data. |

## onLaunchServiceRegisteredChanged

```TypeScript
onLaunchServiceRegisteredChanged(stateDataList: Array<LaunchServiceStateData>): void
```

This interface is invoked when the registration status of LaunchService changes (registration or deregistration).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceObserver-onLaunchServiceRegisteredChanged(stateDataList: Array<LaunchServiceStateData>): void--><!--Device-LaunchServiceObserver-onLaunchServiceRegisteredChanged(stateDataList: Array<LaunchServiceStateData>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stateDataList | Array&lt;[LaunchServiceStateData](arkts-ability-launchservicestatedata-i-sys.md)&gt; | Yes | List of LaunchServices whose status changes. |
