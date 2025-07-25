# 基础类型定义

>**说明：**
>
>本模块首批接口从API version 7开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。

## Resource

资源引用类型，用于设置组件属性的值。各类资源文件，需要放入特定子目录中存储管理，资源目录的示例请参考[资源分类](../../../quick-start/resource-categories-and-access.md#资源分类)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

可以通过`$r`或者`$rawfile`创建Resource类型对象，不可以修改Resource中的各属性的值。

- `$r('belonging.type.name')`

  belonging：系统资源或者应用资源，相应的取值为'sys'和'app'；

  type：资源类型，支持'boolean'、'color'、'float'、'intarray'、'integer'、'pattern'、'plural'、'strarray'、'string'、'media'；

  name：资源名称，在资源定义时确定。

- `$rawfile('filename')`

  filename：工程中resources/rawfile目录下的文件名称。

>  **说明：**
>
>  引用资源类型时，需确保资源类型对象内的数据类型与当前以资源类型作为参数的属性方法本身的类型一致。例如某个属性方法支持设置string | Resource，那么在使用Resource引用类型时，其数据类型也应当为string。
>
>  引用资源类型时，需确保资源类型对象用法为当前支持的用法，否则当前以资源类型作为参数的属性效果将和不设置该属性相同。

## Length

长度类型，用于描述尺寸单位。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| string                | 需要显式指定[像素单位](ts-pixel-units.md)，如'10px'，也可设置百分比字符串，如'100%'。<br/>**说明：** <br/>不指定像素单位时，默认单位vp，如'10'，等同于10。 |
| number                | 默认单位vp。                                |
| [Resource](#resource) | 资源引用类型，引入系统资源或者应用资源中的尺寸。               |

## ResourceStr

字符串类型，用于描述字符串入参可以使用的类型。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                        |
| --------------------- | ------------------------- |
| string                | 字符串类型。                    |
| [Resource](#resource) | 资源引用类型，引入系统资源或者应用资源中的字符串。 |

## Padding

内边距类型，用于描述组件不同方向的内边距。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明                   |
| ------ | ----------------- | ---- | -------------------- |
| top    | [Length](#length) | 否    | 上内边距，组件内元素距组件顶部的尺寸。  |
| right  | [Length](#length) | 否    | 右内边距，组件内元素距组件右边界的尺寸。 |
| bottom | [Length](#length) | 否    | 下内边距，组件内元素距组件底部的尺寸。  |
| left   | [Length](#length) | 否    | 左内边距，组件内元素距组件左边界的尺寸。 |

## LocalizedPadding<sup>12+</sup>

内边距类型，用于描述组件不同方向的内边距。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明                   |
| ------ | ----------------- | ---- | -------------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 上内边距，组件内元素距组件顶部的尺寸。  |
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 右内边距，组件内元素距组件右边界的尺寸。<br />从右至左显示语言模式下为<br />左内边距，组件内元素距组件左边界的尺寸。 |
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 下内边距，组件内元素距组件底部的尺寸。  |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 左内边距，组件内元素距组件左边界的尺寸。<br />从右至左显示语言模式下为<br />右内边距，组件内元素距组件右边界的尺寸。 |

## Margin

外边距类型，用于描述组件不同方向的外边距。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明                   |
| ------ | ----------------- | ---- | -------------------- |
| top    | [Length](#length) | 否    | 上外边距，组件顶部距组件外元素的尺寸。  |
| right  | [Length](#length) | 否    | 右外边距，组件右边界距组件外元素的尺寸。 |
| bottom | [Length](#length) | 否    | 下外边距，组件底部距组件外元素的尺寸。  |
| left   | [Length](#length) | 否    | 左外边距，组件左边界距组件外元素的尺寸。 |

## LocalizedMargin<sup>12+</sup>

外边距类型，用于描述组件不同方向的外边距。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明                   |
| ------ | ----------------- | ---- | -------------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 上外边距，组件顶部距组件外元素的尺寸。  |
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 右外边距，组件右边界距组件外元素的尺寸。<br />从右至左显示语言模式下为<br />左外边距，组件左边界距组件外元素的尺寸。 |
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 下外边距，组件底部距组件外元素的尺寸。  |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 左外边距，组件左边界距组件外元素的尺寸。<br />从右至左显示语言模式下为<br />右外边距，组件右边界距组件外元素的尺寸。 |

## EdgeWidths<sup>9+</sup>

边框宽度类型，用于描述组件边框不同方向的宽度。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明       |
| ------ | ----------------- | ---- | -------- |
| top    | [Length](#length) | 否    | 组件上边框宽度。 |
| right  | [Length](#length) | 否    | 组件右边框宽度。 |
| bottom | [Length](#length) | 否    | 组件下边框宽度。 |
| left   | [Length](#length) | 否    | 组件左边框宽度。 |

## LocalizedEdgeWidths<sup>12+</sup>

边框宽度类型，用于描述组件边框不同方向的宽度。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明       |
| ------ | ----------------- | ---- | -------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件上边框宽度。 |
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件右边框宽度。<br />从右至左显示语言模式下为组件左边框宽度。 |
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件下边框宽度。 |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件左边框宽度。<br />从右至左显示语言模式下为组件右边框宽度。 |

## BorderRadiuses<sup>9+</sup>

圆角类型，用于描述组件边框圆角半径。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 类型                | 必填   | 说明         |
| ----------- | ----------------- | ---- | ---------- |
| topLeft     | [Length](#length) | 否    | 组件左上角圆角半径。 |
| topRight    | [Length](#length) | 否    | 组件右上角圆角半径。 |
| bottomLeft  | [Length](#length) | 否    | 组件左下角圆角半径。 |
| bottomRight | [Length](#length) | 否    | 组件右下角圆角半径。 |

## LocalizedBorderRadiuses<sup>12+</sup>

圆角类型，用于描述组件边框圆角半径。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 类型                | 必填   | 说明         |
| ----------- | ----------------- | ---- | ---------- |
| topStart    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件左上角圆角半径。<br />从右至左显示语言模式下为组件右上角圆角半径。 |
| topEnd      | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件右上角圆角半径。<br />从右至左显示语言模式下为组件左上角圆角半径。 |
| bottomStart | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件左下角圆角半径。<br />从右至左显示语言模式下为组件右下角圆角半径。 |
| bottomEnd   | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否    | 组件右下角圆角半径。<br />从右至左显示语言模式下为组件左下角圆角半径。 |

## EdgeColors<sup>9+</sup>

边框颜色，用于描述组件边框四条边的颜色。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                              | 必填   | 说明       |
| ------ | ------------------------------- | ---- | -------- |
| top    | [ResourceColor](#resourcecolor) | 否    | 组件上边框颜色。 |
| right  | [ResourceColor](#resourcecolor) | 否    | 组件右边框颜色。 |
| bottom | [ResourceColor](#resourcecolor) | 否    | 组件下边框颜色。 |
| left   | [ResourceColor](#resourcecolor) | 否    | 组件左边框颜色。 |

## LocalizedEdgeColors<sup>12+</sup>

边框颜色，用于描述组件边框四条边的颜色。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                              | 必填   | 说明       |
| ------ | ------------------------------- | ---- | -------- |
| top    | [ResourceColor](#resourcecolor) | 否    | 组件上边框颜色。 |
| end    | [ResourceColor](#resourcecolor) | 否    | 组件右边框颜色。<br />从右至左显示语言模式下为组件左边框颜色。 |
| bottom | [ResourceColor](#resourcecolor) | 否    | 组件下边框颜色。 |
| start  | [ResourceColor](#resourcecolor) | 否    | 组件左边框颜色。<br />从右至左显示语言模式下为组件右边框颜色。 |

## EdgeStyles<sup>9+</sup>

边框样式，用于描述组件边框四条边的样式。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                                       | 必填   | 说明       |
| ------ | ---------------------------------------- | ---- | -------- |
| top    | [BorderStyle](ts-appendix-enums.md#borderstyle) | 否    | 组件上边框样式。 |
| right  | [BorderStyle](ts-appendix-enums.md#borderstyle) | 否    | 组件右边框样式。 |
| bottom | [BorderStyle](ts-appendix-enums.md#borderstyle) | 否    | 组件下边框样式。 |
| left   | [BorderStyle](ts-appendix-enums.md#borderstyle) | 否    | 组件左边框样式。 |

## Offset

相对布局完成位置坐标偏移量。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型                | 必填   | 说明       |
| ---- | ----------------- | ---- | -------- |
| dx   | [Length](#length) | 是    | 水平方向偏移量。 |
| dy   | [Length](#length) | 是    | 竖直方向偏移量。 |

## RectResult<sup>10+</sup>

位置和尺寸类型，用于描述组件的位置和宽高。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数      | 类型     | 描述 |
| ------- | ------ | ----------------------- |
| x     | number | 水平方向横坐标。|
| y     | number | 竖直方向纵坐标。|
| width | number | 内容宽度大小。|
| height | number | 内容高度大小。|

## ResourceColor

type ResourceColor = [Color](ts-appendix-enums.md#color) | number | string | [Resource](#resource)

颜色类型，用于描述资源颜色类型。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| [Color](ts-appendix-enums.md#color) | 颜色枚举值。                                                 |
| number                              | HEX格式颜色，支持rgb或者argb。示例：0xffffff，0xffff0000。number无法识别传入位数，格式选择依据值的大小，例如0x00ffffff作rgb格式解析 |
| string                              | rgb或者argb格式颜色。示例：'#ffffff'，'#ff000000'，'rgb(255, 100, 255)'，'rgba(255, 100, 255, 0.5)'。 |
| [Resource](#resource)               | 使用引入资源的方式，引入系统资源或者应用资源中的颜色。       |

## LengthConstrain

长度约束，用于对组件最大、最小长度做限制。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 类型                | 必填   | 说明      |
| --------- | ----------------- | ---- | ------- |
| minLength | [Length](#length) | 是    | 组件最小长度。 |
| maxLength | [Length](#length) | 是    | 组件最大长度。 |


## Font

设置文本样式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| size   | [Length](#length)                                            | 否   | 设置文本尺寸，Length为number类型时，使用fp单位。不支持设置百分比字符串。<br>默认值：16.0 |
| weight | [FontWeight](ts-appendix-enums.md#fontweight) \| number \| string | 否   | 设置文本的字体粗细，number类型取值[100, 900]，取值间隔为100，取值越大，字体越粗。<br>默认值：400 \| FontWeight.Normal |
| family | string \| [Resource](#resource)                              | 否   | 设置文本的字体列表。使用多个字体，使用','进行分割，优先级按顺序生效。例如：'Arial, HarmonyOS Sans'。当前支持'HarmonyOS Sans'字体和[注册自定义字体](../js-apis-font.md)。 |
| style  | [FontStyle](ts-appendix-enums.md#fontstyle)                  | 否   | 设置文本的字体样式。<br>默认值：FontStyle.Normal             |

## Area<sup>8+</sup>

区域类型，用于存储元素所占区域信息。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称             | 类型                     | 说明                             |
| -------------- | ---------------------- | ------------------------------ |
| width          | [Length](#length)      | 目标元素的宽度，作为返回值时，类型为number，单位vp。 |
| height         | [Length](#length)      | 目标元素的高度，作为返回值时，类型为number，单位vp。 |
| position       | [Position](#position) | 目标元素左上角相对父元素左上角的位置。            |
| globalPosition | [Position](#position) | 目标元素左上角相对页面左上角的位置。             |

## Position

位置类型，用于表示一个坐标点。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型                | 必填   | 说明                          |
| ---- | ----------------- | ---- | --------------------------- |
| x    | [Length](#length) | 否    | x轴坐标，作为返回值时，类型为number，单位vp。 |
| y    | [Length](#length) | 否    | y轴坐标，作为返回值时，类型为number，单位vp。 |

## LocalizedPosition<sup>12+</sup>

位置类型，用于表示一个坐标点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型                | 必填   | 说明                          |
| ---- | ----------------- | ---- | --------------------------- |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否    | LTR模式时x轴相对左边坐标，RTL模式x轴相对右边坐标。  |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否    | y轴坐标。 |

## Edges<sup>12+</sup>

位置类型，表示相对四边的偏移量。同时设置top和bottom，仅top生效；同时设置left和right，仅left生效。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型     | 必填   | 说明                          |
| ---- | ------ | ---- | --------------------------- |
| top    | [Dimension](#dimension10) | 否    | 相对顶边的偏移量。 |
| bottom    | [Dimension](#dimension10) | 否    | 相对底边的偏移量。 |
| left    | [Dimension](#dimension10) | 否    | 相对左边的偏移量。 |
| right    | [Dimension](#dimension10) | 否    | 相对右边的偏移量。 |

## LocalizedEdges<sup>12+</sup>

位置类型，表示相对四边的偏移量。同时设置top和bottom，仅top生效；同时设置start和end，仅start生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型     | 必填   | 说明                          |
| ---- | ------ | ---- | --------------------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否    | 相对顶边的偏移量。 |
| bottom    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否    | 相对底边的偏移量。 |
| start    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否    | LTR模式时相对左边的偏移量，RTL模式时相对右边的偏移量。|
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否    | LTR模式时相对右边的偏移量，RTL模式时相对左边的偏移量。 |

## ConstraintSizeOptions

设置约束尺寸，组件布局时，进行尺寸范围限制。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 类型                | 必填   | 说明      |
| --------- | ----------------- | ---- | ------- |
| minWidth  | [Length](#length) | 否    | 元素最小宽度。 |
| maxWidth  | [Length](#length) | 否    | 元素最大宽度。 |
| minHeight | [Length](#length) | 否    | 元素最小高度。 |
| maxHeight | [Length](#length) | 否    | 元素最大高度。 |

## SizeOptions

设置宽高尺寸。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明    |
| ------ | ----------------- | ---- | ----- |
| width  | [Length](#length) | 否    | 元素宽度。 |
| height | [Length](#length) | 否    | 元素高度。 |


## BorderOptions

边框属性集合，用于描述边框相关信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 参数类型                                                     | 必填 | 说明               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| width  | [Length](ts-types.md#length)&nbsp;\|&nbsp;[EdgeWidths](ts-universal-attributes-border.md#edgewidths9对象说明)<sup>9+</sup>&nbsp;\|&nbsp;[LocalizedEdgeWidths](ts-universal-attributes-border.md#localizededgewidths12对象说明)<sup>12+</sup> | 否   | 设置边框宽度。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。     |
| color  | [ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[EdgeColors](ts-universal-attributes-border.md#edgecolors9对象说明)<sup>9+</sup>&nbsp;\|&nbsp;[LocalizedEdgeColors](ts-universal-attributes-border.md#localizededgecolors12对象说明)<sup>12+</sup> | 否   | 设置边框颜色。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。     |
| radius | [Length](ts-types.md#length)&nbsp;\|&nbsp;[BorderRadiuses](ts-universal-attributes-border.md#borderradiuses9对象说明)<sup>9+</sup>&nbsp;\|&nbsp;[LocalizedBorderRadiuses](ts-universal-attributes-border.md#localizedborderradiuses12对象说明)<sup>12+</sup> | 否   | 设置边框圆角半径。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 |
| style  | [BorderStyle](ts-appendix-enums.md#borderstyle)&nbsp;\|&nbsp;[EdgeStyles](ts-universal-attributes-border.md#edgestyles9对象说明)<sup>9+</sup> | 否   | 设置边框样式。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。     |
| dashGap<sup>12+</sup>  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)&nbsp;\|&nbsp;[EdgeWidths](ts-universal-attributes-border.md#edgewidths9对象说明)&nbsp;\|&nbsp;[LocalizedEdgeWidths](ts-universal-attributes-border.md#localizededgewidths12对象说明) | 否  | 设置虚线的线段间距，仅在边框样式为虚线时生效。<br/>不支持设置百分比。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**卡片能力：** 该接口不支持在ArkTS卡片中使用。|
| dashWidth<sup>12+</sup>  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)&nbsp;\|&nbsp;[EdgeWidths](ts-universal-attributes-border.md#edgewidths9对象说明)&nbsp;\|&nbsp;[LocalizedEdgeWidths](ts-universal-attributes-border.md#localizededgewidths12对象说明) | 否   | 设置虚线的线段长度，仅在边框样式为虚线时生效。<br/>不支持设置百分比。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**卡片能力：** 该接口不支持在ArkTS卡片中使用。     |

## ColorFilter<sup>9+</sup>

创建具有4*5矩阵的颜色过滤器。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 类型       | 必填   | 描述                                       |
| ----------- | -------- | ---- | ---------------------------------------- |
| constructor | number[] | 是    | 创建具有4\*5矩阵的颜色过滤器，入参为[m\*n]位于m行和n列中矩阵值，矩阵是行优先的。 |


## CustomBuilder<sup>8+</sup>

组件属性方法参数可使用CustomBuilder类型来自定义UI描述。

| 名称            | 类型定义                   | 描述                                       |
| ------------- | ---------------------- | ---------------------------------------- |
| CustomBuilder | (()&nbsp;=&gt;&nbsp;any) \| void | 生成用户自定义组件，在使用时结合[@Builder](../../../ui/state-management/arkts-builder.md)使用。 |

## MarkStyle<sup>10+</sup>对象说明

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 类型                                       | 必填 | 默认值      | 描述                                                         |
| ----------- | ------------------------------------------ | ---- | ----------- | ------------------------------------------------------------ |
| strokeColor | [ResourceColor](ts-types.md#resourcecolor) | 否   | Color.White | 内部图标颜色。                                               |
| size        | [Length](ts-types.md#length)               | 否   | -           | 内部图标大小，单位vp。默认大小与多选框组件宽度相同。<br />不支持百分比形式设置。设置为非法值时，按照默认值处理。 |
| strokeWidth | [Length](ts-types.md#length)               | 否   | 2           | 内部图标粗细，单位vp。不支持设置百分比。设置为非法值时，按照默认值处理。 |

## ModalTransition<sup>10+</sup>

全屏模态转场方式枚举类型，用于设置全屏模态转场类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 描述           |
| ------- | ------------ |
| NONE    | 全屏模态无转场动画。   |
| DEFAULT | 全屏模态上下切换动画。  |
| ALPHA   | 全屏模态透明度渐变动画。 |

## Dimension<sup>10+</sup>

长度类型，用于描述尺寸单位。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| [PX](#px10)               | 需要指定以px像素单位，如'10px'。 |
| [VP](#vp10)                | 需要指定数字或vp像素单位，如10或'10vp'。 |
| [FP](#fp10)                | 需要指定以fp像素单位，如'10fp'。|
| [LPX](#lpx10)              | 需要指定以lpx像素单位，如'10lpx'。|
| [Percentage](#percentage10)        | 需要指定以%像素单位，如'10%'。|
| [Resource](#resource) | 资源引用类型，引入系统资源或者应用资源中的尺寸。|

## PX<sup>10+</sup>

长度类型，用于描述以px像素单位为单位的长度。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| {number}px               | 需要指定以px像素单位，如'10px'。 |

## VP<sup>10+</sup>

长度类型，用于描述以vp像素单位为单位的长度。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| {number}vp\|number | 需要指定数字或vp像素单位，如10或'10vp'。 |

## FP<sup>10+</sup>

长度类型，用于描述以fp像素单位为单位的长度。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| {number}fp               | 需要指定以fp像素单位，如'10fp'。 |

## LPX<sup>10+</sup>

长度类型，用于描述以lpx像素单位为单位的长度。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| {number}lpx               | 需要指定以lpx像素单位，如'10lpx'。 |

## Percentage<sup>10+</sup>

长度类型，用于描述以%像素单位为单位的长度。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| {number}%               | 需要指定以%像素单位，如'10%'。 |

## Degree<sup>10+</sup>

角度类型，用于描述以deg像素单位为单位的长度。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                    | 说明                                     |
| --------------------- | -------------------------------------- |
| {number}deg               | 需要指定以deg像素单位，如'10deg'。 |

## MultiShadowOptions<sup>10+</sup>

投影样式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 参数类型 | 必填 | 描述 |
| ------------- | ------- | ---- | -------- |
| radius | number \| [Resource](#resource) | 否 | 投影模糊半径。 <br/>API version 10及以前，默认值：5<br/>API version 11及以后，默认值：20<br/>单位：vp <br/>**说明：** <br/>设置小于等于0的值时，按默认值显示。|
| offsetX | number \| [Resource](#resource) | 否 | X轴偏移量。 <br/>默认值：5<br/>单位：vp |
| offsetY | number \| [Resource](#resource) | 否 | Y轴偏移量。 <br/>默认值：5<br/>单位：vp |

## SafeAreaType<sup>10+</sup>

扩展安全区域的枚举类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 描述                                       |
| -------- | ------------------------------------------ |
| SYSTEM   | 系统默认非安全区域，包括状态栏、导航栏。   |
| CUTOUT   | 设备的非安全区域，例如刘海屏或挖孔屏区域。 |
| KEYBOARD | 软键盘区域。                               |

## SafeAreaEdge<sup>10+</sup>

扩展安全区域的方向。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 描述       |
| ------ | ---------- |
| TOP    | 上方区域。 |
| BOTTOM | 下方区域。 |
| START  | 前部区域。 |
| END    | 尾部区域。 |

## KeyboardAvoidMode<sup>12+</sup>枚举说明

弹窗避让键盘时，避让模式的枚举类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 值   | 说明                                             |
| ------- | ---- | ------------------------------------------------ |
| DEFAULT | 0    | 默认避让软键盘并在到达极限高度之后进行高度压缩。 |
| NONE    | 1    | 不避让软键盘。                                   |

## LayoutSafeAreaType<sup>12+</sup>

扩展布局安全区域的枚举类型。

| 名称     | 值   | 说明                                             |
| -------- | --- |------------------------------------------ |
| SYSTEM   |  0 |设置后，组件的布局范围可扩展至[组件级安全区（safeAreaPadding）](./ts-universal-attributes-size.md#safeareapadding14)和页面级安全区（状态栏、导航栏、挖孔区）。   |

## LayoutSafeAreaEdge<sup>12+</sup>

扩展安全区域的方向。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 值 | 描述       |
| ------ | --- | ---------- |
| TOP    | 0 | 上方区域。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| BOTTOM | 1 | 下方区域。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| START<sup>20+</sup>      | 2 | 前部区域。LTR模式时表示左侧区域，RTL模式表示右侧区域。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |
| END<sup>20+</sup>        | 3 |尾部区域。LTR模式时表示右侧区域，RTL模式表示左侧区域。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |
| VERTICAL<sup>20+</sup>   | 4 |垂直区域。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |
| HORIZONTAL<sup>20+</sup> | 5 |水平区域。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |
| ALL<sup>20+</sup>        | 6 |全部区域。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |

## TouchPoint<sup>11+</sup>

配置跟手点坐标，不配置时，默认居中。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型定义 | 描述       |
| ------ | ----------------------| ---------- |
| X | [Dimension](#dimension10) | 跟手点X轴坐标。 |
| Y | [Dimension](#dimension10) | 跟手点Y轴坐标。 |

## PixelRoundPolicy<sup>11+</sup>

指定组件级像素取整的方向。

**卡片能力：** 从API version 11开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明                   |
| ------ | ----------------- | ---- | -------------------- |
| start | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | 否 | 组件前部边界取整对齐方式。 |
| top | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | 否 | 组件上部边界取整对齐方式。 |
| end | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | 否 | 组件尾部边界取整对齐方式。 |
| bottom | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | 否 | 组件底部边界取整对齐方式。 |

## VoidCallback<sup>12+</sup>

type VoidCallback：() => void;

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Callback<sup>12+</sup>

Callback<T,V = void> = (data: T) => V;

带参数的函数回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HoverCallback<sup>12+</sup>

hover事件的回调类型。

type HoverCallback = (isHover: boolean, event: HoverEvent) => void;

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称            | 类型                  | 描述                                       |
| ------------- | ---------------------- | ---------------------------------------- |
| HoverCallback | (isHover: boolean, event: HoverEvent) => void | hover事件的回调。 |

## VisibleAreaEventOptions<sup>12+</sup>

关于区域变化相关的参数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名 | 类型                                                | 必填 | 说明                                                         |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | 是   | 阈值数组。其中，每个阈值代表组件可见面积（即组件在屏幕显示区的面积，只计算父组件内的面积，超出父组件部分不会计算）与组件自身面积的比值。每个阈值的取值范围为[0.0, 1.0]，如果开发者设置的阈值超出该范围，则会实际取值0.0或1.0。 |
| expectedUpdateInterval | number | 否 | 定义了开发者期望的计算间隔，单位为ms。默认值：1000|

## VisibleAreaChangeCallback<sup>12+</sup>

组件可见区域变化事件的回调类型。

type VisibleAreaChangeCallback = (isExpanding: boolean, currentRatio: number) => void;

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称            | 类型                   | 描述                                       |
| ------------- | ---------------------- | ---------------------------------------- |
| VisibleAreaChangeCallback | (isExpanding: boolean, currentRatio: number) => void | 组件可见区域变化事件的回调。<br/>-isExpanding：表示组件的可见面积与自身面积的比值与上一次变化相比的情况，比值变大为true，比值变小为false。<br/>-currentRatio：触发回调时，组件可见面积与自身面积的比值。 |

## DividerStyleOptions<sup>12+</sup>

分割线样式属性集合, 用于描述分割线相关信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                                      | 必填 | 说明              |
| ------ | --------------------------------------- |---|-----------------|
| strokeWidth  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup>  | 否 | 分割线的线宽。         |
| color  | [ResourceColor](#resourcecolor) | 否  | 分割线的颜色。         |
| startMargin | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | 否  | 分割线与菜单侧边起始端的距离。 |
| endMargin  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup>| 否  | 分割线与菜单侧边结束端的距离。 |
| mode  | [DividerMode](ts-appendix-enums.md#dividermode19枚举说明)<sup>19+</sup>| 否  | 设置分割线模式。 |

## TextContentControllerBase<sup>10+</sup>

TextInput、TextArea、Search的基础控制器。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### getTextContentRect<sup>10+</sup>

getTextContentRect(): RectResult

获取已编辑文本内容区域相对组件的位置和大小，返回值单位为像素。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型       | 说明       |
| -------------------  | -------- |
| [RectResult](#rectresult10) | 获取已编辑文本内容区域相对组件的位置和大小。 |

> **说明：**
>
> - 初始不输入文本时，返回值中有相对组件的位置信息，大小为0。
> - 返回值中的位置信息是第一个字符相对于可编辑组件的位置。
> - 在Search组件中，返回的位置信息是相对Search组件中搜索图标的偏移值。
> - 有输入时返回信息中的宽度是组件编辑的固定宽度。

### getTextContentLineCount<sup>10+</sup>

getTextContentLineCount(): number

获取已编辑文本内容的行数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型  | 说明       |
| ----- | -------- |
| number| 已编辑文本内容行数。 |

### getCaretOffset<sup>11+</sup>

getCaretOffset(): CaretOffset

返回当前光标所在位置信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                      | 说明               |
| ----------------------- | ---------------- |
| [CaretOffset](#caretoffset11对象说明) | 光标相对输入框的位置。 |

> **说明：**
>
> - 在当前帧更新光标位置同时调用该接口，该接口不生效。
> - 在Search组件中，返回的位置信息是相对Search组件中搜索图标的偏移值。
> - 在Search组件中，不输入文本时，返回值中有相对Search组件的位置信息。
> - 返回值中的位置信息是光标相对于可编辑组件的位置。

### addText<sup>15+</sup>

addText(text: string, textOperationOptions?: TextContentControllerOptions): number

在已编辑文本的指定位置插入文本，默认插入至文本末尾。
拖拽文本的状态下不生效。

`addText`仅影响应用内部的UI表现，不影响输入法应用的内部逻辑，不推荐在预上屏状态下调用。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型   | 必填   | 说明  |
| ------- | ------ | ---- | ----- |
| text | string | 是    | 插入的文本内容。 |
| textOperationOptions   | [TextContentControllerOptions](#textcontentcontrolleroptions15) | 否    | 插入文本的配置选项，不设置时默认插入文本至末尾。 |

**返回值：**

| 类型  | 说明       |
| ----- | -------- |
| number| 插入文本后光标的位置。 |

### deleteText<sup>15+</sup>

deleteText(range?: TextRange): void

删除已编辑文本的指定区域的内容。
拖拽文本的状态下不生效。

`deleteText`仅影响应用内部的UI表现，不影响输入法应用的内部逻辑，不推荐在预上屏状态下调用。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型   | 必填   | 说明  |
| ------- | ------ | ---- | ----- |
| range | [TextRange](ts-text-common.md#textrange12) | 否    | 删除文本的范围，包括删除文本的起始位置和终止位置。<br>未指定删除范围时，默认将删除全部文本。未指定删除文本的起始位置，则默认从下标0开始删除；未指定删除文本的终止位置，则默认以文本末尾作为删除的结束点。 |

### getSelection<sup>15+</sup>

getSelection(): TextRange

返回当前文本的选择范围。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                      | 说明               |
| ----------------------- | ---------------- |
| [TextRange](ts-text-common.md#textrange12) | 文本当前的选择范围，未选中返回光标位置。 |

### clearPreviewText<sup>17+</sup>

clearPreviewText(): void

清除当前的预上屏文本内容。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TextDecorationOptions<sup>12+</sup>对象说明

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 参数类型                                                    | 必填 | 描述                                                         |
| ------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type  | [TextDecorationType](ts-appendix-enums.md#textdecorationtype) | 是   | 设置文本装饰线类型。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| color  | &nbsp;[ResourceColor](#resourcecolor) | 否   | 设置文本装饰线颜色。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| style | [TextDecorationStyle](ts-appendix-enums.md#textdecorationstyle12) | 否   | 设置文本装饰线样式。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |

## SelectionOptions<sup>12+</sup>对象说明

setTextSelection选中文字时的配置。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                            | 必填 | 说明             |
| ---------- | ----------------------------------------------- | ---- | ---------------- |
| menuPolicy | [MenuPolicy](#menupolicy12) | 否   | 菜单弹出的策略。 |

## MenuPolicy<sup>12+</sup>

菜单弹出的策略。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 值   | 说明                               |
| ------- | ---- | ---------------------------------- |
| DEFAULT | 0    | 按照底层默认逻辑决定是否弹出菜单。 |
| HIDE    | 1    | 始终不弹出菜单。                   |
| SHOW    | 2    | 始终弹出菜单。                     |

## CaretOffset<sup>11+</sup>对象说明

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名   | 类型     | 描述             |
| ----- | ------ | -------------- |
| index | number | 光标所在位置的索引值。    |
| x     | number | 光标相对输入框的x坐标位值，单位px。 |
| y     | number | 光标相对输入框的y坐标位值，单位px。 |

## InputCounterOptions<sup>11+</sup>对象说明

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名              | 类型    | 描述                                                         |
| ------------------- | ------- | ------------------------------------------------------------ |
| thresholdPercentage | number  | thresholdPercentage是可输入字符数占最大字符限制的百分比值。字符计数器显示的样式为当前输入字符数/最大字符数。当输入字符数大于最大字符数乘百分比值时，显示字符计数器。thresholdPercentage值的有效值区间为[1,100]，数值为小数时，向下取整，如果设置的number超出有效值区间内，不显示字符计数器。thresholdPercentage设置为undefined，显示字符计数器，但此参数不生效。 |
| highlightBorder     | boolean | 如果用户设置计数器时不设置InputCounterOptions，那么当前输入字符数达到最大字符数时，边框和计数器下标将变为红色。如果用户设置显示字符计数器同时thresholdPercentage参数数值在有效区间内，那么当输入字符数超过最大字符数时，边框和计数器下标将变成红色。如果此参数为true，则显示红色边框。计数器默认显示红色边框。 |

## ChainWeightOptions<sup>14+</sup>对象说明

链中组件的布局权重。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名   | 类型     | 描述             |
| ----- | ------ | -------------- |
| horizontal | number | 组件在竖直方向的布局权重，设置大于0的数字时生效。 <br> 默认值：0 <br> 异常值：0  |
| vertical     | number | 组件在水平方向的布局权重，设置大于0的数字时生效。 <br> 默认值：0 <br> 异常值：0 |

## Configuration

数据类型。用于设置颜色模式和字体缩放倍数。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型   | 只读 | 可选 | 说明       |
| --------- | ------ | ---- | ---- | ---------- |
| colorMode | string | 是   | 否   | 颜色模式。 |
| fontScale | number | 是   | 否   | 字体缩放。 |

## LayoutPolicy<sup>15+</sup>

用于组件宽度和高度的布局策略。


**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型   | 只读 | 可选 | 说明 |
| --------- | ------ | ---- | ---- |---------- |
| matchParent | [LayoutPolicy](ts-types.md#layoutpolicy15) | 是 | 否   | 当前组件自适应父组件布局时，其大小与父组件内容区相等，不包括padding，border和safeAreaPadding。<br>**卡片能力：** 从API version 15开始，该接口支持在ArkTS卡片中使用。 <br>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。|
| wrapContent<sup>20+</sup> | [LayoutPolicy](ts-types.md#layoutpolicy15) | 是 | 否   | 当前组件自适应子组件（内容）时，其大小与子组件（内容）相等，并且其大小受父组件内容区大小约束。<br>**卡片能力：** 从API version 20开始，该接口支持在ArkTS卡片中使用。 <br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。|
| fixAtIdealSize<sup>20+</sup> | [LayoutPolicy](ts-types.md#layoutpolicy15) | 是 | 否   | 当前组件自适应子组件（内容）时，其大小与子组件（内容）相等，并且其大小不受父组件内容区大小约束。<br>**卡片能力：** 从API version 20开始，该接口支持在ArkTS卡片中使用。 <br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。|

>  **说明：**
>
> - LayoutPolicy支持设置三种布局策略：matchParent（自适应父组件布局）、wrapContent（根据内容自适应但不超过父组件尺寸的布局）和fixAtIdealSize（根据内容自适应，可能超过父组件尺寸的布局）。具体示例代码参见[设置布局策略](./ts-universal-attributes-size.md#示例5设置布局策略)。
>
> - wrapContent和fixAtIdealSize场景，组件无法通过内容确定大小时，如果组件大小有默认值，则按照默认值进行测算；如果没有默认值，则按照宽高(0,0)进行测算。
> 
> - 容器设置wrapContent，并且有子组件设置matchParent时，容器先由确定大小的子组件撑大，设置matchParent的孩子再匹配父组件大小；如果没有确定大小的孩子，容器和孩子大小均为0。
>
> - LayoutPolicy优先级低于constraintSize。

## TextContentControllerOptions<sup>15+</sup>

用于设置输入框插入字符时的配置选项。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型   | 只读 | 可选 | 说明       |
| --------- | ------ | ---- | ---- | ---------- |
| offset | number | 是   | 是   | 插入文本的位置。 |

## ScrollBarMargin<sup>20+</sup>对象说明

滚动条边距。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 类型                                                         | 只读 | 可选 | 说明                                   |
| ----- | ------------------------------------------------------------ | ---- | -- | -------------------------------------- |
| start | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否   | 是 | 滚动条起始边距。<br/>默认值：0，单位：vp |
| end   | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否   | 是 | 滚动条末尾边距。<br/>默认值：0，单位：vp |