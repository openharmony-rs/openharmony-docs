# ContinueDeviceInfo (System API)

The module defines the parameters required for initiating mission continuation. For details about mission continuation, see [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md)

**Since:** 9

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

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.
