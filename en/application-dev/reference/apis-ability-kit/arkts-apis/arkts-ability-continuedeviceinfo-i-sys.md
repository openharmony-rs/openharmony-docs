# ContinueDeviceInfo (System API)

```TypeScript
export interface ContinueDeviceInfo
```

The module defines the parameters required for initiating mission continuation. For details about mission continuation, see [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continuemission1)

**Since:** 9

<!--Device-unnamed-export interface ContinueDeviceInfo--><!--Device-unnamed-export interface ContinueDeviceInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## dstDeviceId

```TypeScript
dstDeviceId: string
```

Indicates the target deviceId to continue mission.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinueDeviceInfo-dstDeviceId: string--><!--Device-ContinueDeviceInfo-dstDeviceId: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## missionId

```TypeScript
missionId: number
```

Indicates the mission to continue.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinueDeviceInfo-missionId: int--><!--Device-ContinueDeviceInfo-missionId: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## srcDeviceId

```TypeScript
srcDeviceId: string
```

Indicates the original deviceId to continue mission.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinueDeviceInfo-srcDeviceId: string--><!--Device-ContinueDeviceInfo-srcDeviceId: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## wantParam

```TypeScript
wantParam: Record<string, Object>
```

Indicates the extended param.

**Type:** Record&lt;string, Object&gt;

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinueDeviceInfo-wantParam: Record<string, Object>--><!--Device-ContinueDeviceInfo-wantParam: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.
