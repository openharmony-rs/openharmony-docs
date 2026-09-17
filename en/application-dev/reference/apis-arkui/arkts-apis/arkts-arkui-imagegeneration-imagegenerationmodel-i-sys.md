# ImageGenerationModel (System API)

AI Image Model Abstract Interface.

@interface ImageGenerationModel

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## cancelImageGeneration

```TypeScript
cancelImageGeneration(sessionId: number): void
```

Cancel AI image generation task.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | The session id for cancel an AI image generation task.<br>Value: range: [0, +∞] |

## getModelSupportStyles

```TypeScript
getModelSupportStyles(): Array<ImageStyle>
```

Get the types of image styles supported by the AI model.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[ImageStyle](arkts-arkui-imagegeneration-imagestyle-i-sys.md)&gt; | image style information. |

## onComplain

```TypeScript
onComplain(sessionId: number, request: GenerateImageTaskParams, result: GenerateImageTaskResult): void
```

User use complaint menu to complain the result of an AI-generated image task.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | The session id of AI image generation task.<br>Value: range: [0, +∞] |
| request | [GenerateImageTaskParams](arkts-arkui-imagegeneration-generateimagetaskparams-i-sys.md) | Yes | The origin request for AI-generated image task. |
| result | [GenerateImageTaskResult](arkts-arkui-imagegeneration-generateimagetaskresult-i-sys.md) | Yes | The result for AI-generated image task. |

## requestImageGeneration

```TypeScript
requestImageGeneration(sessionId: number, params: GenerateImageTaskParams,
      callback: Callback<GenerateImageTaskPartialResult>): void
```

Request AI image generation task to get the generated image.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | The session id for requesting an AI image generation task.<br>Value: range:[0, +∞] |
| params | [GenerateImageTaskParams](arkts-arkui-imagegeneration-generateimagetaskparams-i-sys.md) | Yes | Parameters for requesting an AI image generation task. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GenerateImageTaskPartialResult](arkts-arkui-imagegeneration-generateimagetaskpartialresult-i-sys.md)&gt; | Yes | the callback used to return the GenerateImageTaskPartialResult. |
