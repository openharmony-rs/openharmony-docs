# TextLayoutResult

文本布局结果。

**起始版本：** 24

<!--Device-text-interface TextLayoutResult--><!--Device-text-interface TextLayoutResult-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## correctRect

```TypeScript
correctRect: TextRectSize
```

布局后段落的矩形尺寸。

**类型：** TextRectSize

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TextLayoutResult-correctRect: TextRectSize--><!--Device-TextLayoutResult-correctRect: TextRectSize-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fitStrRange

```TypeScript
fitStrRange: Array<Range>
```

文本布局计算完成后能够完整显示的字符范围数组。

**类型：** Array<Range>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TextLayoutResult-fitStrRange: Array<Range>--><!--Device-TextLayoutResult-fitStrRange: Array<Range>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

