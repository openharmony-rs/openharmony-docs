# DeferredVideoEnhancementInfo（系统接口）

```TypeScript
interface DeferredVideoEnhancementInfo
```

延迟视频增强信息。

**起始版本：** 13

<!--Device-camera-interface DeferredVideoEnhancementInfo--><!--Device-camera-interface DeferredVideoEnhancementInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isDeferredVideoEnhancementAvailable

```TypeScript
readonly isDeferredVideoEnhancementAvailable: boolean
```

判断是否支持延迟视频增强。

**类型：** boolean

**起始版本：** 13

<!--Device-DeferredVideoEnhancementInfo-readonly isDeferredVideoEnhancementAvailable: boolean--><!--Device-DeferredVideoEnhancementInfo-readonly isDeferredVideoEnhancementAvailable: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## videoId

```TypeScript
readonly videoId?: string
```

视频标识符。

**类型：** string

**起始版本：** 13

<!--Device-DeferredVideoEnhancementInfo-readonly videoId?: string--><!--Device-DeferredVideoEnhancementInfo-readonly videoId?: string-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
