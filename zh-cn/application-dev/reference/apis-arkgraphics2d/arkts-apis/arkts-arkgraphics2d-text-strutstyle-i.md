# StrutStyle

支柱样式，用于控制绘制文本的行间距、基线对齐方式以及其他与行高相关的属性，默认不开启。

**起始版本：** 12

<!--Device-text-interface StrutStyle--><!--Device-text-interface StrutStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## enabled

```TypeScript
enabled?: boolean
```

是否启用支柱样式，true表示使用，false表示不使用，默认为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-enabled?: boolean--><!--Device-StrutStyle-enabled?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontFamilies

```TypeScript
fontFamilies?: Array<string>
```

字体家族名称列表，默认为空，匹配系统字体。

**类型：** Array<string>

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-fontFamilies?: Array<string>--><!--Device-StrutStyle-fontFamilies?: Array<string>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontSize

```TypeScript
fontSize?: number
```

字体大小，浮点数，默认为14.0，单位为物理像素px。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-fontSize?: double--><!--Device-StrutStyle-fontSize?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

字体样式，默认为常规样式。

**类型：** FontStyle

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-fontStyle?: FontStyle--><!--Device-StrutStyle-fontStyle?: FontStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontWeight

```TypeScript
fontWeight?: FontWeight
```

字重，默认为W400。系统默认字体支持字重调节，其他字体设置字重值小于W600时无变化，大于等于W600时可能触发伪加粗效果。

**类型：** FontWeight

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-fontWeight?: FontWeight--><!--Device-StrutStyle-fontWeight?: FontWeight-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontWidth

```TypeScript
fontWidth?: FontWidth
```

字体宽度，默认为NORMAL。

**类型：** FontWidth

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-fontWidth?: FontWidth--><!--Device-StrutStyle-fontWidth?: FontWidth-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## forceHeight

```TypeScript
forceHeight?: boolean
```

是否所有行都将使用支柱的高度，true表示使用，false表示不使用，默认为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-forceHeight?: boolean--><!--Device-StrutStyle-forceHeight?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## halfLeading

```TypeScript
halfLeading?: boolean
```

true表示将行间距平分至行的顶部与底部，false则不平分，默认为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-halfLeading?: boolean--><!--Device-StrutStyle-halfLeading?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## height

```TypeScript
height?: number
```

行高缩放倍数，浮点数，默认为1.0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-height?: double--><!--Device-StrutStyle-height?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## heightOverride

```TypeScript
heightOverride?: boolean
```

是否覆盖高度，true表示覆盖，false表示不覆盖，默认为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-heightOverride?: boolean--><!--Device-StrutStyle-heightOverride?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## leading

```TypeScript
leading?: number
```

自定义应用于支柱的行距，浮点数，单位为物理像素px，默认为-1.0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-StrutStyle-leading?: double--><!--Device-StrutStyle-leading?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

