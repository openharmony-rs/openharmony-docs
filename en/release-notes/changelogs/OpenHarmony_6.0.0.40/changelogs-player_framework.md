# Player Framework Changelogs

## cl.multimedia.1 OH_AVScreenCapture_SetCaptureStrategy in Media Kit Changed

**Access Level**

Public API

**Reason for the Change**

To optimize the developer experience, the error code description is corrected. After starting screen capture, calling this API previously returned the error code **AV_SCREEN_CAPTURE_ERR_UNSUPPORT**, which was inaccurate. To improve the developer experience, the error code description has been corrected.

**Impact of the Change**

Before change: After starting screen capture, calling **OH_AVScreenCapture_SetCaptureStrategy** returned error code **AV_SCREEN_CAPTURE_ERR_UNSUPPORT**.

After change: After starting screen capture, calling **OH_AVScreenCapture_SetCaptureStrategy** now returns error code **AV_SCREEN_CAPTURE_ERR_INVALID_STATE**.

**Start API Level**

API 20

**Change Since**

OpenHarmony SDK 6.0.0.40

**Key API/Component Changes**

native_avscreen_capture.h:

OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)

**Adaptation Guide**

If your application performs precise error handling based on the return value of **OH_AVScreenCapture_SetCaptureStrategy**, update your code to handle **AV_SCREEN_CAPTURE_ERR_INVALID_STATE** instead of AV_SCREEN_CAPTURE_ERR_UNSUPPORT.
