# TextGenerationModel（系统接口）

```TypeScript
export interface TextGenerationModel
```

AI文本模型抽象接口。

**起始版本：** 23

<!--Device-imageGeneration-export interface TextGenerationModel--><!--Device-imageGeneration-export interface TextGenerationModel-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## cancelTextGeneration

```TypeScript
cancelTextGeneration(sessionId: number): void
```

取消AI文本生成任务。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextGenerationModel-cancelTextGeneration(sessionId: int): void--><!--Device-TextGenerationModel-cancelTextGeneration(sessionId: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 取消AI文本生成任务的会话ID。<br>取值范围:[0, +∞] |

## onComplain

```TypeScript
onComplain(sessionId: number, request: string, result: GenerateTextTaskResult): void
```

用户使用投诉举报菜单来投诉AI生成文本任务的结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextGenerationModel-onComplain(sessionId: int, request: string, result: GenerateTextTaskResult): void--><!--Device-TextGenerationModel-onComplain(sessionId: int, request: string, result: GenerateTextTaskResult): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | AI文本生成任务的会话ID。<br>取值范围:[0, +∞] |
| request | string | 是 | AI生成文本任务的原始请求。 |
| result | [GenerateTextTaskResult](arkts-arkui-imagegeneration-generatetexttaskresult-i-sys.md) | 是 | AI生成文本任务的结果。 |

## requestTextGeneration

```TypeScript
requestTextGeneration(sessionId: number, value: string,
      callback: Callback<GenerateTextTaskPartialResult>): void
```

请求AI文本生成任务以获取生成的文本。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextGenerationModel-requestTextGeneration(sessionId: int, value: string,      callback: Callback<GenerateTextTaskPartialResult>): void--><!--Device-TextGenerationModel-requestTextGeneration(sessionId: int, value: string,      callback: Callback<GenerateTextTaskPartialResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 请求AI文本生成任务的会话ID。<br>取值范围:[0, +∞] |
| value | string | 是 | 请求AI文本生成任务的参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GenerateTextTaskPartialResult](arkts-arkui-imagegeneration-generatetexttaskpartialresult-i-sys.md)&gt; | 是 | 回调函数用于返回GenerateTextTaskPartialResult。 |
