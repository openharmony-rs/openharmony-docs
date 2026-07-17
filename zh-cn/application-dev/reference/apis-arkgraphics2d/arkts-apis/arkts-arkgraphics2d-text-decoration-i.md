# Decoration

文本装饰线。

**起始版本：** 12

<!--Device-text-interface Decoration--><!--Device-text-interface Decoration-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## color

```TypeScript
color?: common2D.Color
```

装饰线颜色，默认为跟随文本颜色。

**类型：** common2D.Color

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Decoration-color?: common2D.Color--><!--Device-Decoration-color?: common2D.Color-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## decorationStyle

```TypeScript
decorationStyle?: TextDecorationStyle
```

装饰线样式，默认为SOLID。

**类型：** TextDecorationStyle

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Decoration-decorationStyle?: TextDecorationStyle--><!--Device-Decoration-decorationStyle?: TextDecorationStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## decorationThicknessScale

```TypeScript
decorationThicknessScale?: number
```

装饰线粗细系数，浮点数，默认为1.0。如果设置的值小于等于0，则不会绘制装饰线。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Decoration-decorationThicknessScale?: double--><!--Device-Decoration-decorationThicknessScale?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## textDecoration

```TypeScript
textDecoration?: TextDecorationType
```

装饰线类型，默认为NONE。

**类型：** TextDecorationType

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Decoration-textDecoration?: TextDecorationType--><!--Device-Decoration-textDecoration?: TextDecorationType-End-->

**系统能力：** SystemCapability.Graphics.Drawing

