# TerminationInfo（系统接口）

```TypeScript
declare interface TerminationInfo
```

用于表示被拉起的UIExtensionAbility正常退出时的返回结果。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## code

```TypeScript
code: number
```

被拉起的UIExtensionAbility退出时返回的结果码，0表示正常退出，非0表示异常退出。具体结果码含义由被拉起的UIExtensionAbility定义。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

被拉起UIExtensionAbility退出时返回的数据。未返回数据时该字段为空。

**类型：** import('../api/@ohos.app.ability.Want').default

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
