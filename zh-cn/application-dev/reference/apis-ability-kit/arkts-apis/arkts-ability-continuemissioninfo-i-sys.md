# ContinueMissionInfo（系统接口）

表示发起按照包名迁移时所需参数的枚举，迁移Mission详见：[continueMission接口](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continuemission-3)

**起始版本：** 10

<!--Device-unnamed-export interface ContinueMissionInfo--><!--Device-unnamed-export interface ContinueMissionInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

表示任务所属目标端应用包名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueMissionInfo-bundleName: string--><!--Device-ContinueMissionInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## continueType

```TypeScript
continueType?: string
```

表示任务所属应用迁移类型。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueMissionInfo-continueType?: string--><!--Device-ContinueMissionInfo-continueType?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## dstDeviceId

```TypeScript
dstDeviceId: string
```

表示任务迁移目标设备ID。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueMissionInfo-dstDeviceId: string--><!--Device-ContinueMissionInfo-dstDeviceId: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## srcBundleName

```TypeScript
srcBundleName?: string
```

表示任务所属源端应用包名，默认与bundleName相同。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueMissionInfo-srcBundleName?: string--><!--Device-ContinueMissionInfo-srcBundleName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## srcDeviceId

```TypeScript
srcDeviceId: string
```

表示任务迁移源设备ID。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueMissionInfo-srcDeviceId: string--><!--Device-ContinueMissionInfo-srcDeviceId: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## wantParam

```TypeScript
wantParam: Record<string, Object>
```

表示扩展参数。

**类型：** Record<string, Object>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueMissionInfo-wantParam: Record<string, Object>--><!--Device-ContinueMissionInfo-wantParam: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

