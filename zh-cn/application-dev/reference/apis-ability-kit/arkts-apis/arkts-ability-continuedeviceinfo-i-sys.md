# ContinueDeviceInfo（系统接口）

表示发起Mission迁移时所需参数的接口对象，迁移Mission详见： [continueMission接口](arkts-ability-distributedmissionmanager-continuemission-f-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## dstDeviceId

```TypeScript
dstDeviceId: string
```

表示Mission迁移目标设备ID。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## missionId

```TypeScript
missionId: number
```

表示Mission迁移任务ID。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## srcDeviceId

```TypeScript
srcDeviceId: string
```

表示Mission迁移源设备ID。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## wantParam

```TypeScript
wantParam: Record<string, Object>
```

表示Mission迁移扩展参数，用于传递任务迁移时的自定义信息。可以包含开发者自定义的键值对，用于标识迁移场景或携带迁移相关的配置信息。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。
