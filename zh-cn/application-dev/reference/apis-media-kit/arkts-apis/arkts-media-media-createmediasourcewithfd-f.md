# createMediaSourceWithFd

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

<a id="createmediasourcewithfd"></a>
## createMediaSourceWithFd

```TypeScript
function createMediaSourceWithFd(fdSrc: AVFileDescriptor): MediaSource | undefined
```

通过文件描述符创建媒体源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-media-function createMediaSourceWithFd(fdSrc: AVFileDescriptor): MediaSource | undefined--><!--Device-media-function createMediaSourceWithFd(fdSrc: AVFileDescriptor): MediaSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fdSrc | [AVFileDescriptor](arkts-media-multimedia-media-avfiledescriptor-i.md) | 是 | 媒体文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaSource](arkts-media-multimedia-media-mediasource-i.md) | 返回MediaSource，用于媒体资源设置。 |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';

let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fdSrc = await context.resourceManager.getRawFd('xxx.mp4');
let mediaSource : media.MediaSource | undefined = media.createMediaSourceWithFd(fdSrc);

```

