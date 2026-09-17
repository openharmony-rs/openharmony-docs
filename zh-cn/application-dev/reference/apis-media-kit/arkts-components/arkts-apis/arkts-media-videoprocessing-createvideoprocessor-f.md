# createVideoProcessor

## 导入模块

```TypeScript
import { videoProcessing } from '@kit.MediaKit';
```

## createVideoProcessor

```TypeScript
function createVideoProcessor(): VideoProcessor
```

创建视频处理实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VideoProcessor](arkts-media-videoprocessing-videoprocessor-i.md) | 操作成功时返回VideoProcessor实例，否则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。由于设备能力受限，createVideoProcessor函数无法正常工作。 |
| [29200003](../../apis-image-kit/errorcode-videoprocessingengine.md#29200003-创建失败) | 创建视频处理实例失败。例如，实例数量超过上限。 |
| [29200007](../../apis-image-kit/errorcode-videoprocessingengine.md#29200007-内存不足) | 内存不足。 |
