# LaunchServiceInformation

```TypeScript
declare interface LaunchServiceInformation
```

Information structure of LaunchService.

**Since:** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceInformation--><!--Device-unnamed-declare interface LaunchServiceInformation-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## descriptor

```TypeScript
descriptor: LaunchServiceDescriptor
```

Descriptor of LaunchService.

**Type:** [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceInformation-descriptor: LaunchServiceDescriptor--><!--Device-LaunchServiceInformation-descriptor: LaunchServiceDescriptor-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

PID of the LaunchService process. The value 0 indicates that the process is not started. A value greater than 0 indicates the PID of the running process. The value must be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceInformation-pid: int--><!--Device-LaunchServiceInformation-pid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: launchServiceManager.LaunchServiceState
```

LaunchService status.

**Type:** [launchServiceManager.LaunchServiceState](arkts-ability-launchservicemanager-launchservicestate-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceInformation-state: launchServiceManager.LaunchServiceState--><!--Device-LaunchServiceInformation-state: launchServiceManager.LaunchServiceState-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
