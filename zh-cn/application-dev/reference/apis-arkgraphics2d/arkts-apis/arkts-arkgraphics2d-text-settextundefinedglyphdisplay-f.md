# setTextUndefinedGlyphDisplay

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## setTextUndefinedGlyphDisplay

```TypeScript
function setTextUndefinedGlyphDisplay(noGlyphShow: TextUndefinedGlyphDisplay): void
```

设置字符映射到.notdef（未定义）字形时要使用的字形类型。

影响此调用后呈现的所有文本。

此配置会影响显示字体中未定义字符的方式：

- 默认行为遵循字体的内部.notdef字形设计。  
- 开启后将强制使缺失字形的字符以豆腐块形式显示。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-text-function setTextUndefinedGlyphDisplay(noGlyphShow: TextUndefinedGlyphDisplay): void--><!--Device-text-function setTextUndefinedGlyphDisplay(noGlyphShow: TextUndefinedGlyphDisplay): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| noGlyphShow | [TextUndefinedGlyphDisplay](arkts-arkgraphics2d-text-textundefinedglyphdisplay-e.md) | 是 | 无法塑形字符的显示方式。 |

**示例：**

```TypeScript
text.setTextUndefinedGlyphDisplay(text.TextUndefinedGlyphDisplay.USE_TOFU)

```

