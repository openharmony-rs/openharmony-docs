# MissionParameter（系统接口）

作为[startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md)的入参，表示同步远端设备任务列表时所需的参数对象，包含deviceId、fixConflict和tag等字段。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: string
```

同步目标设备的ID。

**类型：** string

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## fixConflict

```TypeScript
fixConflict: boolean
```

是否处理版本冲突，true表示处理冲突，false表示不处理冲突。

**类型：** boolean

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## tag

```TypeScript
tag: number
```

表示任务的标签，取值为非负整数，0表示默认标签，用于标识和区分不同的同步任务。

**类型：** number

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。
