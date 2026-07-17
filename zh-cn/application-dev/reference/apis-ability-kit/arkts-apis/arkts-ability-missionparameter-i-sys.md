# MissionParameter（系统接口）

作为[startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md#startsyncremotemissions-1)的入参，表示同步时所需参数的枚举。

**起始版本：** 9

<!--Device-unnamed-export interface MissionParameter--><!--Device-unnamed-export interface MissionParameter-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: string
```

表示设备ID。

**类型：** string

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MissionParameter-deviceId: string--><!--Device-MissionParameter-deviceId: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## fixConflict

```TypeScript
fixConflict: boolean
```

表示是否存在版本冲突，true表示存在冲突，false表示不存在冲突。

**类型：** boolean

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MissionParameter-fixConflict: boolean--><!--Device-MissionParameter-fixConflict: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## tag

```TypeScript
tag: number
```

表示任务的标签，0表示默认标签。

**类型：** number

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MissionParameter-tag: int--><!--Device-MissionParameter-tag: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

