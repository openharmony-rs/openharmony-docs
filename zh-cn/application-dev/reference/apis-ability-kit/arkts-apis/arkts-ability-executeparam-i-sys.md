# ExecuteParam（系统接口）

执行意图调用的参数。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityName

```TypeScript
abilityName: string
```

意图调用Ability名称。 如果通过
[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)
装饰器定义的意图来实现应用跳转，此字段传空字符串即可。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

意图调用Ability所属的应用名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId?: string
```

设备标识。获取路径：
{@link @ohos.distributedDeviceManager:distributedDeviceManager.DeviceManager#getAvailableDeviceListSync}

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## displayId

```TypeScript
displayId?: number
```

意图调用时指定的物理屏幕id，该参数应为整数，仅在executeMode为UI_ABILITY_FOREGROUND时生效。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## executeMode

```TypeScript
executeMode: insightIntent.ExecuteMode
```

意图调用执行模式。 如果通过
[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)
装饰器定义的意图来实现应用跳转，此字段需填写（可填任意符合定义的值），但实际不会生效。

**类型：** insightIntent.ExecuteMode

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## flags

```TypeScript
flags?: number
```

意图调用时，意图调用方给意图执行方授权的uris的[flags](arkts-ability-flags-e.md)。

**说明：**

该参数仅支持FLAG_AUTH_READ_URI_PERMISSION、FLAG_AUTH_WRITE_URI_PERMISSION、FLAG_AUTH_READ_URI_PERMISSION|
FLAG_AUTH_WRITE_URI_PERMISSION。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## insightIntentName

```TypeScript
insightIntentName: string
```

意图调用名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## insightIntentParam

```TypeScript
insightIntentParam: Record<string, Object>
```

意图调用参数。

**类型：** Record<string, Object>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName: string
```

意图调用Ability所属的模块名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uris

```TypeScript
uris?: Array<string>
```

意图调用时，意图调用方给意图执行方授权的URI列表。 如果通过
[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)
装饰器定义的意图来实现应用跳转，此字段必选，仅读取数组第一个元素作为[openLink](arkts-ability-uiabilitycontext-c.md#openlink-1)的URI。

**类型：** Array<string>

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

目标意图所属的用户ID。

**说明：**

如果调用方应用的用户ID与目标意图所属的用户ID不同，则需要申请权限`ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS`。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

