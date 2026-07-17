# TextBlobRunBuffer

描述一行文字中具有相同属性的连续字形。

**起始版本：** 11

<!--Device-drawing-interface TextBlobRunBuffer--><!--Device-drawing-interface TextBlobRunBuffer-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## glyph

```TypeScript
glyph: number
```

存储文字的索引，该参数为整数，传入浮点类型时向下取整。

**类型：** number

**起始版本：** 11

<!--Device-TextBlobRunBuffer-glyph: int--><!--Device-TextBlobRunBuffer-glyph: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## positionX

```TypeScript
positionX: number
```

文本的起点x轴坐标，该参数为浮点数。

**类型：** number

**起始版本：** 11

<!--Device-TextBlobRunBuffer-positionX: double--><!--Device-TextBlobRunBuffer-positionX: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## positionY

```TypeScript
positionY: number
```

文本的起点y轴坐标，该参数为浮点数。

**类型：** number

**起始版本：** 11

<!--Device-TextBlobRunBuffer-positionY: double--><!--Device-TextBlobRunBuffer-positionY: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

