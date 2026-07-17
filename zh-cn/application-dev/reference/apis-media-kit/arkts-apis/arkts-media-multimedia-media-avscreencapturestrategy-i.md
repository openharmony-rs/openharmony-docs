# AVScreenCaptureStrategy

Provides the media AVScreenCaptureStrategy definition.

**起始版本：** 20

<!--Device-unnamed-interface AVScreenCaptureStrategy--><!--Device-unnamed-interface AVScreenCaptureStrategy-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

Indicates whether to enable B-frame encoding, which is used to reduce the size of the recorded file.

**类型：** boolean

**起始版本：** 20

<!--Device-AVScreenCaptureStrategy-enableBFrame?: boolean--><!--Device-AVScreenCaptureStrategy-enableBFrame?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## enablePause

```TypeScript
enablePause?: boolean
```

Enable pausing the screen capture. The default value is false.

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVScreenCaptureStrategy-enablePause?: boolean--><!--Device-AVScreenCaptureStrategy-enablePause?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## keepCaptureDuringCall

```TypeScript
keepCaptureDuringCall?: boolean
```

Allows starting or maintaining screen capture during a call

**类型：** boolean

**默认值：** {false} [Required if provided]

**起始版本：** 20

<!--Device-AVScreenCaptureStrategy-keepCaptureDuringCall?: boolean--><!--Device-AVScreenCaptureStrategy-keepCaptureDuringCall?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## privacyMaskMode

```TypeScript
privacyMaskMode?: number
```

Set the fill mode for screen capture when a privacy window exists.

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVScreenCaptureStrategy-privacyMaskMode?: int--><!--Device-AVScreenCaptureStrategy-privacyMaskMode?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

