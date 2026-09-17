# deinitializeEnvironment

## 导入模块

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';
```

## deinitializeEnvironment

```TypeScript
function deinitializeEnvironment(): Promise<void>
```

反初始化图像处理的全局环境。

**起始版本：** 18

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，用于返回操作结果。操作失败时返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [29200006](../errorcode-videoprocessingengine.md#29200006-不被允许的操作) | 不允许执行该操作，可能是由于当前状态不正确。 |

**示例**

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';

async function deinitializeEnvironment() {
  await videoProcessingEngine.initializeEnvironment();
  await videoProcessingEngine.deinitializeEnvironment();
}
```
