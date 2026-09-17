# ContinueMissionInfo (System API)

The module defines the parameters required for initiating mission continuation with the bundle name specified. For details about mission continuation, see [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md)

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the target application to which the mission belongs.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## continueType

```TypeScript
continueType?: string
```

Continuation type of the application to which the mission belongs.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## dstDeviceId

```TypeScript
dstDeviceId: string
```

ID of the target device.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## srcBundleName

```TypeScript
srcBundleName?: string
```

Bundle name of the source application to which the mission belongs. The value is the same as that of **bundleName** by default.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## srcDeviceId

```TypeScript
srcDeviceId: string
```

ID of the source device.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## wantParam

```TypeScript
wantParam: Record<string, Object>
```

Extended parameters.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.
