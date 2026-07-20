# ContinuableInfo（系统接口）

当注册应用任务流转状态监听的回调时，返回应用任务流转状态和流转信息，注册详见：[on('continueStateChange')接口](@ohos.distributedMissionManager:distributedMissionManager.on(type: 'continueStateChange', callback: Callback<ContinueCallbackInfo>))。

**起始版本：** 10

<!--Device-unnamed-export interface ContinuableInfo--><!--Device-unnamed-export interface ContinuableInfo-End-->

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

<!--Device-ContinuableInfo-bundleName: string--><!--Device-ContinuableInfo-bundleName: string-End-->

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

<!--Device-ContinuableInfo-continueType?: string--><!--Device-ContinuableInfo-continueType?: string-End-->

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

<!--Device-ContinuableInfo-srcBundleName?: string--><!--Device-ContinuableInfo-srcBundleName?: string-End-->

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

<!--Device-ContinuableInfo-srcDeviceId: string--><!--Device-ContinuableInfo-srcDeviceId: string-End-->

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

<!--Device-ContinuableInfo-targetAppIds?: Array<string>--><!--Device-ContinuableInfo-targetAppIds?: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

