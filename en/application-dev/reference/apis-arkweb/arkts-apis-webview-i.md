# Interfaces (Others)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:28:28.212Z pushedAt=2026-08-07T08:07:48.238Z -->

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual device.

## Overview

This page summarizes the auxiliary interfaces and data structure types in the ArkWeb Webview module (`@kit.ArkWeb`). These types are primarily used as method input parameters, callback output parameters, or state enums for various Web component capabilities, working together with core classes such as [WebviewController](./arkts-apis-webview-WebviewController.md), [WebCookieManager](./arkts-apis-webview-WebCookieManager.md), and [WebStorage](./arkts-apis-webview-WebStorage.md) to implement control capabilities including web page loading, rendering, interaction, media takeover, and performance optimization.

This module provides web control capabilities. For web page display capabilities, see [Component Description](./arkts-basic-components-web.md). For a complete description of web control capabilities and the core controller class, see [Module Description](./arkts-apis-webview.md).

## WebStorageOrigin

Provides usage information of the Web SQL Database.

**System capability**: SystemCapability.Web.Webview.Core

| Name  | Type  | Read-Only| Optional| Description|
| ------ | ------ | ---- | ---- | ---- |
| origin | string | No | No| Index of the origin.|
| usage  | number | No  | No | Storage usage of the specified source.<br>Unit: byte.     |
| quota  | number | No  | No | Storage quota of the specified source.<br>Unit: byte.   |

## WebHeader

Describes the request/response header returned by the **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| headerKey   | string | No| No| Key of the request/response header.  |
| headerValue | string | No| No| Value of the request/response header.|

## WebCustomScheme

Defines a custom URL scheme.

**System capability**: SystemCapability.Web.Webview.Core

| Name          | Type      | Read-Only| Optional| Description                        |
| -------------- | --------- | ---- | ---- | ---------------------------- |
| schemeName     | string    | No   | No   | Custom protocol name. The maximum length is 32, and only lowercase letters, digits, '.', '+', and '-' are supported. It must start with a letter. If the preceding restrictions are not met, the custom protocol configuration does not take effect.        |
| isSupportCORS  | boolean   | No  | No  | Whether to support cross-origin resource sharing (CORS).<br>The value **true** means to support cross-origin resource sharing (CORS), and **false** means the opposite.<br>Default value: **true**.   |
| isSupportFetch | boolean   | No  | No  | Whether to support fetch requests.<br>The value **true** means to support fetch requests, and **false** means the opposite.<br>Default value: **true**.          |
| isStandard<sup>12+</sup> | boolean   | No   | Yes   | Whether the scheme with this option set is processed as a standard scheme. A standard scheme must comply with the URL parsing rules defined in RFC 1738 section 3.1 and the URL normalization rules defined in RFC 3986 section 6.2.<br>**true** indicates that the scheme with this option set is processed as a standard scheme, and **false** indicates that it is not processed as a standard scheme.<br>Default value: true.           |
| isLocal<sup>12+</sup> | boolean   | No  | Yes  | Whether the scheme is treated with the same security rules as those applied to file URLs.<br>The value **true** indicates that the scheme is treated with the same security rules as those applied to file URLs, and the value **false** indicates the opposite.<br>Default value: **true**.          |
| isDisplayIsolated<sup>12+</sup> | boolean   | No   | Yes   | Whether the content of the scheme with this option set can only be displayed or accessed from other content of the same scheme.<br>**true** indicates that the content of the scheme with this option set can only be displayed or accessed from other content of the same scheme, and **false** indicates that the content of the scheme with this option set can be displayed or accessed from content of other schemes.<br>Default value: true.           |
| isSecure<sup>12+</sup> | boolean   | No  | Yes  | Whether the scheme is treated with the same security rules as those applied to HTTPS URLs. The value **true** indicates that the scheme is treated with the same security rules as those applied to HTTPS URLs, and **false** indicates the opposite.<br>Default value: **true**.          |
| isCspBypassing<sup>12+</sup> | boolean   | No   | Yes   | Whether the scheme with this option set can bypass Content Security Policy (CSP) checks.<br>**true** indicates that the scheme with this option set can bypass CSP checks, and **false** indicates that it cannot bypass CSP checks.<br>Default value: true.<br>When **isStandard** is set to **true**, this value should not be set. If **isCspBypassing** is still set to **true** in this case, the CSP bypass behavior may not meet expectations.         |
| isCodeCacheSupported<sup>12+</sup> | boolean   | No   | Yes   | Whether JavaScript resources of the scheme with this option set support code cache generation.<br>**true** indicates that JavaScript resources of the scheme with this option set support code cache generation, and **false** indicates that they do not support code cache generation.<br>Default value: false.         |

## RequestInfo<sup>12+</sup>

Describes the information about the resource request sent by the **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

| Name     | Type  | Read-Only| Optional|Description       |
| ---------| ------ | -----|------|--------  |
| url      | string | No| No| URL of the request.   |
| method   | string | No| No| Method of the request.   |
| formData | string | No| No| Form data in the request body.|

## CacheOptions<sup>12+</sup>

Represents a configuration object for precompiling JavaScript in the **Web** component to generate bytecode cache, which is designed to control the updating of the bytecode cache.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| responseHeaders   | Array<[WebHeader](#webheader)> | No | No | Response headers returned by the server when requesting this JavaScript file. ETag or Last-Modified is used to identify the file version and determine whether an update is needed.   |

## SnapshotInfo<sup>12+</sup>

Provides information used to obtain a full drawing result.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type|  Read-Only|  Optional| Description|
|------|------|------|------|------|
| id | string | No | Yes | ID of the snapshot, used to identify this full rendering request so that the corresponding full rendering data can be matched in the callback result. If not passed, no ID is specified and the system handles it automatically.|
| size | [SizeOptions](../apis-arkui/arkui-ts/ts-types.md#sizeoptions)  | No | Yes | Size of the Web rendering. The maximum supported size is 16000px * 16000px. The supported length units are px, vp, and %. The length units passed in different parameters must be consistent; otherwise, the rendering size may not meet expectations. The default unit is vp. If the specified size exceeds the specification, the maximum specification is returned. If not passed, the rendering is performed at the actual size of the screenshot area. (Example: width:'100px', height:'200px'. Or width:'20%', height:'30%'. If only a number is specified, the unit is vp.)|

## SnapshotResult<sup>12+</sup>

Represents a full drawing result.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional|  Description|
|------|------|-- |--|---------|
| id | string | No| Yes| Snapshot ID.|
| status | boolean | No | Yes | Status of the snapshot. The value **true** indicates normal, and **false** indicates failure. If obtaining the full rendering result fails, the width and height of the returned size are both 0, and imagePixelMap is empty. |
| size | [SizeOptions](../apis-arkui/arkui-ts/ts-types.md#sizeoptions) | No | Yes | Actual size rendered by Web. The SizeOptions object contains the width and height attributes, both of which are of the number type, in vp. |
| imagePixelMap | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No| Yes| The **image.PixelMap** format.|

## OfflineResourceMap<sup>12+</sup>

Implements an **OfflineResourceMap** object, which is used to set information related to local offline resources that will be injected into memory cache through the [injectOfflineResources](./arkts-apis-webview-WebviewController.md#injectofflineresources12) API. The ArkWeb engine will generate resource caches based on this information and control the validity period of the cache accordingly.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| urlList | Array\<string\> | No   | No   | List of network addresses corresponding to the local offline resources. The first item in the list serves as the origin of the resources. If only one network address is provided, it is used as the origin of the resources. The URL supports only HTTP or HTTPS and cannot exceed 2048 characters. If the preceding restrictions are not met, the resource injection fails.      |
| resource | Uint8Array | No  | No  | Content of a local offline resource.     |
| responseHeaders | Array\<[WebHeader](#webheader)\> | No   | No   | HTTP response headers corresponding to the resources. The Cache-Control or Expires response header provided is used to control the validity period of the resources in the memory cache. If not provided, the default validity period is 86400 seconds, that is, 1 day. The Content-Type response header provided is used to define the MIME type of the resources. MODULE_JS must provide a valid MIME type. Other types may not provide one, and there is no default value. A non-standard MIME type will cause the memory cache to become invalid. If the script tag in the service web page uses the crossorigin attribute, the Cross-Origin response header must be set to **anonymous** or **use-credentials** in the responseHeaders parameter of this API. Otherwise, the memory cache may become invalid.      |
| type | [OfflineResourceType](./arkts-apis-webview-e.md#offlineresourcetype12) | No   | No   | Type of the resources. Currently, only JavaScript, image, and CSS resources are supported.      |

##  PdfConfiguration<sup>14+</sup>

Input parameter of the [createPdf](./arkts-apis-webview-WebviewController.md#createpdf14) function.

> **NOTE**
>
> The number of pixels is calculated as follows: Number of pixels = 96 x Number of inches.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| width                 | number  | No   | No   | Page Width.<br>Value range: greater than or equal to 0. If the value is out of range, it is set to 0.<br>Unit: inch.<br>Recommended value: A4 paper page width 8.27 inches.   |
| height                | number  | No   | No   | Page Height.<br>Value range: greater than or equal to 0. If the value is out of range, it is set to 0.<br>Unit: inch.<br>Recommended value: A4 paper page height 11.69 inches.  |
| scale                 | number  | No| Yes  | Scale multiple.<br>The value range is [0.0, 2.0]. If the value is less than 0.0, set it to **0.0**. If the value is greater than 2.0, set it to **2.0**.<br>Default value: **1.0**|
| marginTop             | number  | No| No  | Top margin.<br>The value range is [0.0, half of the page height). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| marginBottom          | number  | No| No  | Bottom margin.<br>The value range is [0.0, half of the page height). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| marginRight           | number  | No| No  | Right margin.<br>The value range is [0.0, half of the page width). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| marginLeft            | number  | No| No  | Left margin.<br>The value range is [0.0, half of the page width). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| shouldPrintBackground | boolean | No| Yes  | Whether to print the background color. The value **true** means to print the background color, and **false** means the opposite.<br>Default value: **false**.                           |

## ScrollOffset<sup>13+</sup>

Represents the current scrolling offset of a web page.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type  | Read-Only| Optional| Description                                                        |
| ---- | ------ | ---- | ---- | ------------------------------------------------------------ |
| x    | number | No   | No   | Horizontal scroll offset of the web page. The value is the difference between the x-coordinate of the left edge of the web page and the x-coordinate of the left edge of the Web component.<br>When the web page is over-scrolled to the right, the value is negative.<br>When the web page is not over-scrolled or is over-scrolled to the left, the value is 0 or positive.<br>Unit: vp. |
| y    | number | No   | No   | Vertical scroll offset of the web page. The value is the difference between the y-coordinate of the top edge of the web page and the y-coordinate of the top edge of the Web component.<br>When the web page is over-scrolled downward, the value is negative.<br>When the web page is not over-scrolled or is over-scrolled upward, the value is 0 or positive.<br>Unit: vp. |

## HitTestValue

Provides the element information of the area being clicked. For the sample code, see [getLastHitTest](./arkts-apis-webview-WebviewController.md#getlasthittest18).

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- |---- |
| type | [WebHitTestType](./arkts-apis-webview-e.md#webhittesttype) | No| No| Element type of the area being clicked.|
| extra | string        | No| No|Extra information of the area being clicked. If the area being clicked is an image or a link, the extra information is the URL of the image or link.|

## ControllerAttachState<sup>20+</sup>

Binding state between WebviewController and the Web component.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Value| Description|
| ------------------------------- | - | ---------- |
| UNATTACHED | 0 | Unattached.|
| ATTACHED   | 1 | Attached.|

## BlanklessInfo<sup>20+</sup>

Prediction information about the first screen loading of the page, mainly including the predicted first screen similarity, predicted first screen loading duration, and predicted error code. The app determines whether to enable the White-Screen-Free Loading frame interpolation scheme based on this information.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| errCode | [WebBlanklessErrorCode](./arkts-apis-webview-e.md#webblanklesserrorcode20) | No | No | Error code for white-screen-free loading. For details, see [WebBlanklessErrorCode](./arkts-apis-webview-e.md#webblanklesserrorcode20). |
| similarity | number | No | No | Similarity of the first screen. The similarity is calculated based on the first screen content of historical loads. The value ranges from [0, 1.0], where **1.0** indicates a complete match. The closer the value is to 1, the higher the similarity. This value has a lagging nature, meaning the similarity of a local load will only be reflected in the next load. It is recommended that the app does not enable the white-screen-free loading frame insertion solution when the similarity is below a specific threshold (for example, 0.33). |
| loadingTime | number | No | No | Predicts the loading time of the current load based on the first screen loading time of historical loads. Unit: ms. Value range: greater than 0. |

## BlanklessFrameInterpolationInfo<sup>23+</sup>

White-Screen-Free Loading frame interpolation status information, which is used as the callback input parameter in [BlanklessLoadingParam](#blanklessloadingparam23).

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| key | string | No  | No  | Key value that uniquely identifies the page where the frame is interpolated. The value is the same as the key value of [setBlanklessLoadingWithParams](./arkts-apis-webview-WebviewController.md#setblanklessloadingwithparams23).|
| state | [BlanklessFrameInterpolationState](./arkts-apis-webview-e.md#blanklessframeinterpolationstate-23) | No  | No  | Current frame interpolation state.|
| timestamp | number | No  | No  | Time when the frame interpolation is successful, fails, or removed, in ms (UTC time).|
| reason | string | No  | No  | Reason for the frame interpolation failure.|

## BlanklessLoadingParam<sup>23+</sup>

Loading parameters of the White-Screen-Free Loading frame interpolation scheme.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| enable | boolean | No | No | Whether to enable the white-screen-free loading frame interpolation scheme.<br>The value **true** means enabled, and **false** means disabled. |
| duration | number | No  | Yes  | Duration of frame interpolation.<br>The value range is the union of **[200, 2000]** and **{0}**, where **0** indicates that the duration is not specified and the system automatically sets a proper duration.<br>Unit: ms.|
| expirationTime | number | No  | Yes  | Expiration time of the historical frame, in UTC time.<br>**T** indicates the current UTC time. If the expiration time is 30 days, the value is 2592000000 ms. The value range is the union of **(T, T + 2592000000]** and **{0}**. **0** indicates that the expiration time is not specified and the default expiration time (7 days) is used.<br>Unit: ms.|
| callback | Callback<[BlanklessFrameInterpolationInfo](#blanklessframeinterpolationinfo23)> | No | Yes | Callback invoked after frame interpolation succeeds, fails, or is removed.<br>This takes effect only when **enable** is **true**. This parameter is optional. If not set, no operation is performed. |

## HistoryItem

Describes a historical page record.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Type                                  | Read-Only| Optional| Description                        |
| ------------- | -------------------------------------- | ---- | ---- | ---------------------------- |
| icon          | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No  | No  | **PixelMap** object of the icon on the historical page.|
| historyUrl    | string                                 | No  | No  | URL of the historical page.       |
| historyRawUrl | string                                 | No  | No  | Original URL of the historical page.   |
| title         | string                                 | No  | No  | Title of the historical page.          |

## MediaInfo<sup>12+</sup>

Represents a **MediaInfo** object used as a parameter of the [CreateNativeMediaPlayerCallback](./arkts-apis-webview-t.md#createnativemediaplayercallback12) callback. The object contains information about media on the web page. The application may create, based on the information, a player that takes over media playback of the web page.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| embedID | string | No | No  | ID of the `<video>` or `<audio>` element in the web page.|
| mediaType | [MediaType](./arkts-apis-webview-e.md#mediatype12) | No| No| Type of the media.|
| mediaSrcList | [MediaSourceInfo](./arkts-apis-webview-MediaSourceInfo.md)[] | No| No| Source of the media. There may be multiple sources. The application needs to select a supported source to play.|
| surfaceInfo | [NativeMediaPlayerSurfaceInfo](./arkts-apis-webview-NativeMediaPlayerSurfaceInfo.md) | No| No| Surface information used for same-layer rendering.|
| controlsShown | boolean | No | No | Whether the `<video>` or `<audio>` element has the `controls` attribute.<br>The value **true** indicates that it has, and **false** indicates that it does not. |
| controlList | string[] | No| No| Value of the **controlslist** attribute in **\<video>** or **\<audio>**.|
| muted | boolean | No | No | Whether muted playback is required.<br>The value **true** indicates muted playback, and **false** indicates non-muted playback. |
| posterUrl | string | No| No| URL of a poster.|
| preload | [Preload](./arkts-apis-webview-e.md#preload12) | No| No| Whether preloading is required.|
| headers | Record\<string, string\> | No| No| HTTP headers that need to be included in the player's request for media resources.|
| attributes | Record\<string, string\> | No| No| Attributes in **\<video>** or **\<audio>**.|

## RectEvent<sup>12+</sup>

Defines a rectangle.

**System capability**: SystemCapability.Web.Webview.Core

| Name          | Type      | Read-Only| Optional| Description                        |
| -------------- | --------- | ---- | ---- | ---------------------------- |
| x | number | No | No | X-coordinate of the upper left corner of the rectangular area.<br>Unit: px. |
| y | number | No | No | Y-coordinate of the upper left corner of the rectangular area.<br>Unit: px. |
| width | number | No | No | Width of the rectangle.<br>Unit: px. |
| height| number | No | No | Height of the rectangle.<br>Unit: px. |

## WebHttpCookie<sup>23+</sup>

Defines cookie-related fields.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
| ---- | --- | ---- | ---- | ---- |
| samesitePolicy | [WebHttpCookieSameSitePolicy](./arkts-apis-webview-e.md#webhttpcookiesamesitepolicy23) | No| No| Same-site policy of the cookie.|
| expiresDate | string | No | No | Expiration time of the cookie. For details about the time format, see [Date](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Date). If the time string passed in does not conform to this format, the cookie setting does not take effect. |
| name | string | No| No| Name of the cookie.|
| isSessionCookie | boolean | No| No| Whether the cookie is a session cookie.<br>The value **true** indicates that the cookie is a session cookie, and **false** indicates the opposite.|
| value | string | No| No| Value of the cookie.|
| path | string | No| No| Path of the cookie.|
| isHttpOnly | boolean | No | No | Whether the cookie can be accessed only through HTTP requests.<br>The value **true** means the cookie can be accessed only through HTTP, not through JavaScript; **false** means the cookie can be accessed through JavaScript. |
| isSecure | boolean | No | No | Whether the cookie can be sent only through HTTPS.<br>The value **true** means the cookie can be sent only through HTTPS, not through HTTP; **false** means the cookie can be sent through HTTP. |
| domain | string | No| No| Domain names that can access the cookie.|