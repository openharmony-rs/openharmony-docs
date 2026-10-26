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
```

## contentAutoPauseScenes

```TypeScript
contentAutoPauseScenes?: Array<AVScreenCaptureAutoPauseCaptureScene>
```

Sets the set of scenes that automatically pause screen content capture. When the capture session is running, if any of the scenarios in the scenario set occurs, the system automatically pauses the collection of screen content. You can use the OH_AVScreenCapture_ResumeScreenCapture() function to restore the data. image content acquisition is not automatically paused by default. Default value: If this parameter is not set. <br>You can use the OH_AVScreenCapture_ResumeScreenCapture() function to restore data.

**Type:** Array&lt;[AVScreenCaptureAutoPauseCaptureScene](arkts-media-media-avscreencaptureautopausecapturescene-e.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVScreenCaptureStrategy-contentAutoPauseScenes?: Array<AVScreenCaptureAutoPauseCaptureScene>--><!--Device-AVScreenCaptureStrategy-contentAutoPauseScenes?: Array<AVScreenCaptureAutoPauseCaptureScene>-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## enableAEC

```TypeScript
enableAEC?: boolean
```

Specifies whether to enable echo detection and echo cancellation when microphone capture is enabled. Default value: The default value is false, indicating that echo cancellation is disabled.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVScreenCaptureStrategy-enableAEC?: boolean--><!--Device-AVScreenCaptureStrategy-enableAEC?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

Indicates whether to enable B-frame encoding, which is used to reduce the size of the recorded file.

**Type:** boolean

**Since:** 20

<!--Device-AVScreenCaptureStrategy-enableBFrame?: boolean--><!--Device-AVScreenCaptureStrategy-enableBFrame?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## enableHDR

```TypeScript
enableHDR?: boolean
```

Sets whether to output videos in HDR vivid format. Default value: The default value is false, indicating that videos in SDR format are output.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVScreenCaptureStrategy-enableHDR?: boolean--><!--Device-AVScreenCaptureStrategy-enableHDR?: boolean-End-->

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
