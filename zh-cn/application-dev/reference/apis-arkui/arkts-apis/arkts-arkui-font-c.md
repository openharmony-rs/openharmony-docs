# Font

class Font

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getFontByName

```TypeScript
getFontByName(fontName: string): font.FontInfo
```

根据字体名称获取字体详细信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontName | string | 是 | 字体名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| font.FontInfo | Returns the font info |

## getSystemFontList

```TypeScript
getSystemFontList(): Array<string>
```

获取系统支持的字体列表。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 字体名称列表 |

## registerFont

```TypeScript
registerFont(options: font.FontOptions): void
```

Register a customized font in the FontManager.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | font.FontOptions | 是 | FontOptions |

