# Color Space Configuration Issues

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4108f57585ad860302bfbcb224bfa340102941c1 translatedAt=2026-08-22T02:07:07.416Z pushedAt=2026-08-22T06:46:25.608Z -->

## Symptom

When an application is in a post-processing or video encoding scenario, the processed images or videos may exhibit abnormal effects such as color cast and overexposure.

## Cause Analysis

When processing preview stream data or video recording stream data, you must handle the color space correctly. Otherwise, the processed data may exhibit abnormal effects such as color cast and overexposure. The specific causes are as follows:

1. The application does not actively set the color space, so the SDR color space is used by default, but the HDR format is used when configuring the camera output stream.

2. The application actively sets the color space, but uses a format that does not match the current color space when configuring the camera output stream data.

## Solution

1. Call [getActiveColorSpace](../../reference/apis-camera-kit/arkts-apis-camera-ColorManagement.md#getactivecolorspace12) (ArkTS) or [OH_CaptureSession_GetActiveColorSpace](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_getactivecolorspace) (C/C++) to query the color space currently in effect for the camera session, and configure the correct color space information when processing the camera output stream data.

2. Based on the queried colorSpace information, the camera application can configure the corresponding color space parameters through the setColorSpace-related APIs.

   - ImageReceiver scenario (ArkTS): If you use [ImageReceiver to receive images](../image/image-receiver.md), first convert the [Image](../../reference/apis-image-kit/arkts-apis-image-Image.md) data returned by the underlying layer through the imageArrival event listener into a [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md) for image data processing or display. After creating the [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md), you can set the color space property of the image through [setColorSpace](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md#setcolorspace10).

   - NativeWindow scenario (C/C++): If you use [NativeWindow](../../reference/apis-arkgraphics2d/capi-nativewindow.md) to copy the preview stream or video recording stream data obtained from the camera, to avoid losing the color space property during data copying, you can first obtain the OHNativeWindow color space property through [OH_NativeWindow_GetColorSpace](../../reference/apis-arkgraphics2d/capi-external-window-h.md#oh_nativewindow_getcolorspace), and then set the NativeWindow color space property through [OH_NativeWindow_SetColorSpace](../../reference/apis-arkgraphics2d/capi-external-window-h.md#oh_nativewindow_setcolorspace).