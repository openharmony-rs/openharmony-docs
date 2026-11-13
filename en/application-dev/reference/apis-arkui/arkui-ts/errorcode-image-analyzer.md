# AI Image Analyzer Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f75d005fe5f7efe63120bf56956421fffe030023 translatedAt=2026-11-03T01:22:07.125Z pushedAt=2026-11-13T01:05:59.840Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../../errorcode-universal.md).

## 110001 AI Image Analysis Not Supported

**Error Message**

Image analysis feature is unsupported.

**Description**

This error code is reported when the developer calls [startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12) while the AI image analysis feature is not supported.

**Possible Causes**

The AI image analysis API ([startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)) that is not supported by the current device is called.

**Solution**

1. The AI image analysis feature depends on the device capability. Currently, there is no API for proactive query. You can determine whether the device supports the feature by catching error code 110001 when calling [startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12).
2. If the device does not support the feature, do not call [startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12), or guide the user to switch to a supported device.

## 110002 AI Image Analysis Already in Progress

**Error Message**

Image analysis is currently being executed.

**Description**

This error code is reported when the developer calls [startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12) while the previous analysis session has not yet finished.

**Possible Causes**

[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12) is called again before the AI image analysis is complete (the previous analysis has not returned a result).

**Solution**

1. Wait for the previous [startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12) analysis to complete (the result is returned through a Promise or callback) before initiating a new [startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12) call.
2. Avoid calling the same API repeatedly while the analysis is in progress.

## 110003 AI Image Analysis Terminated

**Error Message**

Image analysis is stopped.

**Description**

This error code is reported when the developer calls [stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12) while an AI image analysis is in progress (the Promise of startImageAnalyzer has not yet returned). The current analysis is stopped, and 110003 is thrown to the Promise to indicate that the analysis has been stopped.

**Possible Causes**

[stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12) is called while the AI image analysis is in progress (the Promise of startImageAnalyzer has not yet returned), which stops the current analysis and throws 110003 to the Promise of startImageAnalyzer.

**Solution**

1. Ensure that the [startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12) API has returned a result (that is, the previous analysis has returned a result through the Promise callback, whether successful or failed) before calling the [stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12) API.
2. Check the API call sequence to avoid calling the stop API before the analysis is complete.
