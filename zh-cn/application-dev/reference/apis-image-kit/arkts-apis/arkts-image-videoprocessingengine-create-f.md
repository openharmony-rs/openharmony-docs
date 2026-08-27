# create

## 导入模块

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';
```

## create

```TypeScript
function create(): ImageProcessor
```

创建图像处理实例。

**起始版本：** 18

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageProcessor](arkts-image-videoprocessingengine-imageprocessor-i.md) | 操作成功时返回ImageProcessor实例，否则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。由于设备能力受限，create函数无法正常工作。 |
| [29200003](../errorcode-videoprocessingengine.md#29200003-创建失败) | 创建图像处理实例失败。例如，实例数量超过上限。 |
| [29200007](../errorcode-videoprocessingengine.md#29200007-内存不足) | 内存不足。 |

**示例**

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';

async function create() {
  await videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
}
```
