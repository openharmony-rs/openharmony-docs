# AVScreenCaptureStrategy

```TypeScript
interface AVScreenCaptureStrategy
```

Provides the media AVScreenCaptureStrategy definition.

**Since:** 20

<!--Device-media-interface AVScreenCaptureStrategy--><!--Device-media-interface AVScreenCaptureStrategy-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

Indicates whether to enable B-frame encoding, which is used to reduce the size of the recorded file.

**Type:** boolean

**Since:** 20

<!--Device-AVScreenCaptureStrategy-enableBFrame?: boolean--><!--Device-AVScreenCaptureStrategy-enableBFrame?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## enablePause

```TypeScript
enablePause?: boolean
```

Enable pausing the screen capture. The default value is false.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVScreenCaptureStrategy-enablePause?: boolean--><!--Device-AVScreenCaptureStrategy-enablePause?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## keepCaptureDuringCall

```TypeScript
keepCaptureDuringCall?: boolean
```

Allows starting or maintaining screen capture during a call

**Type:** boolean

**Default:** {false} [Required if provided]

**Since:** 20

<!--Device-AVScreenCaptureStrategy-keepCaptureDuringCall?: boolean--><!--Device-AVScreenCaptureStrategy-keepCaptureDuringCall?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## privacyMaskMode

```TypeScript
privacyMaskMode?: number
```

Set the fill mode for screen capture when a privacy window exists.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVScreenCaptureStrategy-privacyMaskMode?: int--><!--Device-AVScreenCaptureStrategy-privacyMaskMode?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture
