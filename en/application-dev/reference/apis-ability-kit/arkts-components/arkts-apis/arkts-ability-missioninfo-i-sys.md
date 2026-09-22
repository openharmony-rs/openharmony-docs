# MissionInfo (System API)

```TypeScript
export interface MissionInfo
```

The module defines detailed information about a mission. The information can be obtained through [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md).

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## abilityState

```TypeScript
abilityState: number
```

Indicates the ability state of this mission.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## continuable

```TypeScript
continuable: boolean
```

Indicates whether the mission is continuable. The value **true** means continuable, and **false** means not continuable.

**Type:** boolean

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## iconPath

```TypeScript
iconPath: string
```

Indicates icon path of the mission.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## label

```TypeScript
label: string
```

Indicates the label of the mission, used as the task name displayed in the task list.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## lockedState

```TypeScript
lockedState: boolean
```

Indicates the locked state. The value **true** means the locked state, and **false** means the unlocked state.

**Type:** boolean

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## missionId

```TypeScript
missionId: number
```

Indicates mission id.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## runningState

```TypeScript
runningState: number
```

Indicates the running state. The value **0** means enabled, indicating that the task is active and valid, and the corresponding Ability is running or can be restored to the foreground. The value **-1** means not enabled, indicating that the task is closed, destroyed, or cannot be restored.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp: string
```

Indicates the recent created or updated time of the mission. Unit: ns

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## unclearable

```TypeScript
unclearable: boolean
```

Indicates whether the mission can be manually deleted by the user. The value **true** means it can be manually deleted by the user, and **false** means it cannot be manually deleted by the user.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## want

```TypeScript
want: Want
```

Indicates want of the mission.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 8

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.
