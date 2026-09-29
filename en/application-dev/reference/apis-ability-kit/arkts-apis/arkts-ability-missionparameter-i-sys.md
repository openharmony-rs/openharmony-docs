# MissionParameter (System API)

```TypeScript
export interface MissionParameter
```

Parameters corresponding to mission.

**Since:** 9

<!--Device-unnamed-export interface MissionParameter--><!--Device-unnamed-export interface MissionParameter-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: string
```

Device ID.

**Type:** string

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-MissionParameter-deviceId: string--><!--Device-MissionParameter-deviceId: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## fixConflict

```TypeScript
fixConflict: boolean
```

Whether a version conflict exists. **true** if yes, **false** otherwise.

**Type:** boolean

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-MissionParameter-fixConflict: boolean--><!--Device-MissionParameter-fixConflict: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## tag

```TypeScript
tag: number
```

Tag of the mission. The value **0** means the default tag.

**Type:** number

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-MissionParameter-tag: int--><!--Device-MissionParameter-tag: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.
