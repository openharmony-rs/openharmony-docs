# getFontByName

## getFontByName

```TypeScript
function getFontByName(fontName: string): FontInfo
```

根据传入的系统字体名称获取系统字体的相关信息。

> **说明：**
>
> -getFontByName需要先通过[UIContext](arkts-arkui-uicontext.md)中的
> [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取
> [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用getFontByName可能导致
> [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
>
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的
> [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的
> [Font](arkts-arkui-uicontext.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getFontByName

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontName | string | 是 | 系统的字体名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FontInfo | 字体的详细信息。 |

