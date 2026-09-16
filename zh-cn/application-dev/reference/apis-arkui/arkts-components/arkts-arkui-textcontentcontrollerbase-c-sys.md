# TextContentControllerBase

TextInput、TextArea、Search的基础控制器。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getText

```TypeScript
getText(range?: TextRange): string
```

获取指定范围的文本内容。可用于以下场景：  
- 文本编辑器中获取用户选中的文本内容进行处理。  
- 内容校验时获取特定范围的文本进行检查。  
- 文本处理应用中提取部分文本内容进行分析或转换。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | 否 | 获取文本的范围，包括需要获取文本的起始位置和终止位置。<br>未指定范围时，默认将获取全部文本。未指定获取文本的起始位置，则默认从下标0开始；未指定获取文本的终止位置，则默认以文本末尾作为结束点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定范围内的文本内容字符串。当指定的起始位置大于终止位置时，返回空字符串。 |
