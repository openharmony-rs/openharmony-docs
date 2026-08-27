# ProgressButton

文本下载按钮，可显示具体下载进度。

> **说明：**
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果ProgressButton设置通用属性和通用事件，编
> 译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ProgressButton本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议
> ProgressButton设置通用属性和通用事件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ProgressButton } from '@kit.ArkUI';
```

## clickCallback

```TypeScript
clickCallback: () => void
```

下载按钮的点击回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorOptions

```TypeScript
colorOptions?: ProgressButtonColorOptions
```

下载按钮颜色。用于自定义按钮各部分的颜色（进度条、描边、文本、背景）。需要自定义颜色时传入此参数，不传入时使用系统默认配色方案。

**类型：** [ProgressButtonColorOptions](arkts-arkui-arkui-advanced-progressbutton-progressbuttoncoloroptions-i.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

下载按钮的文本。默认值：空字符串。  
**说明：**最长显示组件宽度，超出部分用省略号代替。从API version 20开始，支持Resource类型。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enable

```TypeScript
enable: boolean
```

下载按钮是否可以点击。true：可以点击。false：不可点击。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## progress

```TypeScript
progress: number
```

下载按钮的当前进度值。取值范围：[0,100]。设置小于0的数值时置为0，设置大于100的数值时置为100。默认值：0

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## progressButtonRadius

```TypeScript
progressButtonRadius?: LengthMetrics
```

下载按钮的圆角（不支持百分比设置）。取值范围：[0, height/2]默认值：height/2设置值小于0时按照0处理，设置其他非法数值时，按照默认值处理。当直接入参为undefined时，按照默认值处理，入参为LengthMetrics.vp时，建议传入具体数值，传入null/undefined会导致显示异常。

**类型：** LengthMetrics

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## progressButtonWidth

```TypeScript
progressButtonWidth?: Length
```

下载按钮的宽度，单位vp。取值范围：大于等于44vp。默认值：44vp。当取值为非Resource类型且小于默认值或取值为非法值时，识别值为默认值。当取值为Resource类型且小于默认值时识别为默认值，为非法值时下载按钮的宽度显示为容器宽度的100%。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
