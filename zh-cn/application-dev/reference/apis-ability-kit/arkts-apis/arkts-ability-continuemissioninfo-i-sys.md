# ContinueMissionInfo（系统接口）

表示发起按照包名迁移时所需参数的接口对象，迁移Mission详见： [continueMission接口](arkts-ability-distributedmissionmanager-continuemission-f-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

表示任务所属目标端应用包名。最大长度255字符。该参数作为srcBundleName的默认值使用。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## continueType

```TypeScript
continueType?: string
```

表示任务所属应用迁移类型。如果不传，则使用系统默认值。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

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

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## srcBundleName

```TypeScript
srcBundleName?: string
```

表示任务所属源端应用包名。当源端和目标端应用包名不同时需要传入（如跨应用迁移、应用包名变更等场景），不传入时默认与bundleName相同。最大长度255字符。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

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

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## wantParam

```TypeScript
wantParam: Record<string, Object>
```

表示扩展参数。用于传递任务迁移时的自定义信息。可以包含开发者自定义的键值对，用于标识迁移场景或携带迁移相关的配置信息。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。
