# Interfaces (Others)

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

## WebStorageOrigin

Provides usage information of the Web SQL Database.

**System capability**: SystemCapability.Web.Webview.Core

| Name  | Type  | Read-Only| Optional| Description|
| ------ | ------ | ---- | ---- | ---- |
| origin | string | No | No| Index of the origin.|
| usage  | number | No | No| Storage usage of the origin.    |
| quota  | number | No | No| Storage quota of the origin.  |

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
| schemeName     | string    | No  | No  | Name of the custom URL scheme. The value can contain a maximum of 32 characters, including lowercase letters, digits, periods (.), plus signs (+), and hyphens (-), and must start with a letter.       |
| isSupportCORS  | boolean   | No  | No  | Whether to support cross-origin resource sharing (CORS).<br>The value **true** means to support cross-origin resource sharing (CORS), and **false** means the opposite.<br>Default value: **true**.   |
| isSupportFetch | boolean   | No  | No  | Whether to support fetch requests.<br>The value **true** means to support fetch requests, and **false** means the opposite.<br>Default value: **true**.          |
| isStandard<sup>12+</sup> | boolean   | No  | Yes  | Whether the scheme is processed as a standard scheme. The standard scheme must comply with the URL normalization and parsing rules defined in section 3.1 of RFC 1738.<br>The value **true** indicates that the scheme is processed as a standard scheme, and **false** indicates the opposite.<br>Default value: **true**.          |
| isLocal<sup>12+</sup> | boolean   | No  | Yes  | Whether the scheme is treated with the same security rules as those applied to file URLs.<br>The value **true** indicates that the scheme is treated with the same security rules as those applied to file URLs, and the value **false** indicates the opposite.<br>Default value: **true**.          |
| isDisplayIsolated<sup>12+</sup> | boolean   | No  | Yes  | Whether the content of the scheme can only be displayed or accessed from other content that uses the same scheme.<br>The value **true** indicates that the content of the scheme can only be displayed or accessed from other content that uses the same scheme, and **false** indicates the opposite.<br>Default value: **true**.          |
| isSecure<sup>12+</sup> | boolean   | No  | Yes  | Whether the scheme is treated with the same security rules as those applied to HTTPS URLs. The value **true** indicates that the scheme is treated with the same security rules as those applied to HTTPS URLs, and **false** indicates the opposite.<br>Default value: **true**.          |
| isCspBypassing<sup>12+</sup> | boolean   | No  | Yes  | Whether the scheme can bypass the content security policy (CSP) checks.<br>The value **true** indicates that the scheme can bypass the content security policy (CSP) checks, and **false** indicates the opposite.<br>Default value: **true**.<br>In most cases, this value should not be set when **isStandard** is set to **true**.        |
| isCodeCacheSupported<sup>12+</sup> | boolean   | No  | Yes  | Whether JavaScript resources loaded with the scheme can be used to create a code cache.<br>The value **true** indicates that JavaScript resources loaded with the scheme can be used to create a code cache, and **false** indicates the opposite.<br>The default value is **false**.        |

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
| responseHeaders   | Array<[WebHeader](#webheader)> | No| No| Array of response headers from the server when a JavaScript file is requested. They include information such as E-Tag or Last-Modified to identify the file version and determine whether the bytecode cache needs to be refreshed.  |

## SnapshotInfo<sup>12+</sup>

Provides information used to obtain a full drawing result.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type|  Read-Only|  Optional| Description|
|------|------|------|------|------|
| id | string | No| Yes| Snapshot ID.|
| size | [SizeOptions](../apis-arkui/arkui-ts/ts-types.md#sizeoptions)  | No| Yes| Size for web rendering. The maximum size is 16000 px x 16000 px. The length unit can be px, vp, or %. The length unit must be the consistent across parameters. The default unit is vp. If the size exceeds the specifications , the maximum size is returned. Example: **width: '100px', height: '200px'** or **width: '20%', height'30%'**. If only digits are written, the unit is vp.|

## SnapshotResult<sup>12+</sup>

Represents a full drawing result.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional|  Description|
|------|------|-- |--|---------|
| id | string | No| Yes| Snapshot ID.|
| status | boolean | No| Yes|  Snapshot status. The value can be **true** (normal) or **false** (failure). If the full drawing result fails to be obtained, the width and height of the returned size are both 0, and the map is empty.|
| size | [SizeOptions](../apis-arkui/arkui-ts/ts-types.md#sizeoptions)   | No| Yes|  Actual size drawn on the web page. The value is of the number type, and the unit is vp.|
| imagePixelMap | [image.PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7) | No| Yes| Full drawing result in image.pixelMap format.|

## OfflineResourceMap<sup>12+</sup>

Implements an **OfflineResourceMap** object, which is used to set up information related to local offline resources that will be injected into memory cache through the [injectOfflineResources](./js-apis-webview-WebviewController.md#injectofflineresources12) API. The ArkWeb engine will generate resource caches based on this information and control the validity period of the cache accordingly.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| urlList | Array\<string\> | No  | No  | List of network addresses of the local offline resources. The first item in the list is used as the resources' origin. If only one network address is provided, this single address is used for the resources' origin. The URL supports only the HTTP and HTTPS protocols and contains a maximum of 2048 characters.     |
| resource | Uint8Array | No  | No  | Content of a local offline resource.     |
| responseHeaders | Array<[WebHeader](#webheader)> | No  | No  | HTTP response headers corresponding to the resources. The **Cache-Control** or **Expires** response header is used to control the validity period of the resource in the memory cache. If neither of the headers is provided, a default validity time of 86400 seconds (1 day) will be applied. The **Content-Type** response header is used to define the MIME type of the resource. For resources of type MODULE_JS, a valid MIME type must be provided. For other types, the MIME type is optional, with no default value. A non-standard MIME type can lead to the resource being invalidated in the memory cache. If a **script** tag on the web page uses the **crossorigin** attribute, the **Cross-Origin** response header must be set in the **responseHeaders** parameter of the API. The value for this header should be **anonymous** or **use-credentials**.     |
| type | [OfflineResourceType](./js-apis-webview-e.md#offlineresourcetype12) | No  | No  | Resource type. Currently, only the JavaScript, image, and CSS types are supported.     |

##  PdfConfiguration<sup>14+</sup>

Specifies the input parameters of **createPdf()**.

> **NOTE**
>
> The number of pixels is calculated as follows: Number of pixels = 96 x Number of inches.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type  | Read-Only| Optional|Description                |
| ----------- | ------ | -----|------|------------------- |
| width                 | number  | No  | No  | Page width.<br>Unit: inch.<br>Recommended value: 8.27 inches of A4 paper width.  |
| height                | number  | No  | No  | Page height.<br>Unit: inch.<br>Recommended value: 11.69 inches of A4 paper height. |
| scale                 | number  | No  | Yes  | Scale multiple.<br>The value range is [0.0, 2.0]. If the value is less than 0.0, set it to **0.0**. If the value is greater than 2.0, set it to **2.0**.<br>Default value: **1.0**|
| marginTop             | number  | No  | No  | Top margin.<br>The value range is [0.0, half of the page height). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| marginBottom          | number  | No  | No  | Bottom margin.<br>The value range is [0.0, half of the page height). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| marginRight           | number  | No  | No  | Right margin.<br>The value range is [0.0, half of the page width). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| marginLeft            | number  | No  | No  | Left margin.<br>The value range is [0.0, half of the page width). If the value is not within the value range, set it to **0.0**.<br>Unit: inch.|
| shouldPrintBackground | boolean | No  | Yes  | Whether to print the background color. The value **true** means to print the background color, and **false** means the opposite.<br>The default value is **false**.                           |

## ScrollOffset<sup>13+</sup>

Represents the current scrolling offset of a web page.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type  | Read-Only| Optional| Description                                                        |
| ---- | ------ | ---- | ---- | ------------------------------------------------------------ |
| x    | number | No  | No  | Horizontal scrolling offset of a web page. The value is the difference between the x-coordinate of the left boundary of the web page and that of the left boundary of the **Web** component.<br>When the web page is scrolled rightwards, the value is negative.<br>When the web page is not scrolled or scrolled leftwards, the value is **0** or positive.<br>Unit: vp|
| y    | number | No  | No  | Vertical scrolling offset of a web page. The value is the difference between the y-coordinate of the upper boundary of the web page and that of the upper boundary of the **Web** component.<br>When the web page is scrolled downwards, the value is negative.<br>When the web page is not scrolled or scrolled upwards, the value is **0** or positive.<br>Unit: vp|

## HitTestValue

Provides the element information of the area being clicked. For the sample code, see [getLastHitTest](./js-apis-webview-WebviewController.md#getlasthittest18).

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- |---- |
| type | [WebHitTestType](./js-apis-webview-e.md#webhittesttype) | No| No| Element type of the area being clicked.|
| extra | string        | No| No|Extra information of the area being clicked. If the area being clicked is an image or a link, the extra information is the URL of the image or link.|
