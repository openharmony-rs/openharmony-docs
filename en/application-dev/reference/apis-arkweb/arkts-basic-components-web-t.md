# Types

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-07T04:38:06.134Z pushedAt=2026-08-07T08:12:34.499Z -->

This document provides the type definitions used in the ArkWeb component, including the Web controller and various event callback function types. The WebviewController is used to control the behavior of the Web component, and the callback function types provide developers with the ability to listen for and handle various event scenarios during the running of the Web component.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual device.

## WebviewController<sup>9+</sup>

type WebviewController = import('../api/@ohos.web.webview').default.WebviewController

Defines methods for the web controller.

**System capability**: SystemCapability.Web.Webview.Core

| Type    | Description      |
| ------ | ---------- |
| [import('../api/@ohos.web.webview').default.WebviewController](./arkts-apis-webview-WebviewController.md) | Controls various behaviors of the Web component through WebviewController. A WebviewController object can control only one Web component, and methods on WebviewController (except static methods) can be called only after the Web component and WebviewController are bound. |

## OnAdsBlockedCallback<sup>12+</sup>

type OnAdsBlockedCallback = (details: AdsBlockedDetails) => void

Defines a callback invoked when ads are blocked on the web page.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name              | Type                                       | Mandatory  | Description                        |
| -------------------- | ----------------------------------------------- | ---- | -------------------------------- |
| details | [AdsBlockedDetails](./arkts-basic-components-web-i.md#adsblockeddetails12) | Yes   | Detailed information about the blocked ads when ads are blocked.|

## OnSslErrorEventCallback<sup>12+</sup>

type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void

Callback invoked when an SSL error occurs during resource loading. Returns detailed information about the SSL error.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| sslErrorEvent | [SslErrorEvent](./arkts-basic-components-web-i.md#sslerrorevent12)  | Yes | Detailed information passed when an SSL error occurs during resource loading. |

## OnVerifyPinCallback<sup>22+</sup>

type OnVerifyPinCallback = (verifyPinEvent: VerifyPinEvent) => void

Callback triggered to notify the user of PIN authentication.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| verifyPinEvent | [VerifyPinEvent](./arkts-basic-components-web-i.md#verifypinevent22)  | Yes| Details of the callback triggered to notify the user of PIN authentication.|

## OnContextMenuHideCallback<sup>11+</sup>

type OnContextMenuHideCallback = () => void

Defines a callback invoked when the context menu is hidden.

**System capability**: SystemCapability.Web.Webview.Core

## OnRenderProcessNotRespondingCallback<sup>12+</sup>

type OnRenderProcessNotRespondingCallback = (data : RenderProcessNotRespondingData) => void

Defines a callback invoked when the rendering process does not respond.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| data | [RenderProcessNotRespondingData](./arkts-basic-components-web-i.md#renderprocessnotrespondingdata12) | Yes| Detailed information about the unresponsive rendering process.|

## OnRenderProcessRespondingCallback<sup>12+</sup>

type OnRenderProcessRespondingCallback = () => void

Defines a callback invoked when the rendering process transitions back to a normal operating state from an unresponsive state.

**System capability**: SystemCapability.Web.Webview.Core

## OnViewportFitChangedCallback<sup>12+</sup>

type OnViewportFitChangedCallback = (viewportFit: ViewportFit) => void

Defines a callback invoked when the **viewport-fit** configuration in the web page's **\<meta>** tag changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| viewportFit | [ViewportFit](./arkts-basic-components-web-e.md#viewportfit12) | Yes| Viewport type for **viewport-fit** in the web page **\<meta>** tag.|

## OnNativeEmbedVisibilityChangeCallback<sup>12+</sup>

type OnNativeEmbedVisibilityChangeCallback = (nativeEmbedVisibilityInfo: NativeEmbedVisibilityInfo) => void

Defines a callback invoked when the visibility of a same-layer tag changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| nativeEmbedVisibilityInfo | [NativeEmbedVisibilityInfo](./arkts-basic-components-web-i.md#nativeembedvisibilityinfo12) | Yes | Provides information about visibility changes of same-layer tags.|

## OnFullScreenEnterCallback<sup>12+</sup>

type OnFullScreenEnterCallback = (event: FullScreenEnterEvent) => void

Defines a callback invoked when the **Web** component enters full screen mode.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| event | [FullScreenEnterEvent](./arkts-basic-components-web-i.md#fullscreenenterevent12)  | Yes| Callback event for the **Web** component to enter full screen mode.|

## OnFirstMeaningfulPaintCallback<sup>12+</sup>

type OnFirstMeaningfulPaintCallback = (firstMeaningfulPaint: [FirstMeaningfulPaint](./arkts-basic-components-web-i.md#firstmeaningfulpaint12)) => void

Callback for measuring the first meaningful paint of the main content on the page. This callback is triggered when the page finishes loading the main content. Compared with OnLargestContentfulPaintCallback, which focuses on the paint time of the largest content element, and OnFirstScreenPaintCallback, which focuses on the rendering completion of the first screen's visible content, this callback focuses more on whether the main content has finished loading, making it suitable for evaluating the loading experience of user-visible content.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| firstMeaningfulPaint | [FirstMeaningfulPaint](./arkts-basic-components-web-i.md#firstmeaningfulpaint12) | Yes| Information about the first meaningful paint.|

## OnLargestContentfulPaintCallback<sup>12+</sup>

type OnLargestContentfulPaintCallback = (largestContentfulPaint: [LargestContentfulPaint](./arkts-basic-components-web-i.md#largestcontentfulpaint12)) => void

Callback triggered when the largest content area is painted on the web page. Used to obtain performance measurement information for the largest content paint. Applicable to scenarios such as monitoring web page loading performance and optimizing page rendering speed. Compared with OnFirstMeaningfulPaintCallback, which focuses on the completion of main content loading, and OnFirstScreenPaintCallback, which focuses on the rendering completion of the first screen's visible content, this callback focuses on the paint time of the largest content element, making it suitable for evaluating page rendering completeness and performance bottlenecks.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| largestContentfulPaint | [LargestContentfulPaint](./arkts-basic-components-web-i.md#largestcontentfulpaint12) | Yes| Information about the largest content paint.|

## OnNavigationEntryCommittedCallback<sup>11+</sup>

type OnNavigationEntryCommittedCallback = (loadCommittedDetails: [LoadCommittedDetails](./arkts-basic-components-web-i.md#loadcommitteddetails11)) => void

Defines a callback invoked when a navigation entry is submitted.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| loadCommittedDetails | [LoadCommittedDetails](./arkts-basic-components-web-i.md#loadcommitteddetails11)  | Yes| Detailed information about the web page that has been submitted for redirection.|

## OnSafeBrowsingCheckResultCallback<sup>11+</sup>

type OnSafeBrowsingCheckResultCallback = (threatType: ThreatType) => void

Defines a callback invoked by a website safe browsing check.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| threatType | [ThreatType](./arkts-basic-components-web-e.md#threattype11)  | Yes| Website threat type. |

## OnIntelligentTrackingPreventionCallback<sup>12+</sup>

type OnIntelligentTrackingPreventionCallback = (details: IntelligentTrackingPreventionDetails) => void

Defines a callback invoked when the tracker cookie is intercepted.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| details | [IntelligentTrackingPreventionDetails](./arkts-basic-components-web-i.md#intelligenttrackingpreventiondetails12)  | Yes| Detailed information about intelligent tracking prevention.|

## OnOverrideUrlLoadingCallback<sup>12+</sup>

type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean

Callback used to intercept URL loading requests. It can block the loading of specific URLs or perform custom processing. Applicable to scenarios such as intercepting ads and blocking redirects to malicious websites.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| webResourceRequest   |   [WebResourceRequest](./arkts-basic-components-web-WebResourceRequest.md)   | Yes  | Information about the URL request.|

**Return value**

| Type     | Description                      |
| ------- | ------------------------ |
| boolean | Whether the loading is blocked. **true** is returned if the loading is blocked; otherwise, **false** is returned.|

## WebKeyboardCallback<sup>12+</sup>

type WebKeyboardCallback = (keyboardCallbackInfo: WebKeyboardCallbackInfo) => WebKeyboardOptions

Defines a callback to intercept the soft keyboard initiated from editable elements on a web page. This event is typically called when the **\<input>** tag on the web page is clicked.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name          | Type  | Mandatory  | Description              |
| ------------- | ------ | ---- | ------------------ |
| keyboardCallbackInfo    | [WebKeyboardCallbackInfo](./arkts-basic-components-web-i.md#webkeyboardcallbackinfo12) | Yes   | Input parameter of the callback used to intercept the soft keyboard initiated from editable elements on a web page, including [WebKeyboardController](./arkts-basic-components-web-WebKeyboardController.md) and editable element attributes. |

**Return value**

| Type              | Description                                                        |
| ------------------ | ------------------------------------------------------------ |
| [WebKeyboardOptions](./arkts-basic-components-web-i.md#webkeyboardoptions12) | [WebKeyboardOptions](./arkts-basic-components-web-i.md#webkeyboardoptions12) instance, which is used to determine which type of soft keyboard to start by the ArkWeb kernel.|

## OnOverrideErrorPageCallback<sup>20+</sup>

type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string

Defines a callback of **onOverrideErrorPage**. This callback is triggered when a web page fails to be loaded.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name            | Type     | Mandatory  | Description                                      |
| -------------- | ---- | ---- | ---------------------------------------- |
| errorPageEvent | [OnErrorReceiveEvent](./arkts-basic-components-web-i.md#onerrorreceiveevent12) | Yes| Information returned when an error occurs during web page loading.     |

**Return value**

| Type     | Description                      |
| ------- | ------------------------ |
| string | Base64-encoded HTML text content.|

## MouseInfoCallback<sup>20+</sup>

type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void

This callback is triggered when a same-layer tag is clicked using the mouse or touchpad.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| event | [NativeEmbedMouseInfo](./arkts-basic-components-web-i.md#nativeembedmouseinfo20) | Yes | Detailed information about the mouse or touchpad click or long press on the same-layer tag. |

**Example**

For details about the sample code, see [onNativeEmbedMouseEvent](./arkts-basic-components-web-events.md#onnativeembedmouseevent20).

## OnNativeEmbedObjectParamChangeCallback<sup>21+</sup>

type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void

Defines a callback triggered when the **param** element embedded in the same-layer rendered **object** tag is added, modified, or deleted.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| event | [NativeEmbedParamDataInfo](./arkts-basic-components-web-i.md#nativeembedparamdatainfo21) | Yes| Detailed information about the changes of the **param** element embedded in the **object** tag.|

**Example**

For details about the sample code, see [onNativeEmbedObjectParamChange](./arkts-basic-components-web-events.md#onnativeembedobjectparamchange21).

## OnDetectBlankScreenCallback<sup>22+</sup>

type OnDetectBlankScreenCallback = (event: BlankScreenDetectionEventInfo) => void

Defines a callback triggered when a blank screen is detected.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| event | [BlankScreenDetectionEventInfo](./arkts-basic-components-web-i.md#blankscreendetectioneventinfo22) | Yes| Detailed information when a blank screen is detected.|

**Example**

For details about the sample code, see [onDetectedBlankScreen](./arkts-basic-components-web-events.md#ondetectedblankscreen22).

## OnCameraCaptureStateChangeCallback<sup>23+</sup>

type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void

This callback is triggered when the camera device state of the page changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name              | Type                                       | Mandatory  | Description                        |
| -------------------- | ----------------------------------------------- | ---- | -------------------------------- |
| event | [CameraCaptureStateChangeInfo](./arkts-basic-components-web-i.md#cameracapturestatechangeinfo23) | Yes   | Original and new camera state.|

## OnMicrophoneCaptureStateChangeCallback<sup>23+</sup>

type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void

Defines a callback triggered when the microphone state of the page changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name              | Type                                       | Mandatory  | Description                        |
| -------------------- | ----------------------------------------------- | ---- | -------------------------------- |
| event | [MicrophoneCaptureStateChangeInfo](./arkts-basic-components-web-i.md#microphonecapturestatechangeinfo23) | Yes   | Original and new microphone state.|

## TextSelectionChangeCallback<sup>23+</sup>

type TextSelectionChangeCallback = (selectionText: string) => void

Callback for onTextSelectionChange. Triggered when the text selection content changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name            | Type     | Mandatory  | Description                                      |
| -------------- | ---- | ---- | ---------------------------------------- |
| selectionText | string | Yes| Selected text.     |

**Example**

For details about the complete sample code, see [onTextSelectionChange](./arkts-basic-components-web-events.md#ontextselectionchange23).

## OnFirstScreenPaintCallback<sup>23+</sup>

type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void

This callback is triggered when the first screen rendering is detected to be complete. Compared with OnFirstMeaningfulPaintCallback, which focuses on the completion of main content loading, and OnLargestContentfulPaintCallback, which focuses on the paint time of the largest content element, this callback focuses more on the rendering completion time of the first screen's visible content, making it suitable for evaluating the user's first visual experience.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| firstScreenPaint | [FirstScreenPaint](./arkts-basic-components-web-i.md#firstscreenpaint23) | Yes| Details about the first screen paint.|

**Example**

For details about the complete sample code, see [onFirstScreenPaint](./arkts-basic-components-web-events.md#onfirstscreenpaint23).

## OnCreateAISession

type OnCreateAISession = (id: string, params: string, result: OnAISessionCallback) => boolean

AI session creation callback function type. Allows custom model initialization and result processing.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                                            | Mandatory | Description                 |
| ------ | --------------------------------------------- | -- | ------------------ |
| id     | string                                        | Yes  | Session task ID.            |
| params | string                                        | Yes  | Context data passed during session creation, in JSON string format.|
| result | [OnAISessionCallback](#onaisessioncallback) | Yes  | Callback used to notify the system of the session creation result. |

**Return value**

| Type      | Description                                            |
| ------- | --------------------------------------------- |
| boolean | The value **true** indicates that custom logic is used, skipping the system default behavior; **false** indicates that the system default logic continues to be executed. |

## OnExecuteAIAction

type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void

AI session execution operation callback function type. Used to implement custom AI model execution.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                                            | Mandatory | Description                 |
| ------ | --------------------------------------------- | -- | ------------------ |
| id     | string                                        | Yes  | Session task ID.            |
| params | string                                        | Yes  | Context data passed during operation execution, in JSON string format.|
| result | [OnAISessionCallback](#onaisessioncallback) | Yes  | Callback used to notify the system of the operation execution result. |

## OnDestroyAISession

type OnDestroyAISession = (id: string) => void

AI session destruction callback function type. Used to clean up resources associated with the custom AI model.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type     | Mandatory | Description      |
| --- | ------ | -- | ------- |
| id  | string | Yes  | Session task ID. |

## OnAISessionCallback

type OnAISessionCallback = (state: AISessionResultType, content: string) => void

AI session operation result callback function type. Used to report the result of session creation or execution.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name     | Type                                                                             | Mandatory | Description              |
| ------- | ------------------------------------------------------------------------------ | -- | --------------- |
| state   | [AISessionResultType](./arkts-basic-components-web-e.md#aisessionresulttype) | Yes  | Status result of AI session creation or execution. |
| content | string                                                                         | Yes  | Response content of the AI session, in text or JSON format, containing the reply content generated by the AI model.|

## OnInputmethodAttachedCallback

type OnInputmethodAttachedCallback = () => void;

This callback is triggered when the input method is detected to be successfully attached.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For the complete example, see [onInputmethodAttached](./arkts-basic-components-web-events.md#oninputmethodattached).
<!--no_check-->