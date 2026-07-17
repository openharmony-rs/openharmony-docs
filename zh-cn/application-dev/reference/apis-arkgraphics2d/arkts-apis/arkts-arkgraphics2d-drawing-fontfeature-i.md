# FontFeature

表示字体特征。字体特征是字体内置的排版规则，用于控制字形的显示效果，具体包括连字、替代字形、上下标等功能。

**起始版本：** 20

<!--Device-drawing-interface FontFeature--><!--Device-drawing-interface FontFeature-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## name

```TypeScript
name: string
```

字体特征的名称。常见的字体特征名称包含liga、frac、case等，需要对应的ttf文件支持才能生效。

**类型：** string

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontFeature-name: string--><!--Device-FontFeature-name: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## value

```TypeScript
value: number
```

字体特征的数值，浮点数。建议通过字体查看工具或查阅字体文档，确定具体的有效取值范围。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontFeature-value: double--><!--Device-FontFeature-value: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

