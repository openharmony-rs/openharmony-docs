# TerminationInfo（系统接口）

表示嵌入式UI的提供方终止时的信息。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface TerminationInfo--><!--Device-unnamed-declare interface TerminationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## code

```TypeScript
code: number
```

定义终止码。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TerminationInfo-code: int--><!--Device-TerminationInfo-code: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

定义额外的终止信息。

**类型：** import('../api/@ohos.app.ability.Want').default

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default--><!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

