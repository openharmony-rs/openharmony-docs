# AVScreenCaptureStrategy

```TypeScript
interface AVScreenCaptureStrategy
```

录屏策略。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableDeviceLevelCapture

```TypeScript
enableDeviceLevelCapture?: boolean
```

用于指定折叠屏PC在折叠状态下录制半块屏幕还是整块屏幕。true表示折叠屏PC在折叠状态下录制整块屏幕，false表示折叠屏PC在折叠状态下录制半块屏幕。

**类型：** boolean

**默认值：** false

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。
