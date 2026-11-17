# LaunchServiceProcessStateData (System API)

```TypeScript
declare interface LaunchServiceProcessStateData
```

Describes the status change of the LaunchService process and is used for the [LaunchServiceObserver] {./application/LaunchServiceObserver:LaunchServiceObserver}.

**Since:** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceProcessStateData--><!--Device-unnamed-declare interface LaunchServiceProcessStateData-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## descriptor

```TypeScript
descriptor: LaunchServiceDescriptor
```

Descriptor for starting the service.

**Type:** [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceProcessStateData-descriptor: LaunchServiceDescriptor--><!--Device-LaunchServiceProcessStateData-descriptor: LaunchServiceDescriptor-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## pid

```TypeScript
pid: number
```

PID of the LaunchService process. The value 0 indicates that the process is not running. A value greater than 0 indicates that the process is running. The value must be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceProcessStateData-pid: int--><!--Device-LaunchServiceProcessStateData-pid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## state

```TypeScript
state: launchServiceManager.LaunchServiceProcessState
```

LaunchService process status. 0: The LaunchService process is started. 1: The LaunchService process is stopped. The value must be an integer.

**Type:** [launchServiceManager.LaunchServiceProcessState](arkts-ability-launchservicemanager-launchserviceprocessstate-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceProcessStateData-state: launchServiceManager.LaunchServiceProcessState--><!--Device-LaunchServiceProcessStateData-state: launchServiceManager.LaunchServiceProcessState-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
