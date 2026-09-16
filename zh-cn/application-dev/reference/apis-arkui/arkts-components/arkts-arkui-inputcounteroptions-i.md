# InputCounterOptions

计数器的配置项。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextColor

```TypeScript
counterTextColor?: ColorMetrics
```

设置组件中字符计数器的文本颜色。当用户输入字符数大于最大字符数乘百分比值时，计数器会显示当前输入的字符数，并且计数器的文本颜色为counterTextColor指定的颜色。如果不设置counterTextColor，则计数器的文本颜色为默认颜色，默认颜色为灰色。

**类型：** [ColorMetrics](../arkts-apis/arkts-arkui-colormetrics-t.md)

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextOverflowColor

```TypeScript
counterTextOverflowColor?: ColorMetrics
```

设置组件中字符计数器在溢出时的文本颜色。当用户输入的字符数超过计数器最大长度时，计数器的文本颜色和边框的颜色会切换为counterTextOverflowColor指定的颜色，以提醒用户输入已超出限制。如果不设置counterTe xtOverflowColor，则计数器和边框在溢出时的文本颜色为默认颜色，默认颜色为红色。

**说明：** 

当设置了[InputCounterOptions](arkts-arkui-inputcounteroptions-i.md)的highlightBorder属性时，边框颜色才会被同步更改。

**类型：** [ColorMetrics](../arkts-apis/arkts-arkui-colormetrics-t.md)

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## highlightBorder

```TypeScript
highlightBorder?: boolean
```

如果用户设置计数器时不设置InputCounterOptions，那么当前输入字符数达到最大字符数时，边框和计数器下标将变为红色。如果用户设置显示字符计数器同时thresholdPercentage参数数值在有效区间内，那么当输入字符数超过最大字符数时，边框和计数器下标将变成红色。如果此参数为true，则显示红色边框，参数为false则不显示。<br>默认值：true。

**类型：** boolean

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thresholdPercentage

```TypeScript
thresholdPercentage?: number
```

可输入字符数占最大字符限制的百分比值。字符计数器显示的样式为当前输入字符数/最大字符数。当输入字符数大于最大字符数乘百分比值时，显示字符计数器。有效值区间为[1,100]，数值为小数时，向下取整，如果设置的number超出有效值区间内，不显示字符计数器。设置为undefined时，显示字符计数器，但此参数不生效。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
