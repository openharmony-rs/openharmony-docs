# TextContentControllerBase

TextContentControllerBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare abstract class TextContentControllerBase--><!--Device-unnamed-export declare abstract class TextContentControllerBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getText

```TypeScript
getText(range?: TextRange): string | undefined
```

Gets the text content of the selected range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextContentControllerBase-getText(range?: TextRange): string | undefined--><!--Device-TextContentControllerBase-getText(range?: TextRange): string | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](../../apis-arkui/arkts-apis/arkts-arkui-textcommon-textrange-i.md) | 否 | selected range. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | text content of the selected range. |

