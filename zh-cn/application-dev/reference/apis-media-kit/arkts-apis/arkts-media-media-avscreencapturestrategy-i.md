# AVScreenCaptureStrategy

录屏策略。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

录屏是否使能B帧编码。true表示录屏文件使能B帧编码，false表示录屏文件禁用B帧编码，默认是false。 B帧视频编码相关的约束和限制可以参考文档B帧视频编码约束和限制。如果当前不符合B帧视频编码的约束和限制，则正常录制不含B帧的视频，不会返回错误。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## enablePause

```TypeScript
enablePause?: boolean
```

表示录屏过程中是否允许暂停录屏。true表示允许，false表示不允许。默认是false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## keepCaptureDuringCall

```TypeScript
keepCaptureDuringCall?: boolean
```

蜂窝通话时是否保持录屏。true表示蜂窝通话时保持录屏，false表示蜂窝通话时不进行录屏，默认为false。

**类型：** boolean

**默认值：** {false} [Required if provided]

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## privacyMaskMode

```TypeScript
privacyMaskMode?: number
```

设置屏幕录制时对隐私窗口的屏蔽模式。

- 0：表示存在隐私窗口时，采用全屏屏蔽模式，默认是0。

- 1：表示存在隐私窗口时，采用隐私窗口屏蔽模式。

- 设置为其他值时返回错误。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture
