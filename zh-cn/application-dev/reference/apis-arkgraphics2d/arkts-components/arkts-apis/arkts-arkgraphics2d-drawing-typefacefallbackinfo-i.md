# TypefaceFallbackInfo

```TypeScript
interface TypefaceFallbackInfo
```

定义字体回退信息结构体，表示一组使用相同回退字体的字形片段。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## glyphIds

```TypeScript
glyphIds: Array<number>
```

该字形片段的字形ID数组。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

## typeface

```TypeScript
typeface: Typeface
```

该字形片段匹配到的字体对象。

**类型：** [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing
