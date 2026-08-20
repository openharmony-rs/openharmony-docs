# @ohos.multimedia.videoProcessing (视频处理)

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhuyicheng666-->
<!--Designer: @gongzheng92-->
<!--Tester: @gongzheng92-->
<!--Adviser: @w_Machine_cc-->

本模块提供视频质量处理能力，目前支持视频AI-HDR增强相关功能。

本模块包含一个基础类：[VideoProcessor](#videoprocessor)类。

> **说明：**
>
> - 本模块仅支持在Stage模型下使用。
> - 本模块首批接口从API version 26.0.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { videoProcessing } from '@kit.MediaKit';
```

## videoProcessing.createVideoProcessor

createVideoProcessor(): VideoProcessor

创建视频处理实例。如果操作成功，返回VideoProcessor实例，否则返回null。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**返回值：**

|  类型 | 说明  |
| ------------ | ------------ |
|  [VideoProcessor](#videoprocessor) | 视频处理实例。如果操作成功，返回VideoProcessor实例，否则返回null |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[视频处理引擎错误码](../apis-image-kit/errorcode-videoprocessingengine.md)。

| 错误码ID  | 错误信息  |
| :------------ | :------------ |
| 801  | Capability not supported. Function createVideoProcessor can not work correctly due to limited device capabilities.|
| 29200003  | Failed to create video processing instance. For example, the number of instances exceeds the upper limit. |
| 29200007  | Out of memory.  |

**示例：**

```ts
import { videoProcessing } from '@kit.MediaKit';

function createVideoProcessor() {
  let videoProcessor = videoProcessing.createVideoProcessor();
}
```

## VideoProcessor

视频处理类，提供视频质量处理相关功能，目前支持AI-HDR增强能力。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

### getStatus

getStatus(): Promise\<VideoProcessorStatus | undefined\>

获取视频处理器功能的当前状态。使用Promise异步回调。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**返回值：**

|  类型 | 说明  |
| ------------ | ------------ |
| Promise\<[VideoProcessorStatus](#videoprocessorstatus) \| undefined\>  |  Promise对象。返回VideoProcessorStatus，若获取失败则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息  |
| :------------ | :------------ |
| 801  | Capability not supported. |

**示例：**

```ts
import { videoProcessing } from '@kit.MediaKit';

async function getStatus() {
  let videoProcessor = videoProcessing.createVideoProcessor();
  let status = await videoProcessor.getStatus();
  if (status !== undefined && status.aiHdr !== undefined) {
    console.info('AIHDR enabled: ' + status.aiHdr.enabled);
  }
}
```

### onStatusChange

onStatusChange(callback: VideoProcessorStatusCallback): void

注册视频处理器状态变更的监听。使用callback异步回调。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

|  参数名 | 类型  | 必填  | 说明  |
| :------------ | :------------ | :------------ | :------------ |
|  callback | [VideoProcessorStatusCallback](#videoprocessorstatuscallback)  | 是  | 状态发生变化时触发的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[视频处理引擎错误码](../apis-image-kit/errorcode-videoprocessingengine.md)。

| 错误码ID  | 错误信息  |
| :------------ | :------------ |
| 801  | Capability not supported. |
| 29200007  | Out of memory.  |
| 29200009  | Input value is invalid.  |

**示例：**

```ts
import { videoProcessing } from '@kit.MediaKit';

function onStatusChange() {
  let videoProcessor = videoProcessing.createVideoProcessor();
  videoProcessor.onStatusChange((status: videoProcessing.VideoProcessorStatus) => {
    if (status !== undefined && status.aiHdr !== undefined) {
      console.info('AIHDR status changed, enabled: ' + status.aiHdr.enabled);
	}
  });
}
```

### offStatusChange

offStatusChange(callback?: VideoProcessorStatusCallback): void

注销视频处理器状态变更的监听。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

|  参数名 | 类型  | 必填  | 说明  |
| :------------ | :------------ | :------------ | :------------ |
|  callback | [VideoProcessorStatusCallback](#videoprocessorstatuscallback)  | 否  | 需要移除的回调函数。若不传入该参数，将移除该事件类型的所有回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[视频处理引擎错误码](../apis-image-kit/errorcode-videoprocessingengine.md)。

| 错误码ID  | 错误信息  |
| :------------ | :------------ |
| 801  | Capability not supported. |
| 29200006  | The operation is not permitted. This may be caused by incorrect status.  |
| 29200009  | Input value is invalid.  |

**示例：**

```ts
import { videoProcessing } from '@kit.MediaKit';

function offStatusChange() {
  let videoProcessor = videoProcessing.createVideoProcessor();
  videoProcessor.offStatusChange();
}
```

## VideoProcessorStatus

interface VideoProcessorStatus

视频处理器的统一状态。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

| 名称  | 类型  | 只读  | 可选  | 说明  |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| aiHdr | [VideoProcessorAiHdrStatus](#videoprocessoraihdrstatus) | 否  | 是  | AI-HDR增强状态。 |

## VideoProcessorAiHdrStatus

interface VideoProcessorAiHdrStatus

AI-HDR增强功能的状态。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

| 名称  | 类型  | 只读  | 可选  | 说明  |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| enabled | boolean | 否  | 是  | AI-HDR增强功能是否已开启。<br>true表示AI-HDR增强功能已开启，false表示AI-HDR增强功能未开启。 |

## VideoProcessorStatusCallback

type VideoProcessorStatusCallback = (status: VideoProcessorStatus) => void

视频处理器状态变更的回调类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ------ | ---------------------------------------------------------- |
| status | [VideoProcessorStatus](#videoprocessorstatus) | 是 | 变更后的视频处理器状态。 |

