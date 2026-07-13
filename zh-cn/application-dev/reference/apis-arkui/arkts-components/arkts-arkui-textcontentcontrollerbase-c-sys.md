# TextContentControllerBase

TextContentControllerBase

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getText

```TypeScript
getText(range?: TextRange): string
```

Gets the text content of the selected range.

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

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

