# LaunchServiceStateData (System API)

```TypeScript
declare interface LaunchServiceStateData
```

Describes the status change data of the LaunchService. This data is used for [LaunchServiceObserver] {./application/LaunchServiceObserver:LaunchServiceObserver}.

**Since:** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceStateData--><!--Device-unnamed-declare interface LaunchServiceStateData-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## descriptor

```TypeScript
descriptor: LaunchServiceDescriptor
```

Descriptor of LaunchService.

**Type:** [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceStateData-descriptor: LaunchServiceDescriptor--><!--Device-LaunchServiceStateData-descriptor: LaunchServiceDescriptor-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## registered

```TypeScript
registered: boolean
```

Latest status after the registration status of LaunchService changes. true indicates registered, and false indicates not registered.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceStateData-registered: boolean--><!--Device-LaunchServiceStateData-registered: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
