# ImageGenerationModel（系统接口）

```TypeScript
interface ImageGenerationModel
```

AI图像模型抽象接口。

**起始版本：** 23

<!--Device-imageGeneration-interface ImageGenerationModel--><!--Device-imageGeneration-interface ImageGenerationModel-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## cancelImageGeneration

```TypeScript
cancelImageGeneration(sessionId: number): void
```

取消AI图像生成任务。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageGenerationModel-cancelImageGeneration(sessionId: int): void--><!--Device-ImageGenerationModel-cancelImageGeneration(sessionId: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 请求AI图像生成任务的会话ID。<br>取值范围: [0, +∞] |

## getModelSupportStyles

```TypeScript
getModelSupportStyles(): Array<ImageStyle>
```

获取AI模型支持的图像风格类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageGenerationModel-getModelSupportStyles(): Array<ImageStyle>--><!--Device-ImageGenerationModel-getModelSupportStyles(): Array<ImageStyle>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ImageStyle](arkts-arkui-imagegeneration-imagestyle-i-sys.md)&gt; | 图片风格信息 |

## onComplain

```TypeScript
onComplain(sessionId: number, request: GenerateImageTaskParams, result: GenerateImageTaskResult): void
```

用户使用投诉举报菜单来投诉AI生成图像任务的结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageGenerationModel-onComplain(sessionId: int, request: GenerateImageTaskParams, result: GenerateImageTaskResult): void--><!--Device-ImageGenerationModel-onComplain(sessionId: int, request: GenerateImageTaskParams, result: GenerateImageTaskResult): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 请求AI图像生成任务的会话ID。<br>取值范围: [0, +∞] |
| request | [GenerateImageTaskParams](arkts-arkui-imagegeneration-generateimagetaskparams-i-sys.md) | 是 | AI生成图像任务的原始请求。 |
| result | [GenerateImageTaskResult](arkts-arkui-imagegeneration-generateimagetaskresult-i-sys.md) | 是 | AI生成图像任务的结果。 |

## requestImageGeneration

```TypeScript
requestImageGeneration(sessionId: number, params: GenerateImageTaskParams,
      callback: Callback<GenerateImageTaskPartialResult>): void
```

请求AI图像生成任务以获取生成的图像。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageGenerationModel-requestImageGeneration(sessionId: int, params: GenerateImageTaskParams,      callback: Callback<GenerateImageTaskPartialResult>): void--><!--Device-ImageGenerationModel-requestImageGeneration(sessionId: int, params: GenerateImageTaskParams,      callback: Callback<GenerateImageTaskPartialResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 请求AI图像生成任务的会话ID。<br>取值范围:[0, +∞] |
| params | [GenerateImageTaskParams](arkts-arkui-imagegeneration-generateimagetaskparams-i-sys.md) | 是 | 请求AI图像生成任务的参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GenerateImageTaskPartialResult](arkts-arkui-imagegeneration-generateimagetaskpartialresult-i-sys.md)&gt; | 是 | 回调函数用于返回 GenerateImageTaskPartialResult。 |
