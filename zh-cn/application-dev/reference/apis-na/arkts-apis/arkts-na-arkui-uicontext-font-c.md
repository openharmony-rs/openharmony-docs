# Font

class Font

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class Font--><!--Device-unnamed-export declare class Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getFontByName

```TypeScript
getFontByName(fontName: string): font.FontInfo
```

根据名称获取系统字体的详细信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-getFontByName(fontName: string): font.FontInfo--><!--Device-Font-getFontByName(fontName: string): font.FontInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontName | string | 是 | font name |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| font.FontInfo | Returns the font info |

## getSystemFontList

```TypeScript
getSystemFontList(): Array<string>
```

Gets a list of fonts supported by system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-getSystemFontList(): Array<string>--><!--Device-Font-getSystemFontList(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | A list of font names |

## registerFont

```TypeScript
registerFont(options: font.FontOptions): void
```

在字体管理器中注册自定义字体。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-registerFont(options: font.FontOptions): void--><!--Device-Font-registerFont(options: font.FontOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | font.FontOptions | 是 | FontOptions |

