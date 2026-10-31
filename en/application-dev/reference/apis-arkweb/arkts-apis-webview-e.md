# Enums

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=595dfecd254e3797b40fd02681ac1055f9439da2 translatedAt=2026-08-07T04:26:21.387Z pushedAt=2026-08-07T07:52:02.478Z -->

The ArkWeb Enums module is a collection of enum type definitions for ArkWeb (Web subsystem), providing unified type constraints and state description capabilities for the WebView component and its associated API classes. This module defines enum types covering multiple domains such as web page interaction, security status, DNS configuration, download tasks, media playback control, kernel version, process mode, memory management, offline resources, no-white-screen loading, site isolation, soft keyboard behavior, cookie policy, scroll control, and device form factor, serving as the foundational type support layer for the entire WebView API system.

When using core classes such as WebviewController, WebMessagePort, WebDownloadItem, NativeMediaPlayerHandler, NativeMediaPlayerBridge, and WebSchemeHandlerRequest in [Module Description](arkts-apis-webview.md), developers must rely on the enum types in this module to configure behavior parameters or parse returned results. When developers need to finely control the running mode of the Web component, query page status, handle download tasks, integrate native media playback control, or optimize loading experience, they should refer to the corresponding enum definitions in this module.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## WebHitTestType

Enumerates the node types that the cursor hits.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| EditText      | 0 |Editable area.                           |
| Email         | 1 |Email address.                           |
| HttpAnchor    | 2 | Hyperlink with an HTTP address. |
| HttpAnchorImg | 3 | Image with a hyperlink, where the link address is HTTP + HTML::img. |
| Img           | 4 |HTML::img tag.                          |
| Map           | 5 |Geographical address.                               |
| Phone         | 6 |Phone number.                               |
| Unknown       | 7 |Unknown content.                               |

## SecureDnsMode<sup>10+</sup>

Enumerates the modes in which the **Web** component uses HTTPDNS.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| OFF                                  | 0 | HTTPDNS is not used. It can be used to revoke the previously used HTTPDNS configuration. |
| AUTO                                 | 1 |HTTPDNS is used in automatic mode. If the specified HTTPDNS server is unavailable for resolution, the component falls back to the system DNS server.|
| SECURE_ONLY                          | 2 |The specified HTTPDNS server is forcibly used for DNS resolution.|

## SecurityLevel<sup>11+</sup>

Enumerates the security levels of the web page.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| NONE          | 0 |The web page is neither absolutely secure nor insecure, that is, neutral. A typical example is a web page whose URL scheme is not HTTP or HTTPS.|
| SECURE        | 1 |The web page is secure, using the HTTPS protocol and a trusted certificate.|
| WARNING       | 2 |The web page is insecure. A typical example is a web page that uses the HTTP or HTTPS protocol but an outdated TLS version.|
| DANGEROUS     | 3 |The web page is dangerous. This means that the page may have attempted to load HTTPS scripts to no avail, have failed authentication, or contain insecure active content in HTTPS, malware, phishing, or any other sources of major threats.|

## MediaPlaybackState<sup>12+</sup>

Enumerates the playback control states of the current web page.

**System capability**: SystemCapability.Web.Webview.Core

| Name   | Value  | Description              |
| ------- | ---- | ------------------ |
| NONE    | 0    | No audio or video playback is started on the page.|
| PLAYING | 1    | The audio and video on the page are being played.|
| PAUSED  | 2    | The audio and video on the page are paused.  |
| STOPPED | 3    | The audio and video on the page are stopped.  |

## PressureLevel<sup>14+</sup>

Enumerates the memory pressure levels. When an application clears the cache occupied by the **Web** component, the **Web** kernel releases the cache based on the memory pressure level.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| MEMORY_PRESSURE_LEVEL_MODERATE | 1 | Moderate memory pressure level. At this level, the **Web** kernel attempts to release the cache that has low reallocation overhead and does not need to be used immediately.|
| MEMORY_PRESSURE_LEVEL_CRITICAL | 2 | Critical memory pressure level. At this level, the **Web** kernel attempts to release all possible memory caches.|

## WebMessageType<sup>10+</sup>

Enumerates the data types supported by the [WebMessagePort](./arkts-apis-webview-WebMessagePort.md) API.

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Value| Description                           |
| ------------ | -- |------------------------------- |
| NOT_SUPPORT  | 0 |Unsupported data type.|
| STRING       | 1 |String type.|
| NUMBER       | 2 |Number type.|
| BOOLEAN      | 3 |Boolean type.|
| ARRAY_BUFFER | 4 |Raw binary data buffer.|
| ARRAY        | 5 |Array type.|
| ERROR        | 6 |Error object type.|

## JsMessageType<sup>10+</sup>

Enumerates the data types of the results returned after the [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10) API is executed.

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Value| Description                             |
| ------------ | -- |--------------------------------- |
| NOT_SUPPORT  | 0 |Unsupported data type.|
| STRING       | 1 |String type.|
| NUMBER       | 2 |Number type.|
| BOOLEAN      | 3 |Boolean type.|
| ARRAY_BUFFER | 4 |Raw binary data buffer.|
| ARRAY        | 5 |Array type.|

## RenderProcessMode<sup>12+</sup>

Enumerates the ArkWeb renderer subprocess mode types. You can select the appropriate mode based on the app's requirements for memory usage and renderer process isolation.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| SINGLE        | 0 |ArkWeb single render subprocess mode. In this mode, multiple **Web** components share one render subprocess.|
| MULTIPLE      | 1 |ArkWeb multi-render subprocess mode. In this mode, each **Web** component has a rendering subprocess.|

## OfflineResourceType<sup>12+</sup>

Enumerates the offline resource types corresponding to the [OfflineResourceMap](./arkts-apis-webview-i.md#offlineresourcemap12) object.

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Value| Description                             |
| ------------ | -- |--------------------------------- |
| IMAGE  | 0 | Resource of the image type.|
| CSS       | 1 | Resource of the CSS type.|
| CLASSIC_JS       | 2 | JavaScript resources loaded via the &lt;script src="" /&gt; tag.|
| MODULE_JS      | 3 | JavaScript resources loaded via the &lt;script src="" type="module" /&gt; tag.|

## ScrollType<sup>12+</sup>

Enumerates the scroll types for [setScrollable](./arkts-apis-webview-WebviewController.md#setscrollable12).

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Value| Description                             |
| ------------ | -- |--------------------------------- |
| EVENT  | 0 | Scroll event, which represents web page scrolling generated through the touchscreen, touchpad, or mouse wheel. |

## WebDownloadState<sup>11+</sup>

Enumerates the states of a download task.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| IN_PROGRESS                                  | 0 |The download task is in progress.|
| COMPLETED                                 | 1 |The download task is completed.|
| CANCELED                          | 2 |The download task has been canceled.|
| INTERRUPTED                          | 3 |The download task is interrupted.|
| PENDING                          | 4 |The download task is pending.|
| PAUSED                          | 5 |The download task is paused.|
| UNKNOWN                          | 6 |The state of the download task is unknown.|

## WebDownloadErrorCode<sup>11+</sup>

Enumerates the download task error codes.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| ERROR_UNKNOWN                                  | 0 |Unknown error.|
| FILE_FAILED | 1 |  Failed to operate the file.|
| FILE_ACCESS_DENIED | 2 | No permission to access the file.|
| FILE_NO_SPACE | 3 | The disk space is insufficient.|
| FILE_NAME_TOO_LONG | 5 | The file name is too long. |
| FILE_TOO_LARGE | 6 | The file is too large.|
| FILE_TRANSIENT_ERROR | 10 |  Some temporary issues occur, such as insufficient memory, files in use, and too many files open at the same time.|
| FILE_BLOCKED | 11 |  Access to the file is blocked due to certain local policies.|
| FILE_TOO_SHORT | 13 |  The file to resume downloading is not long enough. It may not exist.|
| FILE_HASH_MISMATCH | 14 |  Hash mismatch.|
| FILE_SAME_AS_SOURCE | 15 |  The file already exists.|
| NETWORK_FAILED | 20 |  Common network error.|
| NETWORK_TIMEOUT | 21 | Network connection timeout.|
| NETWORK_DISCONNECTED | 22 | Network disconnected.|
| NETWORK_SERVER_DOWN | 23 |  The server is shut down.|
| NETWORK_INVALID_REQUEST | 24 |  Invalid network request. The request may be redirected to an unsupported scheme or an invalid URL.|
| SERVER_FAILED | 30 | The server returns a general error.|
| SERVER_NO_RANGE | 31 |  The server does not support the range request.|
| SERVER_BAD_CONTENT | 33 |   The server does not have the requested data.|
| SERVER_UNAUTHORIZED | 34 |  The file cannot be downloaded from the server.|
| SERVER_CERT_PROBLEM | 35 |  The server certificate is incorrect.|
| SERVER_FORBIDDEN | 36 |  The access to the server is forbidden.|
| SERVER_UNREACHABLE | 37 |  The server cannot be accessed.|
| SERVER_CONTENT_LENGTH_MISMATCH | 38 |  The received data does not match the content length.|
| SERVER_CROSS_ORIGIN_REDIRECT | 39 | An unexpected cross-site redirection occurs.|
| USER_CANCELED | 40 | The user cancels the download.|
| USER_SHUTDOWN | 41 | The user closes the application.|
| CRASH | 50 | The application crashes.|

## WebResourceType<sup>12+</sup>

Enumerates the types of requested resources.

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Value| Description                             |
| ------------ | -- |--------------------------------- |
| MAIN_FRAME | 0 | Top-level page.|
| SUB_FRAME | 1 | Frame or Iframe.|
| STYLE_SHEET | 2 | CSS style sheet.|
| SCRIPT | 3 | External script.|
| IMAGE | 4 | Image (JPG, GIF, PNG, or other format).|
| FONT_RESOURCE | 5 | Font.|
| SUB_RESOURCE | 6 | Other sub-resource. If the type is unknown, it is used as the default type.|
| OBJECT | 7 | Object (or embed) tag of the plug-in, or the resource requested by the plug-in.|
| MEDIA | 8 | Media resource.|
| WORKER | 9 | Main resource of a dedicated worker thread.|
| SHARED_WORKER | 10 | Main resource of a shared worker thread.|
| PREFETCH | 11 | Explicit prefetch request.|
| FAVICON | 12 | Website icon.|
| XHR | 13 | XMLHttpRequest.|
| PING | 14 | <a ping\>/sendBeacon ping request.|
| SERVICE_WORKER | 15 | Main resource of a service worker.|
| CSP_REPORT | 16 | Report of Content Security Policy violation.|
| PLUGIN_RESOURCE | 17 | Resource requested by the plug-in.|
| NAVIGATION_PRELOAD_MAIN_FRAME | 19 | Main frame redirection request that triggers service worker preloading.|
| NAVIGATION_PRELOAD_SUB_FRAME | 20 | Subframe redirection request that triggers service worker preloading.|

## PlaybackStatus<sup>12+</sup>

Enumerates the playback statuses of the player, which is an input parameter of the [handleStatusChanged](./arkts-apis-webview-NativeMediaPlayerHandler.md#handlestatuschanged12) API.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| PAUSED  | 0 | Media paused. |
| PLAYING | 1 | Media playing. |

## NetworkState<sup>12+</sup>

Enumerates the network statuses of the player.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| EMPTY         | 0 | The player has not started downloading data.|
| IDLE          | 1 | The player's network activity is idle. This could mean that the download of a media segment is complete, and the player is waiting to start downloading the next segment.|
| LOADING       | 2 | The player is downloading media data.|
| NETWORK_ERROR | 3 | A network error occurs.|

## ReadyState<sup>12+</sup>

Enumerates the cache states of the player.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| HAVE_NOTHING      | 0 | There is no data cached.|
| HAVE_METADATA     | 1 | Only media metadata is cached.|
| HAVE_CURRENT_DATA | 2 | Data up to the current playback position is cached.|
| HAVE_FUTURE_DATA | 3 | The buffered duration exceeds the current playback progress, but stuttering may still occur. |
| HAVE_ENOUGH_DATA  | 4 | Sufficient data has been cached to ensure smooth playback.|

## MediaError<sup>12+</sup>

Enumerates the error types of the player.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| NETWORK_ERROR | 1 | Network error.|
| FORMAT_ERROR  | 2 | Media format error.|
| DECODE_ERROR  | 3 | Decoding error.|

## SuspendType<sup>12+</sup>

Enumerates the suspension types of the player.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| ENTER_BACK_FORWARD_CACHE | 0 | The page enters the BFCache. |
| ENTER_BACKGROUND         | 1 | The page enters the background. |
| AUTO_CLEANUP             | 2 | The page is automatically cleaned up by the system.|

## MediaType<sup>12+</sup>

Enumerates the media types.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| VIDEO | 0 | Video.|
| AUDIO | 1 | Audio.|

## SourceType<sup>12+</sup>

Enumerates the media source types.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| URL | 0 | URL.|
| MSE | 1 | Blob.|

## Preload<sup>12+</sup>

Enumerates how the player preloads media data.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
|------|----|------|
| NONE     | 0 | No media data is preloaded.|
| METADATA | 1 | Only the metadata of the media is preloaded.|
| AUTO     | 2 | A sufficient amount of media data is preloaded to ensure smooth playback|

## ProxySchemeFilter<sup>15+</sup>

Enumerates the schemes that use the proxy.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| MATCH_ALL_SCHEMES | 0 |All schemes use proxies.|
| MATCH_HTTP        | 1 |HTTP requests use proxies.|
| MATCH_HTTPS       | 2 |HTTPS requests use proxies.|

## WebDestroyMode<sup>20+</sup>

Enumerates the destroy modes of the **Web** component. When the Web component is destroyed, the destroy mode affects the resource release time of the Web kernel, such as the JavaScript running context and rendering context.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| NORMAL_MODE | 0 | Normal mode. The system determines the destroy time of **Web** component resources.|
| FAST_MODE   | 1 | Quick mode. When the **Web** component is destroyed, the related internal resources are destroyed immediately.|

## ScrollbarMode<sup>23+</sup>

Enumerates the global scrollbar modes in the web page.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| OVERLAY_LAYOUT_SCROLLBAR  | 0 | Overlay scrollbar that can be dragged. |
| FORCE_DISPLAY_SCROLLBAR    | 1 | The scrollbar is always displayed.|
| OVERLAY_VISUAL_SCROLLBAR    | 2 | Overlay scrollbar that cannot be dragged.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model. |

## WebBlanklessErrorCode<sup>20+</sup>

Enumerates the error codes of the blankless loading.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| SUCCESS | 0 | Operation successful.|
| ERR_UNKNOWN   | -1 | Unknown error or internal status error.|
| ERR_INVALID_PARAM   | -2 | Invalid parameter.|
| ERR_CONTROLLER_NOT_INITED   | -3 | **WebViewController** is not bound to any component.|
| ERR_KEY_NOT_MATCH   | -4 | No key value is matched. [setBlanklessLoadingWithKey](./arkts-apis-webview-WebviewController.md#setblanklessloadingwithkey20) must be used with [getBlanklessInfoWithKey](./arkts-apis-webview-WebviewController.md#getblanklessinfowithkey20) and their key values must be the same. Otherwise, this error code is returned.|
| ERR_SIGNIFICANT_CHANGE   | -5 | The similarity is low, and the system determines that the scene change is too large. As a result, the [setBlanklessLoadingWithKey](./arkts-apis-webview-WebviewController.md#setblanklessloadingwithkey20) API does not enable frame interpolation.|
| ERR_DURATION_OUT_OF_RANGE<sup>23+</sup>   | -6 | The frame interpolation duration set in [BlanklessLoadingParam](./arkts-apis-webview-i.md#blanklessloadingparam23) is out of range.<br>**Model restriction**: This API can be used only in the stage model.|
| ERR_EXPIRATION_TIME_OUT_OF_RANGE<sup>23+</sup>   | -7 | The historical frame expiration time set in [BlanklessLoadingParam](./arkts-apis-webview-i.md#blanklessloadingparam23) is out of range.<br>**Model restriction**: This API can be used only in the stage model.|

## BlanklessFrameInterpolationState <sup>23+</sup>

Frame interpolation status of blankless loading.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| FRAME_INTERPOLATION_SUCCEEDED | 0 | Frame interpolation succeeded.|
| FRAME_INTERPOLATION_FAILED   | 1 | Frame interpolation failed.|
| FRAME_INTERPOLATION_REMOVED   | 2 | The frame interpolation is removed.|

## ArkWebEngineVersion<sup>20+</sup>

For ArkWeb kernel versions, see [Adaptation Guide for the M114 Kernel on OpenHarmony 6.0](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md) and [Adaptation Guide for the M132 Kernel on OpenHarmony 7.0](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md).

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| SYSTEM_DEFAULT   | 0     | System default kernel (see [Constraints](../../web/web-component-overview.md#constraints)). The default kernel is M132 for OpenHarmony 6.0 and M144 for OpenHarmony 7.0.|
| M114             | 1     | Legacy kernel of OpenHarmony 6.0. Developers can select this legacy kernel. If this kernel does not exist on the system version, the setting does not take effect and the system default kernel is used.|
| M132             | 2     | Evergreen kernel of OpenHarmony 6.0 (legacy kernel of OpenHarmony 7.0). M132 is the default kernel of OpenHarmony 6.0. If this kernel does not exist on the system version, the setting does not take effect and the system default kernel is used.|
| M144             | 3     | Evergreen kernel of OpenHarmony 7.0. M144 is the default kernel of OpenHarmony 7.0. If this kernel does not exist on the system version, the setting does not take effect and the system default kernel is used.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model. |
| ARKWEB_EVERGREEN<sup>23+</sup> | 99999 | The latest kernel (evergreen kernel) of the system. Developers can select this kernel to always use the latest kernel on each system version. |

**Table 1** Description of evergreen kernel and legacy kernel

| Kernel Type| Name| Description|
| ----------- | -------- | -------- |
| Evergreen kernel    | EVERGREEN WebCore | Latest Web kernel of the system, based on which the complete functionalities are implemented. This kernel is recommended for applications.|
| Legacy kernel    | LEGACY WebCore    | A previous-release kernel that receives only security and PR-related fixes, used solely for compatibility rollback, and is supported for a fixed duration only.|

## SiteIsolationMode<sup>21+</sup>

The site isolation mechanism isolates websites from different origins in different renderer subprocesses, reducing the cross-origin attack surface. For example, in the original process model on PC, each tab corresponds to one renderer subprocess. After site isolation is enabled, iframes from different origins run in independent renderer subprocesses.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| PARTIAL | 0 | Partial site isolation, that is, new sites are loaded in the same renderer process. |
| STRICT  | 1 | Strict site isolation. Iframes from different sites are switched to new render processes.|

## WebSoftKeyboardBehaviorMode<sup>22+</sup>

Enumerates the behavior modes of the web soft keyboard.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| DEFAULT | 0 | When the **Web** component is focused or unfocused, or its status changes to inactive or active, the system attempts to hide or display the soft keyboard. This value is used by default.|
| DISABLE_AUTO_KEYBOARD_ON_ACTIVE | 1 | When the **Web** component's status changes between inactive and active, the system does not hide or start the soft keyboard.|

## WebHttpCookieSameSitePolicy<sup>23+</sup>

Enumerates the policies for sending cookies in cross-site requests.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ---- | -- |----------------------------------------- |
| NONE | 0 | Cookies can be carried in cross-site requests, but the **secure** attribute must be set.|
| LAX | 1 | Cookies can be carried in specific cross-site requests, such as navigation scenarios of some GET requests.|
| STRICT | 2 | Cookies cannot be carried in cross-site requests.|

## UserAgentFormFactor<sup>24+</sup>

Enumerates the user device forms.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

| Name        | Value| Description                             |
| ------------ | -- |--------------------------------- |
| AUTOMOTIVE  | 'Automotive' |Telematics device, which is a string.|
| DESKTOP       | 'Desktop' |PC, which is a string.|
| MOBILE       | 'Mobile' |Mobile phone, which is a string.|
| EINK      | 'EInk' |E-ink screen, which is a string.|
| TABLET | 'Tablet' |Tablet, which is a string.|
| WATCH        | 'Watch' |Watch, a string type.|
| XR        | 'XR' |VR+AR device, a string type.|