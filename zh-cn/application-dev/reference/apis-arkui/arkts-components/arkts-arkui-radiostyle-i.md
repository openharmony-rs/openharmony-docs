# RadioStyle

单选框的颜色。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checkedBackgroundColor

```TypeScript
checkedBackgroundColor?: ResourceColor
```

开启状态底板颜色。

默认值：`$r('sys.color.ohos_id_color_text_primary_activated')`

**类型：** ResourceColor

**默认值：** #007DFF

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicatorColor

```TypeScript
indicatorColor?: ResourceColor
```

开启状态内部圆饼颜色。从API version 12开始，indicatorType设置为RadioIndicatorType.TICK和RadioIndicatorType.DOT时，支持修改内部颜色。indicatorType
设置为RadioIndicatorType.CUSTOM时，不支持修改内部颜色。

默认值：`$r('sys.color.ohos_id_color_foreground_contrary')`

**类型：** ResourceColor

**默认值：** #FFFFFF

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uncheckedBorderColor

```TypeScript
uncheckedBorderColor?: ResourceColor
```

关闭状态描边颜色。

默认值：`$r('sys.color.ohos_id_color_switch_outline_off')`

**类型：** ResourceColor

**默认值：** #182431

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

