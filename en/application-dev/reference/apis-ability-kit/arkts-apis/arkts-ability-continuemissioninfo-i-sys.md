# ContinueMissionInfo (System API)

```TypeScript
export interface ContinueMissionInfo
```

The module defines the parameters required for initiating mission continuation with the bundle name specified. For details about mission continuation, see [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continuemission3)

**Since:** 10

<!--Device-unnamed-export interface ContinueMissionInfo--><!--Device-unnamed-export interface ContinueMissionInfo-End-->

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

<!--Device-ContinueMissionInfo-bundleName: string--><!--Device-ContinueMissionInfo-bundleName: string-End-->

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

<!--Device-ContinueMissionInfo-continueType?: string--><!--Device-ContinueMissionInfo-continueType?: string-End-->

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

<!--Device-ContinueMissionInfo-dstDeviceId: string--><!--Device-ContinueMissionInfo-dstDeviceId: string-End-->

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

<!--Device-ContinueMissionInfo-srcBundleName?: string--><!--Device-ContinueMissionInfo-srcBundleName?: string-End-->

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

<!--Device-ContinueMissionInfo-srcDeviceId: string--><!--Device-ContinueMissionInfo-srcDeviceId: string-End-->

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

<!--Device-ContinueMissionInfo-wantParam: Record<string, Object>--><!--Device-ContinueMissionInfo-wantParam: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.
