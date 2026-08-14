# TextContentControllerBase

TextContentControllerBase

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare abstract class TextContentControllerBase--><!--Device-unnamed-declare abstract class TextContentControllerBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getText

```TypeScript
getText(range?: TextRange): string
```

Gets the text content of the selected range.

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-TextContentControllerBase-getText(range?: TextRange): string--><!--Device-TextContentControllerBase-getText(range?: TextRange): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | TextRange | 否 | selected range. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | text content of the selected range. |

