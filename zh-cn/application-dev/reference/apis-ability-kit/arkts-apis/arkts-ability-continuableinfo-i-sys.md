# ContinuableInfo（系统接口）

当注册应用任务流转状态监听的回调时，返回应用任务流转状态和流转信息，注册详见： on('continueStateChange')接口。

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

表示任务所属目标端应用包名。该参数作为srcBundleName的默认值使用，当srcBundleName未传入时，其值默认与bundleName相同。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## continueType

```TypeScript
continueType?: string
```

表示任务所属应用迁移类型。取值由应用在配置文件中自定义，用于标识不同的任务流转策略（如多设备协同时的任务流转、跨设备复制任务状态等场景）。如果不传，则使用系统默认值。

**类型：** string

**起始版本：** 12

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

## targetAppIds

```TypeScript
targetAppIds?: Array<string>
```

表示任务所属目标应用ID列表。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。
