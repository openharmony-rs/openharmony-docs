# FillRequest

```TypeScript
export interface FillRequest
```

自动填充的填充请求。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface FillRequest--><!--Device-unnamed-export interface FillRequest-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## customData

```TypeScript
customData: CustomData
```

自定义数据。

**类型：** [CustomData](arkts-ability-customdata-i-sys.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FillRequest-customData: CustomData--><!--Device-FillRequest-customData: CustomData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## isPopup

```TypeScript
isPopup: boolean
```

自动填充服务是否拉起popup窗口。

true：当前拉起popup窗口。

false：当前拉起模态窗。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FillRequest-isPopup: boolean--><!--Device-FillRequest-isPopup: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。
