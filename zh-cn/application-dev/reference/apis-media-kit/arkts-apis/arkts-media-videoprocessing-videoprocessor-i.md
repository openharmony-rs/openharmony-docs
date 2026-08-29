# VideoProcessor

提供VideoProcessor类型，包括AIHDR相关功能。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

## 导入模块

```TypeScript
import { videoProcessing } from '@kit.MediaKit';
```

## getStatus

```TypeScript
getStatus(): Promise<VideoProcessorStatus | undefined>
```

获取当前视频处理功能的状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[VideoProcessorStatus](arkts-media-videoprocessing-videoprocessorstatus-i.md) \| undefined&gt; | Promise对象，用于返回VideoProcessorStatus；如果无法获取状态，则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。 |

## offStatusChange

```TypeScript
offStatusChange(callback?: VideoProcessorStatusCallback): void
```

取消注册视频处理功能状态变化的监听回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VideoProcessorStatusCallback](arkts-media-videoprocessing-videoprocessorstatuscallback-t.md) | 否 | 需要取消注册的回调函数。 参数不填时，默认取消该事件类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。 |
| [29200006](../../apis-image-kit/errorcode-videoprocessingengine.md#29200006-不被允许的操作) | 不允许执行该操作，可能是由于当前状态不正确。 |
| [29200009](../../apis-image-kit/errorcode-videoprocessingengine.md#29200009-值无效) | 输入参数无效。 |

## onStatusChange

```TypeScript
onStatusChange(callback: VideoProcessorStatusCallback): void
```

注册视频处理功能状态变化的监听回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VideoProcessorStatusCallback](arkts-media-videoprocessing-videoprocessorstatuscallback-t.md) | 是 | 视频处理功能状态发生变化时触发的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。 |
| [29200007](../../apis-image-kit/errorcode-videoprocessingengine.md#29200007-内存不足) | 内存不足。 |
| [29200009](../../apis-image-kit/errorcode-videoprocessingengine.md#29200009-值无效) | 输入值无效。 |
