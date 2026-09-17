# WebviewController

WebviewController is the core controller for various behaviors of the **Web** component, providing extensive functions such as page loading and navigation control, JavaScript interaction, lifecycle management, scroll control, page zoom and content search, message port communication, and cache and certificate management. A WebviewController object can control only one **Web** component, and methods on WebviewController (except static methods) can be called only after the **Web** component is bound to WebviewController.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## accessBackward

```TypeScript
accessBackward(): boolean
```

Checks whether going to the previous page can be performed on the current page.

You can use [getBackForwardEntries](#getbackforwardentries) to obtain the historical information list of the current WebView and use [accessStep](#accessstep) to determine whether to move forward or backward based on the specified number of steps.

> **NOTE:** 
> 
> If [setCustomUserAgent](#setcustomuseragent) is called when the **Web**
> component is loaded for the first time, the value of **accessBackward** may be **false** when there are
> multiple historical entries. That is, there is no backward entry. You are advised to call the
> **setCustomUserAgent** method to set a user agent before using **loadUrl** to load a specific page.
> 
> Causes: When the **Web** component is loaded for the first time, calling
> [setCustomUserAgent](#setcustomuseragent) causes the component to reload and
> retain the initial history entry. Then the new entry replaces the initial history entry and no new history
> entry is generated. As a result, the value of **accessBackward** is false.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** is returned if going to the previous page can be performed on the current page. Otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## accessForward

```TypeScript
accessForward(): boolean
```

Checks whether going to the next page can be performed on the current page.

You can use [getBackForwardEntries](#getbackforwardentries) to obtain the historical information list of the current WebView and use [accessStep](#accessstep) to determine whether to move forward or backward based on the specified number of steps.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** is returned if going to the next page can be performed on the current page; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## accessStep

```TypeScript
accessStep(step: number): boolean
```

Checks whether a specific number of steps forward or backward can be performed on the current page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| step | number | Yes | Number of the steps to take. A positive number means to move forward, and a negative number means to move backward. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether a specific number of steps forward or backward can be performed on the current page.<br>**true** is returned if a specific number of steps forward or backward can be performed on the current page; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## addIntelligentTrackingPreventionBypassingList

```TypeScript
static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

Adds a list of domain names that bypass intelligent tracking prevention.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | Yes | List of domain names that bypass intelligent tracking prevention. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## avoidVisibleViewportBottom

```TypeScript
avoidVisibleViewportBottom(avoidHeight: number): void
```

Sets the bottom avoidance height of the visible viewport on the web page.

> **NOTE:** 
> 
> - The valid value range of **avoidHeight** is [0, height of the **Web** component]. Values outside this range are adjusted to the nearest boundary.
> 
> - When a non-zero value is specified for **avoidHeight**, the position and size of the **Web** component remain unchanged, but the visible viewport shift upwards by the specified height, lifting the web page content by the
> **avoidHeight**. This API is used to customize the avoidance area at the bottom of a web page. It is not
> recommended that this API be used when the editable area of the web page is tapped to pull up the keyboard. If
> this API is used in this scenario, the keyboard avoidance mode is set to **OVERLAYS_CONTENT**.
> 
> - When the height of this API is set to **0**, the web page content can be restored, and the keyboard avoidance mode is specified by keyboardAvoidMode().

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| avoidHeight | number | Yes | Bottom avoidance height of the visible viewport on the web page.<br>Unit: vp. <br>Value range: [0, height of the **Web** component] <br>If the value is less than 0, the value **0** is used. If the value is greater than the height of the **Web** component, the height of the **Web** component is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This functionality is not supported. |

## backOrForward

```TypeScript
backOrForward(step: number): void
```

Performs a specific number of steps forward or backward on the current page based on the history stack. No redirection will be performed if the corresponding page does not exist in the history stack.

Because the previously loaded web pages are used for the operation, no page reloading is involved.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| step | number | Yes | Number of the steps to take. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## backward

```TypeScript
backward(): void
```

Moves to the previous page based on the history stack. This API is generally used together with [accessBackward](#accessbackward).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## clearBlanklessLoadingCache

```TypeScript
static clearBlanklessLoadingCache(keys?: Array<string>) : void
```

Clears the blankless loading cache of the page with a specified key value.

In an applet or web application, when the content changes significantly during page loading, an obvious scene change may occur. If you are concerned about this change, you can use this API to clear the page cache.

> **NOTE:** 
> 
> - After the page is cleared, the optimization effect appears when the page is loaded for the third time.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | No | Key value list on the pages using the blankless optimization solution. The **key** value has been specified in [getBlanklessInfoWithKey](#getblanklessinfowithkey).<br>Default value: key list of all pages cached by the blankless optimization solution.<br>Valid value range: The key length cannot exceed 2048 characters, and the number of keys must be less than or equal to 100. The key value is the same as that input to the **Web** component during page loading.<br>Invalid value setting behavior: If **undefined** or **null** is passed, error code **401** is thrown. If the key length exceeds 2048, the key does not take effect. If the key length exceeds 100, the first 100 values are used. If the key is empty, the default value is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) |  |

## clearClientAuthenticationCache

```TypeScript
clearClientAuthenticationCache(): void
```

Clears the user operation corresponding to the client certificate request event recorded by the **Web** component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## clearHistory

```TypeScript
clearHistory(): void
```

Clears the browsing history. You are not advised to call **clearHistory()** in **onErrorReceive()** and **onPageBegin()**. Otherwise, abnormal exit occurs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## clearHostIP

```TypeScript
static clearHostIP(hostName: string): void
```

Clears the IP address of a specified host after domain name resolution.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hostName | string | Yes | Domain name of the host whose DNS records are to be cleared. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## clearIntelligentTrackingPreventionBypassingList

```TypeScript
static clearIntelligentTrackingPreventionBypassingList(): void
```

Deletes all domain names from the list of domain names added through the **addIntelligentTrackingPreventionBypassingList** API.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## clearMatches

```TypeScript
clearMatches(): void
```

Clears the matches found through [searchAllAsync](#searchallasync).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## clearPrefetchedResource

```TypeScript
static clearPrefetchedResource(cacheKeyList: Array<string>): void
```

Clears the cache of prefetched resources based on the specified cache key list. The cache key in the input parameter must be the prefetched resource cache key specified by [prefetchResource](#prefetchresource).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cacheKeyList | Array&lt;string&gt; | Yes | Key used to query the cache of prefetched resources. The value can contain only letters and digits. If this parameter is not passed or is left empty, **url** is used by default. |

## clearServiceWorkerWebSchemeHandler

```TypeScript
static clearServiceWorkerWebSchemeHandler(): void
```

Clears all WebSchemeHandlers that are set in the application and used to intercept ServiceWorker.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## clearSslCache

```TypeScript
clearSslCache(): void
```

Clears the user operation corresponding to the SSL certificate error event recorded by the **Web** component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## clearWebSchemeHandler

```TypeScript
clearWebSchemeHandler(): void
```

Clears all WebSchemeHandlers set for the **Web** component.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## closeAllMediaPresentations

```TypeScript
closeAllMediaPresentations(): void
```

Closes all full-screen videos on a web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## closeCamera

```TypeScript
closeCamera(): void
```

Disables the camera capture of the current web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## constructor

```TypeScript
constructor(webTag?: string)
```

Constructs a **WebviewController** object.

> **NOTE:** 
> 
> - No parameter: new webview.WebviewController() indicates an empty constructor. No parameter is required when the C API is not used.
> 
> - Parameter is a valid string: new webview.WebviewController("xxx"), used for developers to distinguish multiple instances and call methods under the corresponding instance.
> 
> - Empty parameter: new webview.WebviewController("") or new webview.WebviewController(undefined). In this scenario, the parameter is meaningless and cannot distinguish multiple instances. **undefined** is returned directly, and developers need to check whether the return value is normal.
> 
> After the **Web** component is destroyed, it is unbound from WebViewController. Subsequently, calling non-
> static methods of WebviewController will throw a
> [17100001](../../../reference/apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component)
> exception. Pay attention to the call timing and catch exceptions to prevent abnormal process exit.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| webTag | string | No | Name of the **Web** component. |

## createPdf

```TypeScript
createPdf(configuration: PdfConfiguration, callback: AsyncCallback<PdfData>): void
```

Obtains the data stream of a specified web page using an asynchronous callback.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configuration | [PdfConfiguration](arkts-arkweb-webview-pdfconfiguration-i.md) | Yes | Parameters required for creating a PDF file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PdfData](arkts-arkweb-webview-pdfdata-c.md)&gt; | Yes | Callback used to return the data stream of an online PDF file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid input parameter. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## createPdf

```TypeScript
createPdf(configuration: PdfConfiguration): Promise<PdfData>
```

Obtains the data stream of a specified web page using a promise.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configuration | [PdfConfiguration](arkts-arkweb-webview-pdfconfiguration-i.md) | Yes | Parameters required for creating a PDF file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PdfData](arkts-arkweb-webview-pdfdata-c.md)&gt; | Promise used to return the result. It returns a web page PDF data stream (a PdfData object containing PDF binary data represented as an ArrayBuffer). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid input parameter. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## createWebMessagePorts

```TypeScript
createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>
```

Creates web message ports.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isExtentionType | boolean | No | Whether to use the extended interface.<br>The value **true** means to use the extended interface, and **false** means the opposite. <br>Default value: **false**. <br>If **undefined** or **null** is passed, error code **401** will be thrown.<br>**Since:** 10 |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[WebMessagePort](arkts-arkweb-webview-webmessageport-i.md)&gt; | List of web message ports. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed.<br>**Applicable version:** 10 and later |

## createWebPrintDocumentAdapter

```TypeScript
createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter
```

Creates a **PrintDocumentAdapter** instance to provide content for printing.

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobName | string | Yes | Name of the file to print. |

**Return value:**

| Type | Description |
| --- | --- |
| [print.PrintDocumentAdapter](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-print-printdocumentadapter-i.md) | Adapter for the print document, which controls the print behavior and print task. It can print the current web page content through the print service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>): void
```

Grants the cross-domain request and fetch request permissions for custom protocol URLs to the web kernel. When the Web performs a cross-domain fetch of a custom protocol URL, the fetch request can be intercepted by the [onInterceptRequest](../arkts-components/arkts-arkweb-web-comp-attribute.md#oninterceptrequest) event API, so that developers can further process the request. It is recommended to call this API before any **Web** component is initialized.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| schemes | Array&lt;[WebCustomScheme](arkts-arkweb-webview-webcustomscheme-i.md)&gt; | Yes | Array of up to 10 custom schemes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100020](../errorcode-webview.md#17100020-failed-to-register-custom-schemes) | Failed to register custom schemes.<br>**Applicable version:** 12 and later |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void
```

Grants the cross-domain request and fetch request permissions for custom protocol URLs to the web kernel. When the Web performs a cross-domain fetch of a custom protocol URL, the fetch request can be intercepted by the [onInterceptRequest](../arkts-components/arkts-arkweb-web-comp-attribute.md#oninterceptrequest) event API, so that developers can further process the request. It is recommended to call this API before any **Web** component is initialized.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| schemes | Array&lt;[WebCustomScheme](arkts-arkweb-webview-webcustomscheme-i.md)&gt; | Yes | Array of up to 10 custom schemes. |
| lazyInitWebEngine | boolean | Yes | Whether to skip WebEngine initialization in the API.<br>The value **true** means to skip the WebEngine initialization and store the registered schemes temporarily. When the WebEngine is initialized, the schemes are transferred to the WebEngine. The value false means to initialize the WebEngine automatically in the API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100020](../errorcode-webview.md#17100020-failed-to-register-custom-schemes) | Failed to register custom schemes. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. The length of the schemes array is greater than 10. 2. The character length of the scheme is greater than 32. 3. The character in the scheme is not within the allowed range of lowercase English letters, numbers, and the symbols ".", "+", "-". |

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string): void
```

Deletes a JavaScript object with the specified name on the application side that is registered with the window using [registerJavaScriptProxy](#registerjavascriptproxy) or [javaScriptProxy](../arkts-components/arkts-arkweb-web-comp-attribute.md#javascriptproxy). The deletion takes effect after the page is reloaded.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the registered JavaScript object, which can be used to invoke the corresponding object on the application side from the web side. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100008](../errorcode-webview.md#17100008-deleting-a-javascriptproxy-that-does-not-exist) | Failed to delete JavaScriptProxy because it does not exist. |

## enableAdsBlock

```TypeScript
enableAdsBlock(enable: boolean): void
```

Enables ad blocking.

> **NOTE:** 
> 
> - The ad blocking feature works only for the release-type application, not the debug-type application.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable ad blocking.<br>The value **true** means to enable ad blocking, and **false** means the opposite. <br>Default value: **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Parameter string is too long. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## enableAdvancedSecurityMode

```TypeScript
static enableAdvancedSecurityMode(securityParams: SecurityParams): void
```

Disables specific web engine capabilities by configuring security feature options to reduce the attack surface. Typical use cases include: apps with high security requirements (such as financial and government apps) should enable advanced security mode to disable unnecessary web engine capabilities.

> **NOTE:** 
> 
> - This API is a global static API. It only needs to be called once during the entire app lifecycle and does not need to be called repeatedly.
> 
> - It must be called before [initializeWebEngine()](#initializewebengine).Otherwise, the setting does not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| securityParams | [SecurityParams](arkts-arkweb-webview-securityparams-i.md) | Yes | Security feature option configuration. |

## enableBackForwardCache

```TypeScript
static enableBackForwardCache(features: BackForwardCacheSupportedFeatures): void
```

Enables the back-forward cache of a **Web** component. You can specify whether to add a specific page to the back -forward cache.

This API must be called before [initializeWebEngine()](#initializewebengine) initializes the kernel.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| features | [BackForwardCacheSupportedFeatures](arkts-arkweb-webview-backforwardcachesupportedfeatures-c.md) | Yes | Features of the pages, which allow them to be added to the back-forward cache. |

## enableIntelligentTrackingPrevention

```TypeScript
enableIntelligentTrackingPrevention(enable: boolean): void
```

Enables intelligent tracking prevention.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable intelligent tracking prevention.<br>The value **true** means to enable intelligent tracking prevention, and **false** means the opposite. <br>Default value: **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## enablePrivateNetworkAccess

```TypeScript
static enablePrivateNetworkAccess(enable: boolean): void
```

Sets the private network access check feature.

After this feature is enabled, the **Web** component performs CORS preflight on private network requests (such as requests for accessing local servers or intranet resources). It sends an OPTIONS preflight request to obtain explicit authorization from the target server and then transmits the actual data. Disabling this feature will skip the security check.

> **NOTE:** 
> 
> The private network access check feature currently takes effect mainly for Web Worker scenarios.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the private network access check feature. The value **true** means to enable the private network access check feature, and **false** means the opposite. |

## enableSafeBrowsing

```TypeScript
enableSafeBrowsing(enable: boolean): void
```

Enables the safe browsing feature. This feature is forcibly enabled and cannot be disabled for identified untrusted websites.

By default, this feature does not take effect. OpenHarmony provides only the malicious website blocking web UI. The website risk detection and web UI display features are implemented by the vendor. You are advised to listen for [DidStartNavigation](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/content/public/browser/web_contents_observer.h) and [DidRedirectNavigation](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/content/public/browser/web_contents_observer.h) in **WebContentsObserver** for detection.

> **NOTE:** 
> 
> This API does not take effect.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the safe browsing feature.<br>The value **true** means to enable the safe browsing feature, and **false** means the opposite. <br>Default value: **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## enableWholeWebPageDrawing

```TypeScript
static enableWholeWebPageDrawing(): void
```

Enables the full drawing capability for the web page. This API works only during **Web** component initialization.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## executeAIPageCommand

```TypeScript
executeAIPageCommand(command: string): Promise<string>
```

Executes `AIPageCommand` asynchronously. This API uses a promise to return the result. The command type and command parameters are specified through the `command` parameter in JSON string format.

> **NOTE:** 
> 
> - The return format varies for different commands. For details, see [AIPageCommand](../../../reference/apis-arkweb/arkts-apis-webview-AIPageCommand.md) and [AIPageInteraction](../../../reference/apis-arkweb/arkts-apis-webview-AIPageInteraction.md).
> 
> - When a command cannot be dispatched or has no result to return, the promise may return an empty string.
> 
> - When the return value is not empty, it is a JSON string. The app can parse it with `JSON.parse` before use.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | string | Yes | Command parameter in JSON format. The parameter format varies for different commands. For query commands, see [AIPageCommand](../../../reference/apis-arkweb/arkts-apis-webview-AIPageCommand.md). For interaction commands, see [AIPageInteraction](../../../reference/apis-arkweb/arkts-apis-webview-AIPageInteraction.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the command execution result in JSON format. The return format varies for different commands. When a command cannot be dispatched or has no return value, an empty string is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100024](../errorcode-webview.md#17100024-aipagecommand-format-error) | Command format error. The command parameter does not conform to the JSON format requirements. |

## forward

```TypeScript
forward(): void
```

Moves forward by one page in the history stack. Generally used together with [accessForward](#accessforward).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getActiveWebEngineVersion

```TypeScript
static getActiveWebEngineVersion(): ArkWebEngineVersion
```

Obtains the current ArkWeb kernel version.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ArkWebEngineVersion](arkts-arkweb-webview-arkwebengineversion-e.md) | The ArkWeb kernel version defined by [ArkWebEngineVersion](arkts-arkweb-webview-arkwebengineversion-e.md). |

## getAttachState

```TypeScript
getAttachState(): ControllerAttachState
```

Checks whether the current **WebViewController** is bound to a **Web** component.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md) | Attach status of **WebViewController** and the **Web** component. |

## getBackForwardEntries

```TypeScript
getBackForwardEntries(): BackForwardList
```

Obtains the historical information list of the current WebView.

> **NOTE:** 
> 
> onLoadIntercept is triggered when the loading starts. At this time, no
> historical node is generated. Therefore, the historical stack obtained by calling **getBackForwardEntries** in
> **onLoadIntercept** does not include the page that is being loaded.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [BackForwardList](arkts-arkweb-webview-backforwardlist-i.md) | The history list of the current WebView. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getBlanklessInfoWithKey

```TypeScript
getBlanklessInfoWithKey(key: string) : BlanklessInfo
```

Obtains the prediction information about blankless loading (for details, see [BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md)) and starts to generate the loading transition frame. The application determines whether to enable blankless loading based on the information. This API must be used together with the [setBlanklessLoadingWithKey](#setblanklessloadingwithkey) API before the page loading API is triggered or in **onLoadIntercept**, and after the **WebViewController** is bound to the **Web** component.

> **NOTE:** 
> 
> - The default size of the persistent cache capacity is 30 MB (about 30 pages). You can set the cache capacity by calling [setBlanklessLoadingCacheCapacity](#setblanklessloadingcachecapacity). For details, see the description of this API. When the maximum capacity is exceeded, the cache is updated based on the Least Recently Used (LRU) mechanism. The persistent cache data that has been stored for more than seven days is automatically cleared. After the cache is cleared, the optimization effect appears when the page is loaded for the third time.
> 
> - If the snapshot similarity (**similarity** in [BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md))is extremely low, check whether the **key** value is correct.
> 
> - After this API is called, page loading snapshot detection and transition frame generation calculation are enabled, which generates certain resource overhead.
> 
> - Blankless loading consumes certain resources, which depends on the resolution of the **Web** component. When the width and height of the resolution are respectively **w** and **h**, the peak memory usage increases by about **12 × w × h** B in the page-opening phase. After the page is opened, the memory is reclaimed, which does not affect the stable memory usage. When the size of the solid-state application cache is increased, the increased cache of each page is about **w × h/10** B and the cache is located in the application cache.
> 
> - Add the **ohos.permission.INTERNET** and **ohos.permission.GET_NETWORK_INFO** permissions to **module.json5**. For details, see [Declaring Permissions in the Configuration File](../../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key value that uniquely identifies the page.<br>The value cannot be empty and can contain a maximum of 2048 characters.<br>Invalid values do not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md) | Prediction information about blankless loading, including the first screen similarity and first screen loading duration. The application determines whether to enable blankless loading based on the prediction information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) |  |

## getCertificate

```TypeScript
getCertificate(): Promise<Array<cert.X509Cert>>
```

Obtains the certificate information of this website. When the **Web** component is used to load an HTTPS website, SSL certificate verification is performed. This API uses a promise to return the [X.509 certificate](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-x509cert-i.md) of the current website.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[cert.X509Cert](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-x509cert-i.md)&gt;&gt; | Promise used to obtain the X.509 certificate array of the current HTTPS website. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a web component. |

## getCertificate

```TypeScript
getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void
```

Obtains the certificate information of the current website. When the **Web** component is used to load an HTTPS website, SSL certificate verification is performed. This API uses an asynchronous callback to return the X.509 certificate (for the X509Cert certificate type definition, see [X509Cert](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-x509cert-i.md)) of the current website, so that developers can display the website certificate information.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[cert.X509Cert](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-x509cert-i.md)&gt;&gt; | Yes | Callback used to obtain the X.509 certificate array of the current website. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a web component. |

## getCustomUserAgent

```TypeScript
getCustomUserAgent(): string
```

Obtains a custom user agent.

For details about the default **User-Agent**, see [Developing User-Agent](../../../web/web-default-userAgent.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Information about the custom user agent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getDefaultUserAgent

```TypeScript
static getDefaultUserAgent(): string
```

Obtains the default user agent.

This API can be called only in the UI thread.

For details about the default **User-Agent**, see [Developing User-Agent](../../../web/web-default-userAgent.md).

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Default **User-Agent** string of ArkWeb. |

## getErrorPageEnabled

```TypeScript
getErrorPageEnabled(): boolean
```

Queries whether the default error page is enabled.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the default error page is enabled.<br>The value true indicates that the default error page is enabled, and false indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getFavicon

```TypeScript
getFavicon(): image.PixelMap
```

Obtains the favicon of this page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | **PixelMap** object of the favicon of the page. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getHitTest

```TypeScript
getHitTest(): WebHitTestType
```

Obtains the element type of the area being clicked.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getLastHitTest](#getlasthittest)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebHitTestType](arkts-arkweb-webview-webhittesttype-e.md) | Element type of the area being clicked. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getHitTestValue

```TypeScript
getHitTestValue(): HitTestValue
```

Obtains the element information of the area being clicked.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getLastHitTest](#getlasthittest)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [HitTestValue](arkts-arkweb-webview-hittestvalue-i.md) | Element information of the area being clicked. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getLastHitTest

```TypeScript
getLastHitTest(): HitTestValue
```

Obtains the element information of the area being clicked last time.

**Since:** 18

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [HitTestValue](arkts-arkweb-webview-hittestvalue-i.md) | Element information of the area being clicked. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getLastJavascriptProxyCallingFrameUrl

```TypeScript
getLastJavascriptProxyCallingFrameUrl(): string
```

Injects a JavaScript object into the window object through [registerJavaScriptProxy](#registerjavascriptproxy) or [javaScriptProxy](../arkts-components/arkts-arkweb-web-comp-attribute.md#javascriptproxy). This API obtains the URL of the frame that last called the injected object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL of the frame of the last injected object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getMediaPlaybackState

```TypeScript
getMediaPlaybackState(): MediaPlaybackState
```

Queries the audio and video playback status of the current web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [MediaPlaybackState](arkts-arkweb-webview-mediaplaybackstate-e.md) | Playback control status of the current web page. The options are **NONE**, **PLAYING**, **PAUSED**, and **STOPPED**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getOriginalUrl

```TypeScript
getOriginalUrl(): string
```

Obtains the original URL of the current page.

Risk warning: If you want to obtain the URL for JavaScriptProxy communication API authentication, use [getLastJavascriptProxyCallingFrameUrl&lt;sup&gt;12+&lt;/sup&gt;](#getlastjavascriptproxycallingframeurl).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Original URL address of the current page. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getPageHeight

```TypeScript
getPageHeight(): number
```

Obtains the height of this web page. For details, see [Obtaining the Web Page Content Height](../../../web/web-getpage-height.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Height of the current web page. Unit: vp |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getPageOffset

```TypeScript
getPageOffset(): ScrollOffset
```

Obtains the current scrolling offset of the web page (excluding the over-scrolling offset).

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ScrollOffset](arkts-arkweb-webview-scrolloffset-i.md) | Current scroll offset of the web page (excluding over-scroll offset), which contains x and y coordinates, in vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

## getPrintBackground

```TypeScript
getPrintBackground(): boolean
```

Obtains whether the web page background is printed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether to print the web page background.<br>The value **true** means to print the web page background; **false** means not to print the web page background. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getProgress

```TypeScript
getProgress() : number
```

Obtains the loading progress of the current web page.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Loading progress of the current page. The value range is [0, 100]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

## getRenderProcessMode

```TypeScript
static getRenderProcessMode(): RenderProcessMode
```

Obtains the ArkWeb render subprocess mode.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [RenderProcessMode](arkts-arkweb-webview-renderprocessmode-e.md) | Render subprocess mode.<br>You can call **getRenderProcessMode()** to obtain the ArkWeb child render process mode of the current device. The enumerated value **0** indicates the single child render process mode, and **1** indicates the multi-child render process mode. <br>If the obtained value is not an enumerated value of **RenderProcessMode**, the multi-render subprocess mode is used by default. |

## getScrollable

```TypeScript
getScrollable(): boolean
```

Obtains whether this web page is scrollable.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether this web page is scrollable.<br>The value **true** indicates that this web page is scrollable, and **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getScrollOffset

```TypeScript
getScrollOffset(): ScrollOffset
```

Obtains the current scrolling offset (including the over-scrolling offset) of the web page.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ScrollOffset](arkts-arkweb-webview-scrolloffset-i.md) | Current scroll offset of the web page (including the overscroll offset), containing x and y coordinates, in vp. |

## getSecurityLevel

```TypeScript
getSecurityLevel(): SecurityLevel
```

Obtains the security level of this web page.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [SecurityLevel](arkts-arkweb-webview-securitylevel-e.md) | Security level of the web page. The value can be **NONE**, **SECURE**, **WARNING**, or **DANGEROUS**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getSiteIsolationMode

```TypeScript
static getSiteIsolationMode(): SiteIsolationMode
```

Queries the currently effective site isolation mode.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [SiteIsolationMode](arkts-arkweb-webview-siteisolationmode-e.md) | Site isolation mode.<br>getSiteIsolationMode() queries the currently effective site isolation mode. |

## getSubframeErrorPageEnabled

```TypeScript
getSubframeErrorPageEnabled(): boolean
```

Queries whether the subframe error page feature is enabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether the subframe error page feature is enabled.<br>- **true**: The subframe error page feature is enabled (that is, both **enable** and **includeSubframe** are **true**). <br>- **false**: The subframe error page feature is not enabled (including the case where the error page feature is not enabled, or the error page feature is enabled but the subframe error page feature is not enabled). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getSurfaceId

```TypeScript
getSurfaceId(): string
```

Obtains the ID of the surface corresponding to ArkWeb. The ID can be used to capture a screenshot of the web page.

> **NOTE:** 
> 
> This API is valid only when the **Web** component rendering mode is **ASYNC_RENDER**. The value of
> **getSurfaceId** can be obtained only after the **Web** component is initialized.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the surface held by ArkWeb. |

## getTitle

```TypeScript
getTitle(): string
```

Obtains the title of the current web page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Title of the current web page. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getUrl

```TypeScript
getUrl(): string
```

Obtains the URL of the current page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL address of the current page. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getUserAgent

```TypeScript
getUserAgent(): string
```

Obtains the default user agent of this web page.

For details about the default **User-Agent**, see [Developing User-Agent](../../../web/web-default-userAgent.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Default user agent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## getUserAgentClientHintsEnabled

```TypeScript
static getUserAgentClientHintsEnabled(): boolean
```

Queries whether the User-Agent Client Hints feature is currently enabled.

**Since:** 24

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the User-Agent Client Hints feature is enabled. The value **true** indicates enabled, and **false** indicates disabled. |

## getUserAgentMetadata

```TypeScript
getUserAgentMetadata(userAgent: string): UserAgentMetadata
```

Obtains the UserAgentMetadata information of a user agent.

**Since:** 24

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userAgent | string | Yes | Information about the custom user agent. You can use [getUserAgent](#getuseragent) to obtain the current default user agent. |

**Return value:**

| Type | Description |
| --- | --- |
| [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md) | [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md) corresponding to userAgent. |

## getWebId

```TypeScript
getWebId(): number
```

Obtains the index value of the **Web** component, which can be used for managing multiple **Web** components.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the Web component. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(): Promise<boolean>
```

Checks whether this page contains images. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result.<br> The value **true** indicates that this page contains images, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(callback: AsyncCallback<boolean>): void
```

Checks whether this page contains images. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result.<br> The value **true** indicates that this page contains images, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## initializeWebEngine

```TypeScript
static initializeWebEngine(): void
```

Loads the dynamic library file of the web engine through this API before the **Web** component is initialized, so as to improve startup performance. It also automatically preconnects to frequently visited websites in history.

> **NOTE:** 
> 
> - **initializeWebEngine** cannot be called in an asynchronous thread. Otherwise, the system breaks down.
> 
> - **initializeWebEngine** takes effect globally and needs to be called only once in an application lifecycle.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## injectOfflineResources

```TypeScript
injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void
```

Injects local offline resources to the memory cache to improve the initial page startup speed.

Resources in the memory cache are automatically managed by the ArkWeb engine. When the injected resources are excessive and cause significant memory pressure, the engine will automatically release unused resources. It is advisable to avoid injecting a large number of resources into the memory cache.

Under normal circumstances, the validity period of the resources is controlled by the provided Cache-Control or Expires response header, with a default validity period of 86,400 seconds, which is one day.

The MIME type of the resources is configured through the provided Content-Type response header. The Content-Type must comply with standards; otherwise, the resources cannot be used correctly. For resources of type MODULE_JS, a valid MIME type must be provided. For other types, the MIME type is optional.

Resources injected in this mode can be loaded only through HTML tags. If a **script** tag on the web page uses the **crossorigin** attribute, the **Cross-Origin** response header must be set in the **responseHeaders** parameter of the API. The value for this header should be **anonymous** or **use-credentials**.

After **webview.WebviewController.SetRenderProcessMode(webview.RenderProcessMode.MULTIPLE)** is called, the application starts the multi-rendering process mode. This API does not take effect in this scenario.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceMaps | Array&lt;[OfflineResourceMap](arkts-arkweb-webview-offlineresourcemap-i.md)&gt; | Yes | Configuration object for local offline resources. A maximum of 30 resources can be injected in a single call, with a maximum size of 10 MB per individual resource. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**Applicable version:** 22 and later |

## isActiveWebEngineEvergreen

```TypeScript
static isActiveWebEngineEvergreen(): boolean
```

Checks whether the system is using the evergreen kernel, that is, the latest kernel.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the system is using the evergreen kernel. If the system is using the evergreen kernel, **true** is returned. Otherwise, **false** is returned. |

## isAdsBlockEnabled

```TypeScript
isAdsBlockEnabled(): boolean
```

Checks whether ad blocking is enabled.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** is returned if ad blocking is enabled; otherwise, **false** is returned.<br>Default value: **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## isAdsBlockEnabledForCurPage

```TypeScript
isAdsBlockEnabledForCurPage(): boolean
```

Checks whether ad blocking is enabled on this web page.

After ads blocking is enabled for the **Web** component, this feature is enabled for all web pages by default. You can call [addAdsBlockDisallowedList](arkts-arkweb-webview-adsblockmanager-c.md#addadsblockdisallowedlist) to disable the feature for specific domains.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** is returned if ad blocking is enabled; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## isAutoPreconnectEnabled

```TypeScript
static isAutoPreconnectEnabled(): boolean
```

Queries the automatic preconnection status of the Web kernel.

If the automatic preconnection status of the Web kernel is not set by using [setAutoPreconnect](#setautopreconnect), automatic preconnection is enabled by default, and **true** is returned.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether auto preconnection is enabled for the Web kernel. The value **true** indicates that the private network access check feature is enabled, and **false** indicates the opposite. |

## isIncognitoMode

```TypeScript
isIncognitoMode(): boolean
```

Checks whether this Webview is in incognito mode.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the Webview is in incognito mode.<br>The value **true** indicates that incognito mode is enabled for WebView, and **false** indicates the opposite. <br>Default value: **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## isIntelligentTrackingPreventionEnabled

```TypeScript
isIntelligentTrackingPreventionEnabled(): boolean
```

Obtains whether the **Web** component has enabled intelligent tracking prevention.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the Web component has enabled the smart anti-tracking feature.<br>The value **true** indicates that the smart anti-tracking feature is enabled, and **false** indicates that it is not enabled. <br>Default value: **false** |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## isPrivateNetworkAccessEnabled

```TypeScript
static isPrivateNetworkAccessEnabled(): boolean
```

Obtains whether the private network access check feature is enabled for the **Web** component.

> **NOTE:** 
> 
> The private network access check feature currently takes effect mainly for Web Worker scenarios.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the private network access check feature is enabled for the **Web** component. The value **true** indicates that the private network access check feature is enabled, and **false** indicates the opposite. |

## isSafeBrowsingEnabled

```TypeScript
isSafeBrowsingEnabled(): boolean
```

Checks whether the safe browsing feature is enabled for this web page.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the safe browsing feature is enabled for this web page.<br>The value **true** indicates that the safe browsing feature is enabled, and **false** indicates the opposite. <br>Default value: **false**. |

## loadData

```TypeScript
loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void
```

Loads specified data.

When both **baseUrl** and **historyUrl** are empty:

If **encoding** is not base64 (including null values), ASCII encoding is used for octets within the secure URL character range, and the standard %xx hexadecimal encoding of the URL is used for octets outside the secure URL character range.

**data** must be encoded using Base64 or any hash (#) in the content must be encoded as %23. Otherwise, hash (#) is considered as the end of the content, and the remaining text is used as the document fragment identifier.

> **NOTE:** 
> 
> - To load a local image, you can assign a space to either **baseUrl** or **historyUrl**. For details, see the sample code.
> 
> - In the scenario of loading a local image, **baseUrl** and **historyUrl** cannot be both empty. Otherwise, the image cannot be loaded.
> 
> - If the rich text in HTML contains special characters such as hash (#), you are advised to set the values of
> **baseUrl** and **historyUrl** to spaces.
> 
> - To load texts, you need to set `&lt;meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8"&gt;` to avoid inconsistent font sizes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | String obtained after being base64 or URL encoded. |
| mimeType | string | Yes | Media type (MIME). |
| encoding | string | Yes | Encoding type, which can be base64 or URL. |
| baseUrl | string | No | URL (HTTP/HTTPS/data compliant), which is assigned by the **Web** component to **window.origin**. If a large number of HTML files need to be loaded, set this parameter to **data**.<br>If **undefined** or **null** is passed, error code **401** will be thrown. |
| historyUrl | string | No | URL used for historical records. If this parameter is not empty, historical records are managed based on this URL. This parameter is invalid when **baseUrl** is left empty.<br>If **undefined** or **null** is passed, error code **401** will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2048.<br>**Applicable version:** 9 - 10 |

## loadUrl

```TypeScript
loadUrl(url: string | Resource, headers?: Array<WebHeader>): void
```

Loads a specified URL.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string &#124; Resource | Yes | URL to load. |
| headers | Array&lt;[WebHeader](arkts-arkweb-webview-webheader-i.md)&gt; | No | Additional HTTP request header of the URL.<br>Default value: **[]**. <br>If **undefined** or **null** is passed, error code **401** will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid. |
| [17100003](../errorcode-webview.md#17100003-incorrect-resource-path) | Invalid resource path or file type. |

## off('controllerAttachStateChange')

```TypeScript
off(type: 'controllerAttachStateChange', callback?: Callback<ControllerAttachState>): void
```

Deregisters the attach state event of **WebViewController**. After the deregistration, callback notifications will not be received.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controllerAttachStateChange' | Yes | Attach state event of **WebViewController**, whose value is fixed to **controllerAttachStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md)&gt; | No | Callback triggered when the attach state of **WebViewController** changes. By default, this parameter is left blank. If **Callback** is specified, only the specified callback is deregistered. Otherwise, all callbacks will be deregistered.<br>If **null** or **undefined** is passed, error code **401** is thrown. |

## on('controllerAttachStateChange')

```TypeScript
on(type: 'controllerAttachStateChange', callback: Callback<ControllerAttachState>): void
```

Registers the attach state event of **WebViewController**, which obtains the attach state change notification through a callback.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controllerAttachStateChange' | Yes | Attach state event of **WebViewController**, whose value is fixed to **controllerAttachStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md)&gt; | Yes | Callback triggered when the attach state of **WebViewController** changes. |

## onActive

```TypeScript
onActive(): void
```

Called when the **Web** component enters the active state.

The application can interact with the user while in the active foreground state, and it remains in this state until the focus is moved away from it due to some event (for example, an incoming call is received or the device screen is turned off).

If the page was previously in the inactive state, the event listener registered through document.addEventListener ('visibilitychange',...) in the H5 page will be triggered, and document.visibilityState changes from "hidden" to"visible".

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## onCreateNativeMediaPlayer

```TypeScript
onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void
```

Registers a callback function. After [enableNativeMediaPlayer](../arkts-components/arkts-arkweb-web-comp-attribute.md#enablenativemediaplayer) is used to enable the app to take over web page media playback, the registered callback function is triggered when media is played on the web page.

If the application does not take over media playback on the web page, this callback is not invoked.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md) | Yes | Callback when the application takes over media playback on the web page. |

## onInactive

```TypeScript
onInactive(): void
```

Called when the **Web** component enters the inactive state. You can implement the behavior to perform after the application loses focus.

When this API is called, any content that can be safely paused, such as animations and geographical locations, is paused as much as possible. However, the JavaScript is not paused. To pause the JavaScript globally, use [pauseAllTimers](#pausealltimers). To reactivate the **Web** component, use [onActive](#onactive).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## pageDown

```TypeScript
pageDown(bottom: boolean): void
```

Scrolls the page down by half the viewport or jumps to the bottom of the page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bottom | boolean | Yes | Whether to jump to the bottom of the page.<br>The value **false** means to scroll the page down by half the viewport, and the value **true** means to jump to the bottom of the page. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## pageUp

```TypeScript
pageUp(top: boolean): void
```

Scrolls the page up by half the viewport or jumps to the top of the page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| top | boolean | Yes | Whether to jump to the top of the page.<br>The value **false** means to scroll the page up by half the viewport, and the value **true** means to jump to the top of the page. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## pauseAllMedia

```TypeScript
pauseAllMedia(): void
```

Pauses all audio and video on a web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## pauseAllTimers

```TypeScript
static pauseAllTimers(): void
```

Pauses all WebView timers. While the timers are paused, timer operations such as setInterval and setTimeout in the web page are suspended. It is recommended to pause timers when the app enters the background and resume them when the app returns to the foreground, so as to save resources. This API can be used in pair with [resumeAllTimers](#resumealltimers)() to avoid timer state confusion.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## pauseMicrophone

```TypeScript
pauseMicrophone(): void
```

Pauses microphone capture on the current web page.

> **NOTE:** 
> 
> Differences from resumeMicrophone and stopMicrophone:
> 
> pauseMicrophone only pauses microphone capture and can be restored through resumeMicrophone; stopMicrophone
> stops capture and releases resources.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## postMessage

```TypeScript
postMessage(name: string, ports: Array<WebMessagePort>, uri: string): void
```

Sends a web message to an HTML window.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the message to send. |
| ports | Array&lt;[WebMessagePort](arkts-arkweb-webview-webmessageport-i.md)&gt; | Yes | Message ports for sending the message. |
| uri | string | Yes | URI for receiving the message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## postUrl

```TypeScript
postUrl(url: string, postData: ArrayBuffer): void
```

Loads a URL with postData using the "POST" method. If the URL is not a network URL, the [loadUrl](#loadurl) method is used to load the URL, and the postData parameter is ignored.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL to load. |
| postData | ArrayBuffer | Yes | Data to transfer using the POST method. The request must be encoded in "application/x-www-form-urlencoded" format. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid. |

## precompileJavaScript

```TypeScript
precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<number>
```

Precompiles JavaScript to generate the bytecode cache or update the existing bytecode cache based on the provided parameters.

The API determines whether to update the existing bytecode cache based on the provided file information, E-Tag response header, and Last-Modified response header.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | Network address corresponding to the local JavaScript file, that is, the network address used when the service web page requests the server version of the file. The network address supports only the HTTP and HTTPS protocols and contains a maximum of 2048 characters. If the cache corresponding to the network address is invalid, the service web page requests the corresponding resource through the network. |
| script | string &#124; Uint8Array | Yes | Text content of the local JavaScript. The content cannot be empty. |
| cacheOptions | [CacheOptions](arkts-arkweb-webview-cacheoptions-i.md) | Yes | Whether to update the bytecode cache. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the error code for generating the bytecode cache. The value **0** indicates no error, and the value **-1** indicates an internal error. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void
```

Prefetches resources in the background for a page that is likely to be accessed in the near future, without executing the page JavaScript code or presenting the page. This can significantly reduce the load time for the prefetched page.

> **NOTE:** 
> 
> - The downloaded page resources are cached for about five minutes. After this period, the **Web** component automatically releases them.
> 
> - **prefetchPage** can also normally prefetch 302 redirect pages.
> 
> - When **prefetchPage** is executed first and then the page is loaded, the prefetched resources are loaded directly from the cache.
> 
> - When multiple URLs are prefetched consecutively with **prefetchPage**, only the first one takes effect.
> 
> - **prefetchPage** has a time limit. Multiple prefetches cannot be performed within 500 ms.
> 
> - **prefetchPage** caches all resources except those with the Cache-Control: no-store header. If a Vary response header or Cache-Control: no-store header exists, or the downloaded page resources have been cached for more than five minutes, the resources are revalidated before use.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL to preload. |
| additionalHeaders | Array&lt;[WebHeader](arkts-arkweb-webview-webheader-i.md)&gt; | No | Additional HTTP request headers for the URL.<br>Default value: [] |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**Applicable version:** 22 and later |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void
```

Prefetches resources in the background for a page that is likely to be accessed in the near future, without executing the page JavaScript code or presenting the page. This can significantly reduce the load time for the prefetched page.

> **NOTE:** 
> 
> - The downloaded page resources are cached for about five minutes. After this period, the **Web** component automatically releases them.
> 
> - **prefetchPage** can also normally prefetch 302 redirect pages.
> 
> - When **prefetchPage** is executed first and then the page is loaded, the prefetched resources are loaded directly from the cache.
> 
> - **prefetchPage** caches all resources except those with the Cache-Control: no-store header. If a Vary response header or Cache-Control: no-store header exists, or the downloaded page resources have been cached for more than five minutes, the resources are revalidated before use.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL to preload. |
| additionalHeaders | Array&lt;[WebHeader](arkts-arkweb-webview-webheader-i.md)&gt; | No | Additional HTTP request headers for the URL.<br>Default value: [] |
| prefetchOptions | [PrefetchOptions](arkts-arkweb-webview-prefetchoptions-c.md) | No | Options for customizing the prefetch behavior.<br>The minimum interval between two prefetches is 500 ms. By default, Cache-Control: no-store in the response header is not ignored. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**Applicable version:** 22 and later |

## prefetchResource

```TypeScript
static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,
                            cacheValidTime?: number): void
```

Prefetches resource requests based on specified request information and additional HTTP request headers, saves them to the memory cache, and specifies the cache key and validity period to accelerate loading. Currently, only POST requests with Content-Type of application/x-www-form-urlencoded are supported. A maximum of six POST requests can be prefetched. To prefetch a seventh one, use [clearPrefetchedResource](#clearprefetchedresource) to clear unnecessary POST request caches. Otherwise, the earliest prefetched POST cache is automatically cleared. To use the prefetched resource cache, developers need to add the key-value pair "ArkWebPostCacheKey" to the request header of the actual POST request, with the value being the cacheKey of the corresponding cache.

Resources in the memory cache are automatically managed by the kernel. When too many resources are injected, causing excessive memory pressure, the kernel automatically releases unused resources. However, injecting a large number of resources into the memory cache should still be avoided.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [RequestInfo](arkts-arkweb-webview-requestinfo-i.md) | Yes | Information about the prefetched request. |
| additionalHeaders | Array&lt;[WebHeader](arkts-arkweb-webview-webheader-i.md)&gt; | No | Additional HTTP request header of the prefetched request.<br>If **undefined** or **null** is passed, error code **401** will be thrown. |
| cacheKey | string | No | Key used to query the cache of prefetched resources. The value can contain only letters and digits. If this parameter is not passed or is left empty, **url** is used by default.<br>If **undefined** or **null** is passed, error code **401** will be thrown. |
| cacheValidTime | number | No | Validity period of the prefetched resource cache.<br>Value range: (0, 2147483647]. <br>Default value: 300s. <br>Unit: s. <br>If undefined or null is passed in, an exception with error code 401 is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**Applicable version:** 22 and later |

## prepareForPageLoad

```TypeScript
static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void
```

Preconnects to a URL. Call this API before loading the URL. It only performs DNS resolution and socket connection for the URL, without fetching the main resource or sub-resources.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for preconnection. |
| preconnectable | boolean | Yes | Whether to perform preconnection. If the value is **true**, DNS resolution and socket connection preconnection are performed for the URL. If the value is **false**, no preconnection operation is performed. |
| numSockets | number | Yes | Number of sockets to be preconnected. The value must be greater than 0. A maximum of six socket connections are allowed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**Applicable version:** 22 and later |
| [17100013](../errorcode-webview.md#17100013-invalid-number-of-sockets-during-preconnection) | The number of preconnect sockets is invalid. |

## refresh

```TypeScript
refresh(): void
```

Called when the **Web** component refreshes the web page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## refresh

```TypeScript
refresh(ignoreCache: boolean): void
```

Notifies the **Web** component to refresh the web page. You can choose whether to ignore the cache refresh.

**Since:** 24

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ignoreCache | boolean | Yes | Whether to ignore cache refresh when the **Web** component refreshes the web page.<br>The value **true** means to ignore the cache refresh, and **false** means the opposite. <br>**NOTE:** <br>If **undefined** or **null** is passed in, the value is **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,
        asyncMethodList?: Array<string>, permission?: string): void
```

Registers a proxy for interaction between the application and web pages loaded by the **Web** component. Registers a JavaScript object with the window. APIs of this object can then be invoked in the window.

For the example, see [Invoking Application Functions on the Frontend Page](../../../web/web-in-page-app-function-invoking.md).

> **NOTE:** 
> 
> - The **registerJavaScriptProxy** API must be used together with the **deleteJavaScriptRegister** API to prevent memory leak.
> 
> - It is recommended that **registerJavaScriptProxy** be used only with trusted URLs and over secure HTTPS connections. Injecting JavaScript objects into untrusted web components can expose your application to malicious attacks.
> 
> - After **registerJavaScriptProxy** is called, the application exposes the registered JavaScript object to all page frames.
> 
> - If a **registerJavaScriptProxy** is both registered in the synchronous and asynchronous lists, it is called asynchronously by default.
> 
> - You should register **registerJavaScriptProxy** either in synchronous list or in asynchronous list.Otherwise, this API fails to be registered.
> 
> - After the HTML5 thread submits an asynchronous JavaScript task to the ETS main thread, the HTML5 thread can continue to execute subsequent tasks without waiting for the task execution to complete and return a result. In this way, scenarios where the HTML5 thread is blocked due to long-running JavaScript tasks or a congested ETS thread can be effectively reduced. However, an asynchronous JavaScript task cannot return a value, and a task execution sequence cannot be ensured. Therefore, you should determine whether to use a synchronous or asynchronous function based on a specific scenario.
> 
> - The injected object does not appear in JavaScript until the page is reloaded.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jsObject | object | Yes | Application-side JavaScript object to be registered. Methods and attributes can be declared separately, but cannot be registered and used at the same time. If an object contains only attributes, HTML5 can access the attributes in the object. If an object contains only methods, HTML5 can access the methods in the object.<br>1. The parameter and return value can be any of the following types: <br>string, number, boolean. <br>2. Dictionary or Array, with a maximum of 10 nested layers and 10,000 data records per layer. <br>3. Object, which must contain the **methodNameListForJsProxy:[fun1, fun2]** attribute, where **fun1** and **fun2** are methods that can be called. <br>4. The parameter also supports Function and Promise. Their callback cannot have return values. <br>5. The return value supports Promise. Its callback cannot have a return value. |
| name | string | Yes | Name of the object to be registered, which is the same as that invoked in the window. After registration, the window can use this name to access the JavaScript object at the application side. |
| methodList | Array&lt;string&gt; | Yes | Synchronous methods of the JavaScript object to be registered at the application side. |
| asyncMethodList | Array&lt;string&gt; | No | Asynchronous methods of the JavaScript object to be registered at the application side. The default value is null. Asynchronous methods cannot obtain return values.<br>If **undefined** or **null** is passed, error code **401** will be thrown.<br>**Since:** 12 |
| permission | string | No | JSON string, which is empty by default. This string is used to configure JSBridge permission control and define the URL trustlist at the object and method levels.<br>1. The **scheme** and **host** parameters cannot be empty. The **host** does not support wildcards and can contain only complete host names. <br>2. You can configure only the object-level trustlist, which takes effect for all JSBridge methods. <br>3. If method-level trustlists are configured for JSBridge method A, the intersection of object-level and method-level trustlists takes effect. <br>If **undefined** or **null** is passed, error code **401** will be thrown.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## removeAllCache

```TypeScript
static removeAllCache(clearRom: boolean): void
```

Removes all resource caches generated by Webview (including private mode) in the app.

**Since:** 18

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clearRom | boolean | Yes | Whether to clear the cache files in both ROM and RAM. If this parameter is set to **true**, the cache files in both ROM and RAM are cleared. If this parameter is set to **false**, only the cache files in RAM are cleared. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## removeCache

```TypeScript
removeCache(clearRom: boolean): void
```

Removes all resource caches generated by Webview in the app.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clearRom | boolean | Yes | Whether to clear the cache files in both ROM and RAM. If this parameter is set to **true**, the cache files in both ROM and RAM are cleared. If this parameter is set to **false**, only the cache files in RAM are cleared. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## removeIntelligentTrackingPreventionBypassingList

```TypeScript
static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

Deletes the domain names from the list of domain names added through the **addIntelligentTrackingPreventionBypassingList** API.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | Yes | List of domain names that bypass intelligent tracking prevention. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

## requestFocus

```TypeScript
requestFocus(): void
```

Requests focus for the specified component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## restoreWebState

```TypeScript
restoreWebState(state: Uint8Array) : void
```

Restores the page status history from the serialized data of the current WebView.

If the value of **state** is too large, exceptions may occur. It is recommended that the page status history be not restored when the **state** value is greater than 512 KB.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | Uint8Array | Yes | Serialized data of the page status history. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## resumeAllMedia

```TypeScript
resumeAllMedia(): void
```

Resumes the playback of the audio and video that are paused by the pauseAllMedia interface.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## resumeAllTimers

```TypeScript
static resumeAllTimers(): void
```

Resumes all timers that are paused from the **pauseAllTimers()** API.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## resumeMicrophone

```TypeScript
resumeMicrophone(): void
```

Resumes microphone capture on the current web page. Before using the microphone , add the **ohos.permission.MICROPHONE** permission to **module.json5**. For details about how to add the permission, see [Declaring Permissions in the Configuration File](../../../security/AccessToken/declare-permissions.md).

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## runJavaScript

```TypeScript
runJavaScript(script: string): Promise<string>
```

Executes a JavaScript script asynchronously in the context of the current page. This API uses a promise to return the script execution result. This method and its callback must be used on the UI thread.

> **NOTE:** 
> 
> - The JavaScript status is no longer retained during navigation operations (such as **loadUrl**). For example,the global variables and functions defined before **loadUrl** is called do not exist in the loaded page.
> 
> - It is recommended that the app use **registerJavaScriptProxy** to ensure that the JavaScript status can be retained across page navigation.
> 
> - Currently, passing objects is not supported. Passing structs is supported.
> 
> - Executing asynchronous methods cannot obtain return values. Determine whether to use synchronous or asynchronous methods based on the specific context.
> 
> - The string data type passed from the frontend page to the app side is treated as JSON-formatted data and needs to be deserialized with JSON.parse.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| script | string | Yes | JavaScript script. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result if the operation is successful and null otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-incorrect-resource-path) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScript

```TypeScript
runJavaScript(script: string, callback: AsyncCallback<string>): void
```

Executes a JavaScript script asynchronously in the context of the current page. This API uses an asynchronous callback to return the script execution result. This method and its callback must be used on the UI thread.

> **NOTE:** 
> 
> - The JavaScript status is no longer retained during navigation operations (such as **loadUrl**). For example,the global variables and functions defined before **loadUrl** is called do not exist in the loaded page.
> 
> - It is recommended that the app use **registerJavaScriptProxy** to ensure that the JavaScript status can be retained across page navigation.
> 
> - Currently, passing objects is not supported. Passing structs is supported.
> 
> - Executing asynchronous methods cannot obtain return values. Determine whether to use synchronous or asynchronous methods based on the specific context.
> 
> - The string data type passed from the frontend page to the app side is treated as JSON-formatted data and needs to be deserialized with JSON.parse.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| script | string | Yes | JavaScript script. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. **null** is returned if the JavaScript script fails to be executed or no value is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-incorrect-resource-path) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>
```

Executes a JavaScript script asynchronously and returns the script execution result through a promise. **runJavaScriptExt** can be invoked only after **loadUrl** is executed, for example, in onPageEnd.

> **NOTE:** 
> 
> - The string data type passed from the frontend page to the app side is treated as JSON-formatted data and needs to be deserialized with JSON.parse.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| script | string &#124; ArrayBuffer | Yes | JavaScript script.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[JsMessageExt](arkts-arkweb-webview-jsmessageext-c.md)&gt; | Promise used to return the script execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void
```

Executes a JavaScript script. This API uses an asynchronous callback to return the script execution result. **runJavaScriptExt** can be invoked only after **loadUrl** is executed. For example, it can be invoked in **onPageEnd**.

> **NOTE:** 
> 
> - The string data type passed from the frontend page to the app side is treated as JSON-formatted data and needs to be deserialized with JSON.parse.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| script | string &#124; ArrayBuffer | Yes | JavaScript script.<br>**Since:** 12 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[JsMessageExt](arkts-arkweb-webview-jsmessageext-c.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## scrollBy

```TypeScript
scrollBy(deltaX: number, deltaY: number, duration?: number): void
```

Scrolls the page by the specified amount within a specified period.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deltaX | number | Yes | Amount to scroll by along the x-axis. The positive direction is rightward.<br>Unit: vp |
| deltaY | number | Yes | Amount to scroll by along the y-axis. The positive direction is downward.<br>Unit: vp |
| duration | number | No | Scrolling animation duration,<br>in milliseconds. <br>If no value is input or the input value is a negative number or 0, the animation is disabled. <br>If **null** or **undefined** is passed, error code **401** is thrown.<br>**Since:** 14 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## scrollByWithResult

```TypeScript
scrollByWithResult(deltaX: number, deltaY: number): boolean
```

Scrolls the page by the specified amount and returns value to indicate whether the scrolling is successful.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deltaX | number | Yes | Amount to scroll by along the x-axis. The positive direction is rightward.<br>Unit: vp |
| deltaY | number | Yes | Amount to scroll by along the y-axis. The positive direction is downward.<br>Unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the current web page can be scrolled, and **false** indicates that the current web page cannot be scrolled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## scrollTo

```TypeScript
scrollTo(x: number, y: number, duration?: number): void
```

Scrolls the page to the specified absolute position within a specified period.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate of the absolute position. If the value is a negative number, the value 0 is used.<br>Unit: vp |
| y | number | Yes | Y coordinate of the absolute position. If the value is a negative number, the value 0 is used.<br>Unit: vp |
| duration | number | No | Scrolling animation duration,<br>in milliseconds. <br>If no value is input or the input value is a negative number or 0, the animation is disabled. <br>If **null** or **undefined** is passed, error code **401** is thrown.<br>**Since:** 14 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## searchAllAsync

```TypeScript
searchAllAsync(searchString: string): void
```

Searches the web page for content that matches the keyword specified by **'searchString'** and highlights the matches on the page. This API returns the result asynchronously through [onSearchResultReceive](../arkts-components/arkts-arkweb-web-comp-attribute.md#onsearchresultreceive).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchString | string | Yes | Search keyword. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## searchNext

```TypeScript
searchNext(forward: boolean): void
```

Searches for and highlights the next match.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| forward | boolean | Yes | Whether to search forward or backward.<br>The value **true** indicates a forward search, and the value **false** indicates a backward search. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## serializeWebState

```TypeScript
serializeWebState(): Uint8Array
```

Serializes the page status history of the current WebView.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Serialized data of the page state history of the current WebView. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setActiveWebEngineVersion

```TypeScript
static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void
```

Sets the ArkWeb kernel version. If the system does not support the specified version, the setting does not take effect and the system default kernel is used (see [Constraints](../../../web/web-component-overview.md#constraints)). This API is a global static API and must be executed before **initializeWebEngine** is called. If any **Web** component has been loaded, the setting does not take effect. Typical use case: when features or compatibility requirements of a specific kernel version are needed, you can switch to the corresponding kernel version.

> **NOTE:** 
> 
> - **setActiveWebEngineVersion** cannot be called in an asynchronous thread.
> 
> - **setActiveWebEngineVersion** takes effect globally and needs to be called only once in an application lifecycle.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| engineVersion | [ArkWebEngineVersion](arkts-arkweb-webview-arkwebengineversion-e.md) | Yes | ArkWeb kernel version. |

## setAppCustomUserAgent

```TypeScript
static setAppCustomUserAgent(userAgent: string) : void
```

Sets the application-level custom user agent, which will overwrite the system user agent and take effect for all **Web** components in the application.

If you need to set the application-level custom user agent, you are advised to call the **setAppCustomUserAgent** method to set the **User-Agent** before creating the **Web** component, and then create the **Web** component with the specified src or load the page using [loadUrl](#loadurl).

For details about the default **User-Agent** definition, application scenarios, and API priorities, see [Developing User-Agent](../../../web/web-default-userAgent.md).

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userAgent | string | Yes | Information about the custom user agent. It is recommended that you obtain the current default user agent through [getDefaultUserAgent](#getdefaultuseragent) and then customize the obtained user agent. |

## setAudioMuted

```TypeScript
setAudioMuted(mute: boolean): void
```

Mutes the web page. Typical use cases include: the app needs to control the web page volume (such as providing a mute switch), or needs to mute during background playback.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mute | boolean | Yes | Whether to mute the web page.<br>The value **true** means to mute the web page, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setAutoPreconnect

```TypeScript
static setAutoPreconnect(enabled: boolean): void
```

Sets the automatic preconnection status of the Web kernel. If this API is not set, automatic preconnection is enabled by default.

This API must be called before [initializeWebEngine()](#initializewebengine) initializes the kernel or a **Web** component is created. If any **Web** component has been loaded, the setting does not take effect.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable automatic preconnection of the Web kernel. The value **true** means to enable the private network access check feature, and **false** means the opposite. |

## setBackForwardCacheOptions

```TypeScript
setBackForwardCacheOptions(options: BackForwardCacheOptions): void
```

Sets the back-forward cache options of the **Web** component.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [BackForwardCacheOptions](arkts-arkweb-webview-backforwardcacheoptions-c.md) | Yes | Options to control the back-forward cache of the **Web** component. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setBlanklessLoadingCacheCapacity

```TypeScript
static setBlanklessLoadingCacheCapacity(capacity: number) : number
```

Sets the persistent cache capacity of the blankless loading solution and returns the value that takes effect. If the API is not explicitly called, the default cache capacity is 30 MB. When this limit is exceeded, transition frames that are not frequently used are eliminated.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capacity | number | Yes | Persistent cache capacity, in MB. The maximum value is 100 MB.<br>The value ranges from 0 to 100. If this parameter is set to **0**, no cache capacity is available and the functionality is disabled globally.<br>When a value less than 0 is set, the value **0** takes effect. When a value greater than 100 is set, the value **100** takes effect. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Effective value that ranges from 0 MB to 100 MB.<br>When a value less than 0 is set, the value **0** takes effect. When a value greater than 100 is set, the value **100** takes effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) |  |

## setBlanklessLoadingWithKey

```TypeScript
setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode
```

Sets whether to enable blankless loading. This API must be used together with [getBlanklessInfoWithKey](#getblanklessinfowithkey).

> **NOTE:** 
> 
> - This API must be called after the page loading API is triggered. Other restrictions are the same as those of [getBlanklessInfoWithKey](#getblanklessinfowithkey).
> 
> - The page must be loaded in the component that calls this API.
> 
> - When the similarity is low, the system will deem the scene change too abrupt and frame insertion will fail.
> 
> - Add the **ohos.permission.INTERNET** and **ohos.permission.GET_NETWORK_INFO** permissions to **module.json5**. For details, see [Declaring Permissions in the Configuration File](../../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key value that uniquely identifies the page. This value must be the same as the **key** value of the **getBlanklessInfoWithKey** API.<br>The value cannot be empty and can contain a maximum of 2048 characters.<br>When an invalid value is set, the error code **WebBlanklessErrorCode** is returned, and the API does not take effect. |
| is_start | boolean | Yes | Whether to enable frame interpolation. The value **true** means to enable frame interpolation, and **false** means the opposite.<br>If **undefined** or **null** is passed in, the value is **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md) | Whether the API is successfully called. For details, see [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) |  |

## setBlanklessLoadingWithParams

```TypeScript
setBlanklessLoadingWithParams(key: string,
      param: BlanklessLoadingParam) : WebBlanklessErrorCode
```

Sets the configuration parameters for frame interpolation during blankless loading. This API must be used with [getBlanklessInfoWithKey](#getblanklessinfowithkey). Compared with [setBlanklessLoadingWithKey](#setblanklessloadingwithkey), this API supports more parameter settings for frame interpolation during blankless loading, including the frame interpolation duration, cache data validity period, and custom callback after frame interpolation is complete.

> **NOTE:** 
> 
> - This API must be called after the page loading API is triggered. Other restrictions are the same as those of [getBlanklessInfoWithKey](#getblanklessinfowithkey).
> 
> - The page must be loaded in the component that calls this API.
> 
> - When the similarity is low, the system will deem the scene change too abrupt and frame insertion will fail.
> 
> - Add the **ohos.permission.INTERNET** and **ohos.permission.GET_NETWORK_INFO** permissions to
> **module.json5**. For details, see
> [Declaring Permissions in the Configuration File](../../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key value that uniquely identifies the page. This value must be the same as the **key** value of the **getBlanklessInfoWithKey** API.<br>The value cannot be empty and can contain a maximum of 2048 characters. <br>When an invalid value is set, the error code **WebBlanklessErrorCode** is returned, and the API does not take effect. |
| param | [BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md) | Yes | Parameters for frame interpolation of blankless loading. |

**Return value:**

| Type | Description |
| --- | --- |
| [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md) | API calling result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

## setConnectionTimeout

```TypeScript
static setConnectionTimeout(timeout: number): void
```

Sets the network connection timeout interval. You can use the **onErrorReceive** method in the **Web** component to obtain the timeout error code. If this API is not called, the default timeout interval is **30** seconds.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Socket connection timeout duration, in seconds. The value must be a positive integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |

## setCustomUserAgent

```TypeScript
setCustomUserAgent(userAgent: string): void
```

Sets a custom user agent, which will overwrite the default user agent.

> **NOTE:** 
> 
> - When **src** of the **Web** component is set to a URL, it is recommended to set **User-Agent** in the onControllerAttached callback. Do not set it in the
> **onLoadIntercept** callback, as this may cause the setting to fail or lead to unexpected results.
> 
> - If **User-Agent** is not set in the **onControllerAttached** callback, calling **setCustomUserAgent** later may cause an anomaly where the loaded page does not match the actually set **User-Agent**.
> 
> - When **src** of the **Web** component is not set to a URL, it is recommended to call **setCustomUserAgent**to set **User-Agent** first, and then use **loadUrl** to load a specific page.
> 
> - For the definition and usage scenarios of the default **User-Agent**, see [User-Agent Development Guide](../../../web/web-default-user-agent.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userAgent | string | Yes | Information about the custom user agent. It is recommended that you obtain the current default user agent through [getUserAgent](#getuseragent) and then customize the obtained user agent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setDownloadDelegate

```TypeScript
setDownloadDelegate(delegate: WebDownloadDelegate): void
```

Sets a **WebDownloadDelegate** for the current **Web** component. The delegate is used to receive the download progress triggered within the page.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delegate | [WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md) | Yes | Delegate used to receive the download progress. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setErrorPageEnabled

```TypeScript
setErrorPageEnabled(enable: boolean): void
```

Sets whether to enable the default error page.

When this API is set to true, if an error occurs during page loading, the [onOverrideErrorPage](../arkts-components/arkts-arkweb-web-comp-attribute.md#onoverrideerrorpage) callback is triggered. You can customize the error display page in the callback.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the default error page. The value **true** means to enable the default error page, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setErrorPageEnabled

```TypeScript
setErrorPageEnabled(enable: boolean, includeSubframe: boolean): void
```

Sets whether to enable the mainframe error page feature, and controls whether to also enable the subframe error page feature.

When **enable** is set to **true**, an error page is displayed when a mainframe loading error occurs: if the [onOverrideErrorPage](../arkts-components/arkts-arkweb-web-comp-attribute.md#onoverrideerrorpage) callback is set, the user-defined error page is displayed; if not, the default error page provided by ArkWeb is displayed. When both **enable** and **includeSubframe** are set to **true**, an error page is also displayed when a subframe loading error occurs, and the **onOverrideErrorPage** callback also takes effect for subframes.

> **NOTE:** 
> 
> - When **enable** is set to **false**, the error page feature for both mainframe and subframe is disabled regardless of the value of **includeSubframe**.
> 
> - When **includeSubframe** is set to **false**, the behavior of this API is the same as that of [setErrorPageEnabled](#seterrorpageenabled)&lt;sup&gt;20+&lt;/sup&gt;, that is, only the mainframe error page feature is enabled, and the subframe error page feature is not enabled.
> 
> - You can use errorPageEvent.request.isMainFrame() to determine whether the error source is a mainframe or a subframe, so as to set the corresponding custom error page in the
> **onOverrideErrorPage** callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the mainframe error page feature. The value **true** means to enable it, and **false** means the opposite. When enabled, an error page is displayed when a mainframe loading error occurs. |
| includeSubframe | boolean | Yes | Whether to also enable the subframe error page feature. The value **true** means to enable it, and **false** means the opposite. When enabled, an error page is also displayed when a subframe loading error occurs. This parameter takes effect only when **enable** is **true**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setHostIP

```TypeScript
static setHostIP(hostName: string, address: string, aliveTime: number): void
```

Sets the IP address of the host after domain name resolution.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hostName | string | Yes | Domain name of the host whose DNS records are to be added. |
| address | string | Yes | Host domain name resolution address (IPv4 and IPv6). |
| aliveTime | number | Yes | Cache validity period, in seconds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## setHttpDns

```TypeScript
static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void
```

Sets how the **Web** component uses HTTPDNS for DNS resolution.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| secureDnsMode | [SecureDnsMode](arkts-arkweb-webview-securednsmode-e.md) | Yes | Mode in which HTTPDNS is used. |
| secureDnsConfig | string | Yes | Information about the HTTPDNS server to use, which must use HTTPS. Only one HTTPDNS server can be configured. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |

## setNetworkAvailable

```TypeScript
setNetworkAvailable(enable: boolean): void
```

Sets the **window.navigator.onLine** attribute in JavaScript.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the **window.navigator.onLine** attribute.<br>The value **true** indicates that the **window.navigator.onLine** attribute is enabled, and the value **false** indicates the opposite. <br>Default value: **true**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setPathAllowingUniversalAccess

```TypeScript
setPathAllowingUniversalAccess(pathList: Array<string>): void
```

Sets a path list. When the file protocol accesses resources in the path list, cross-origin access to local files and other online resources is allowed. In addition, when a path list is set, the file protocol only allows access to resources in the path list. Typical use case: used when the **Web** component needs to be allowed to access local resource files across origins while restricting the access scope to ensure security. (The behavior of fileAccess will be overridden by the behavior of this API.)

Using setPathAllowingUniversalAccess to relax cross-origin access restrictions on directories is a high-risk operation. Based on the principle of least privilege, the paths for el1 and el2 are fixed. The paths in the path list must conform to one of the following path formats:

1. A subdirectory of the app file directory. (The app file directory is obtained through [Context.filesDir]
(../../../reference/apis-ability-kit/js-apis-inner-application-context.md#properties) in Ability Kit.) For example:

* /data/storage/el2/base/files/example  
* /data/storage/el2/base/haps/entry/files/example

2. The app resource directory or its subdirectory.
(The app resource directory is obtained through [Context.resourceDir] (../../../reference/apis-ability-kit/js-apis-inner-application-context.md#properties) in Ability Kit.) For example:

* /data/storage/el1/bundle/entry/resource/resfile  
* /data/storage/el1/bundle/entry/resource/resfile/example

3. Since API version 21, the app cache directory and its subdirectory are also included.
(The app cache directory is obtained through [Context.cacheDir] (../../../reference/apis-ability-kit/js-apis-inner-application-context.md#properties) in Ability Kit.) For example:

* /data/storage/el2/base/cache  
* /data/storage/el2/base/haps/entry/cache/example  
* The **cache/web** directory is not allowed. If it is included, an exception with the code **401** will be thrown. If the **cache** directory is set, **cache/web** cannot be accessed.

4. Since API version 21, the app temporary directory and its subdirectory are also included.
(The app temporary directory is obtained through [Context.tempDir] (../../../reference/apis-ability-kit/js-apis-inner-application-context.md#properties) in Ability Kit.) For example:

* /data/storage/el2/base/temp  
* /data/storage/el2/base/haps/entry/temp/example

If a path in the list is not of the preceding paths, error code 401 is reported and the path list fails to be set. When the path list is set to empty, the accessible files for the file protocol are subject to the behavior of the fileAccess.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pathList | Array&lt;string&gt; | Yes | The path list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Parameter string is too long. <br>3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setPrintBackground

```TypeScript
setPrintBackground(enable: boolean): void
```

Sets whether to print the background of a web page. If the setting of this API is inconsistent with that of [PrintAttributes](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-print-printattributes-i.md), the setting of this API takes precedence.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to print the web page background.<br>The value **true** means to print the web page background, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setRenderProcessMode

```TypeScript
static setRenderProcessMode(mode: RenderProcessMode): void
```

Sets the ArkWeb rendering subprocess mode. You can select the appropriate mode based on the app's requirements for memory usage and rendering process isolation.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [RenderProcessMode](arkts-arkweb-webview-renderprocessmode-e.md) | Yes | Render subprocess mode. <br>You can call [getRenderProcessMode()](#getrenderprocessmode) to view the ArkWeb rendering subprocess mode of the current device. The enumerated value **0** indicates the single render subprocess mode, and **1** indicates the multi-render subprocess mode. <br>By default, mobile phones use the single render subprocess mode, and tablets and PCs/2in1 devices use the multi-render subprocess mode. <br>If an invalid number other than the enumerated value of **RenderProcessMode** is passed, the multi-render subprocess mode is used by default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## setScrollable

```TypeScript
setScrollable(enable: boolean, type?: ScrollType): void
```

Sets whether this web page is scrollable.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether this web page is scrollable.<br>The value **true** indicates that this web page is scrollable, and **false** indicates the opposite. <br>Default value: **true**. |
| type | [ScrollType](arkts-arkweb-webview-scrolltype-e.md) | No | Scrolling type supported by the web page. The default value is supported.<br> - If the value of **enable** is set to **false**, the specified **ScrollType** is disabled. If **ScrollType** is set to the default value, all scrolling types are disabled. <br> - If the value of **enable** is set to **true**, all scrolling types are enabled regardless of the value of **ScrollType**. <br>If **null** or **undefined** is passed, error code **401** is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setScrollbarMode

```TypeScript
static setScrollbarMode(scrollbarMode: ScrollbarMode): void
```

Sets the global scrollbar mode in the web page. When this API is not explicitly called, [ScrollbarMode.OVERLAY_LAYOUT_SCROLLBAR](arkts-arkweb-webview-scrollbarmode-e.md) is used by default, indicating that the scroll bar is not always displayed.

> **NOTE:** 
> 
> - You can set whether to always display the web scrollbar of the current application based on the scrollbar mode.
> 
> - If the [forceDisplayScrollBar](../arkts-components/arkts-arkweb-web-comp-attribute.md#forcedisplayscrollbar) API is set at the same time as this API, the setting of **forceDisplayScrollBar** does not take effect.
> 
> - This API must be called before WebViewController is bound to a **Web** component.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scrollbarMode | [ScrollbarMode](arkts-arkweb-webview-scrollbarmode-e.md) | Yes | Scroll bar mode. |

## setServiceWorkerWebSchemeHandler

```TypeScript
static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

Sets a WebSchemeHandler for all **Web** components of the current app, used to intercept requests of a specified scheme in ServiceWorker.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scheme | string | Yes | Protocol to be intercepted. |
| handler | [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) | Yes | Interceptor that intercepts this protocol. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setSiteIsolationMode

```TypeScript
static setSiteIsolationMode(mode: SiteIsolationMode): void
```

Sets the site isolation mode. The site isolation mechanism isolates websites from different origins in different rendering processes to reduce the cross-domain attack surface. For example, on devices such as PCs, when site isolation mode is not enabled, the original process model assigns one rendering process per tab. After site isolation is enabled, iframes from different origins within a tab can run in independent rendering processes.

For third-party applications that load only trusted web pages, you can disable this functionality to improve performance, reduce memory usage, and reduce interception of cross-domain access. The default value varies according to the device. [SiteIsolationMode.STRICT](arkts-arkweb-webview-siteisolationmode-e.md) is used for PCs and tablets, and [SiteIsolationMode.PARTIAL](arkts-arkweb-webview-siteisolationmode-e.md) is used for phones. In [Secure Shield mode](../../../web/web-secure-shield-mode.md), strict site isolation is used.

> **NOTE:** 
> 
> Strict site isolation cannot be set in single-process mode.
> 
> This API can be called only once during initialization. The site isolation mode cannot be repeatedly changed.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SiteIsolationMode](arkts-arkweb-webview-siteisolationmode-e.md) | Yes | Site isolation mode.<br>The default value depends on the device type and device mode. For PCs and tablets, strict site isolation is used by default. For phones, partial site isolation is used by default. In Secure Shield mode, strict site isolation is used by default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. Possible causes: 1. Site Isolation mode is already set by the developer. 2. Site Isolation mode cannot be strict in single-render-process mode. 3. Site Isolation mode cannot be changed while Secure Shield mode is active. |

## setSocketIdleTimeout

```TypeScript
static setSocketIdleTimeout(timeout: number): void
```

Sets the timeout interval for used sockets to stay idle in the **Web** component. If the value is different from the timeout interval of existing idle sockets, the existing idle sockets are cleared according to the new value.

If this API is not used to set the timeout interval for idle sockets, the default value **300s** is used for the **Web** component.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Timeout interval for used sockets to stay idle in the **Web** component, in seconds.<br>Value range: [30, 300]. <br>If the value is less than 30, the value **30** takes effect. If the value is greater than 300, the value **300** takes effect. |

## setSoftKeyboardBehaviorMode

```TypeScript
setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void
```

Sets the automatic control mode of the soft keyboard. When this API is not explicitly called, the system attempts to automatically hide or show the soft keyboard when the **Web** component loses or gains focus, or when its state switches to inactive or active. Typical use case: when you do not want the **Web** component to automatically hide or re-show the soft keyboard during inactive or active state switching, use DISABLE_AUTO_KEYBOARD_ON_ACTIVE; when you need to retain the default automatic management behavior, use DEFAULT.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WebSoftKeyboardBehaviorMode](arkts-arkweb-webview-websoftkeyboardbehaviormode-e.md) | Yes | Behavior mode of the web soft keyboard. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string): void
```

Sets a URL trust list for the Web. Only URLs in the trust list are allowed to be loaded or navigated to. Otherwise, they are intercepted and an alert page is displayed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| urlTrustList | string | Yes | URL whitelist, configured in JSON format. The maximum size is 10 MB.<br>The whitelist setting API uses an overwrite mode. When the API is called multiple times, the last setting takes effect.<br>When this parameter is set to an empty string, the whitelist is canceled and access to all URLs is allowed. <br>JSON format example: <br>{<br>  "UrlPermissionList": [<br>    {<br>      "scheme": "https", <br>      "host": "www.example1.com", <br>      "port": 443, <br>      "path": "pathA/pathB"<br>    }, <br>    {<br>      "scheme": "http", <br>      "host": "www.example2.com", <br>      "port": 80, <br>      "path": "test1/test2/test3"<br>    } <br>  ] <br>} |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Parameter string is too long. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void
```

Sets a URL trust list for the Web. Only URLs in the trust list are allowed to be loaded or navigated to. Otherwise, they are intercepted and an alert page is displayed. This API extends the control over opaque origin URLs and wildcard rules.

**Since:** 24

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| urlTrustList | string | Yes | URL whitelist configured in JSON format, with a maximum size of 10 MB.<br>The whitelist setting uses an overwrite mode. When this API is called multiple times, the last setting takes effect.<br>When this parameter is set to an empty string, the whitelist is canceled and all URLs are allowed. <br>JSON format example: <br>{<br>  "UrlPermissionList": [<br>    {<br>      "scheme": "https", <br>      "host": "www.example1.com", <br>      "port": 443, <br>      "path": "pathA/pathB"<br>    }, <br>    {<br>      "scheme": "http", <br>      "host": "www.example2.com", <br>      "port": 80, <br>      "path": "test1/test2/test3"<br>    } <br>  ] <br>} |
| allowOpaqueOrigin | boolean | Yes | Whether to allow loadUrl to directly load [opaque origin URLs](https://mdn.org.cn/en-US/docs/Web/URI/Reference/Schemes) such as javascript/data. The value **true** means allowed, and **false** means not allowed. |
| supportWildcard | boolean | Yes | Whether to support wildcard matching for **host** and **path**. For example, to allow access to **a.example.com** and **b.example.com** when ***.example.com** is configured in the trustlist. **true** to support, and **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Initialization error. The WebviewController must be associated with a Web component. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) |  |

## setUserAgentClientHintsEnabled

```TypeScript
static setUserAgentClientHintsEnabled(enabled: boolean): void
```

Sets whether to enable the User-Agent Client Hints feature.

> **NOTE:** 
> 
> User-Agent Client Hints (UA-CH) is a privacy protection mechanism that replaces the traditional **User-Agent**
> string. It transfers client information through on-demand requests and structured data, reducing the risk of
> excessive tracking.
> 
> If this method is not used, the User-Agent Client Hints feature is disabled by default.

**Since:** 24

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the User-Agent Client Hints feature.<br>The value **true** means enabled, and **false** means disabled. |

## setUserAgentForHosts

```TypeScript
static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void
```

Sets a custom user agent for a specific website, which overwrites the system user agent and takes effect for all **Web** components in the application.

To set a custom user agent for a specific website, you are advised to call the **setUserAgentForHosts** method to set **User-Agent** before creating a **Web** component, and then create a **Web** component with a specified src or use [loadUrl](#loadurl) to load a specific page.

For details about the default **User-Agent** definition, application scenarios, and API priorities, see [Developing User-Agent](../../../web/web-default-userAgent.md).

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userAgent | string | Yes | Information about the custom user agent. It is recommended that you obtain the current default user agent through [getDefaultUserAgent](#getdefaultuseragent) and then customize the obtained user agent. |
| hosts | Array&lt;string&gt; | Yes | List of domain names related to the custom user agent. Only the latest list is retained each time the API is called. The maximum number of entries is 20,000, and the excessive entries are automatically truncated. |

## setUserAgentMetadata

```TypeScript
setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void
```

Sets the **UserAgentMetadata** corresponding to the **User-Agent**.

> **NOTE:** 
> 
> User-Agent Metadata is used to populate user agent client hints. It can provide the brand and version
> information of the client, the brand and major version of the underlying operating system, and detailed
> information about the underlying device.
> 
> The user agent can be set through setCustomUserAgent, setAppCustomUserAgent, or setUserAgentForHosts.
> 
> If no UserAgentMetadata is found based on the overridden User-Agent, and the overridden User-Agent contains the
> system default User-Agent, the system default value is used.
> 
> If no UserAgentMetadata is found based on the overridden User-Agent, but the overridden User-Agent does not
> contain the system default user agent, only low-level user agent client hints are generated.

**Since:** 24

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userAgent | string | Yes | Information about the custom user agent. You can use [getUserAgent](#getuseragent) to obtain the current default user agent. |
| metaData | [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md) | Yes | **UserAgentMetadata** corresponding to the user agent. You can use [getUserAgentMetadata](#getuseragentmetadata) to obtain the current default value and then modify it using the corresponding method. |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean): void
```

Sets whether to enable web debugging. For details, see [Debugging Frontend Pages by Using DevTools](../../../web/web-debugging-with-devtools.md).

NOTE: Enabling web debugging allows users to check and modify the internal status of the web page, which poses security risks. Therefore, you are advised not to enable this feature in the officially released version of the application.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | Yes | Sets whether to enable web debugging.<br>The value **true** means to enable web debugging, and **false** means the opposite. <br>Default value: **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void
```

Sets whether to enable wireless web debugging. By default, wireless web debugging is disabled.

* If no port is specified, this API is equivalent to the[setWebDebuggingAccess](#setwebdebuggingaccess) API. In this case, ArkWeb starts a local domain socket listener.  
* When a port is specified, ArkWeb starts a TCP socket listener. In this case, you can debug the web page wirelessly. For details, see [Wireless Debugging](../../../web/web-debugging-with-devtools.md#wireless-debugging).

A port number smaller than 1024 is a well-known or system port and can be enabled only with privileges in the operating system. Therefore, the value of port must be greater than 1024. Otherwise, the API throws an exception.

NOTE: Enabling web debugging allows users to check and modify the internal status of the web page, which poses security risks. Therefore, you are advised not to enable this feature in the officially released version of the application.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | Yes | Sets whether to enable web debugging.<br>The value **true** indicates that web page debugging is enabled, and **false** indicates the opposite. |
| port | number | Yes | Specifies the TCP port number of the DevTools service. If no port is specified, this API is equivalent to the [setWebDebuggingAccess] (#setwebdebuggingaccess) API.<br>Value range: (1024, 65535] <br>If the value of port is within the range of [0, 1024], the **BusinessError** exception is thrown. The error code is **17100023**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100023](../errorcode-webview.md#17100023-port-number-not-allowed) | The port number is not within the allowed range. |

## setWebDestroyMode

```TypeScript
static setWebDestroyMode(mode: WebDestroyMode): void
```

Sets the destroy mode of the **Web** component. The destroy mode of the **Web** component affects the time when web kernel resources, such as the JavaScript running context and rendering context, are released. The default value is [WebDestroyMode.NORMAL_MODE](arkts-arkweb-webview-webdestroymode-e.md) (normal mode), indicating that the system determines the destroy time. You can set [WebDestroyMode.FAST_MODE](arkts-arkweb-webview-webdestroymode-e.md) (fast mode) to destroy resources immediately, improving performance in specific scenarios.

> **NOTE:** 
> 
> [WebDestroyMode.FAST_MODE](arkts-arkweb-webview-webdestroymode-e.md) changes the time when the **Web** component is
> destroyed. When it is used, pay attention to the incorrect implementation that depends on the destroy time of
> the **Web** component. For example, when a **WebViewController** is called in fast mode rather than using
> [WebDestroyMode.NORMAL_MODE](arkts-arkweb-webview-webdestroymode-e.md), the unbinding exception (**17100001**) is more
> likely to be triggered. In this case, the application needs to capture the exception, or use
> [getAttachState](#getattachstate) to obtain the attach state to avoid stability
> problems.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WebDestroyMode](arkts-arkweb-webview-webdestroymode-e.md) | Yes | Destroy mode of the **Web** component.<br>Default value: **WebDestroyMode.NORMAL_MODE** |

## setWebSchemeHandler

```TypeScript
setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

Sets a [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) for the **Web** component. The [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) class is used to intercept requests of a specified scheme.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scheme | string | Yes | Protocol to be intercepted. |
| handler | [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) | Yes | Interceptor that intercepts this protocol. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## slideScroll

```TypeScript
slideScroll(vx: number, vy: number): void
```

Simulates a slide-to-scroll action on the page at the specified velocity.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| vx | number | Yes | Horizontal velocity component of swipe scrolling, where rightward is the positive direction.<br>Unit: vp/s. |
| vy | number | Yes | Vertical velocity component of swipe scrolling, where downward is the positive direction.<br>Unit: vp/s. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## startCamera

```TypeScript
startCamera(): void
```

Enables the camera capture of the current web page. Before using the camera, add the **ohos.permission.CAMERA** permission to **module.json5**. For details about how to add the permission, see [Declaring Permissions in the Configuration File](../../../security/AccessToken/declare-permissions.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## startDownload

```TypeScript
startDownload(url: string): void
```

Uses the download capability of the **Web** component to download a specified URL, for example, downloading a specified image from a web page.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | Download URL. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**Applicable version:** 22 and later |

## stop

```TypeScript
stop(): void
```

Stops page loading.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## stopAllMedia

```TypeScript
stopAllMedia(): void
```

Stops all audio and video on a web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## stopCamera

```TypeScript
stopCamera(): void
```

Stops the camera capture of the current web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## stopMicrophone

```TypeScript
stopMicrophone(): void
```

Stops microphone capture on the current web page.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## storeWebArchive

```TypeScript
storeWebArchive(baseName: string, autoName: boolean): Promise<string>
```

Stores this web page. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| baseName | string | Yes | Save path of the web page. The value cannot be null. |
| autoName | boolean | Yes | Whether to automatically generate a file name.<br>The value **false** means the file is stored with the name specified by baseName, and **true** means the file name is automatically generated based on the current URL and stored in the directory specified by baseName. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the save path if the operation is successful and null otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-incorrect-resource-path) | Invalid resource path or file type. |

## storeWebArchive

```TypeScript
storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void
```

Stores this web page. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| baseName | string | Yes | Save path of the web page. The value cannot be null. |
| autoName | boolean | Yes | Whether to automatically generate a file name.<br>The value **false** means the file is stored with the file name specified by **baseName**, and **true** means the file name is automatically generated based on the current URL and stored in the directory specified by **baseName**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the save path if the operation is successful and null otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-incorrect-resource-path) | Invalid resource path or file type. |

## terminateRenderProcess

```TypeScript
terminateRenderProcess(): boolean
```

Terminates this render process.

Calling this API will destroy the associated render process. If the render process has not been started or has been destroyed, there is no impact. In addition, destroying the render process affects all other instances associated with the render process.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the render process is terminated.<br>The value **true** indicates that the render process can be destroyed or has been destroyed, and **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |

## trimMemoryByPressureLevel

```TypeScript
static trimMemoryByPressureLevel(level: PressureLevel): void
```

Clears the cache occupied by **Web** component based on the specified memory pressure level.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [PressureLevel](arkts-arkweb-webview-pressurelevel-e.md) | Yes | Pressure level of the memory to be cleared. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Parameter string is too long. <br>3.Parameter verification failed. |

## waitForAttached

```TypeScript
waitForAttached(timeout: number): Promise<ControllerAttachState>
```

Asynchronously waits for the **WebViewController** to be attached to the **Web** component. If the attachment is complete or times out, a callback is triggered to return the current [ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md) through a promise.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Asynchronous waiting duration.<br>Value range: [0, 65535] <br>Unit: ms. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md)&gt; | Promise used to return the current [ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md). |

## warmupServiceWorker

```TypeScript
static warmupServiceWorker(url: string): void
```

Warms up ServiceWorker to improve the loading speed of the first screen page (only for pages that use ServiceWorker). Call this API before loading the URL.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the ServiceWorker to preload. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**Applicable version:** 22 and later |

## webPageSnapshot

```TypeScript
webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void
```

Obtains the full drawing result of the web page.

> **NOTE:** 
> 
> - This API does not support concurrent calls.
> 
> - Only supports taking snapshots of resources on the rendering process: static images and text.
> 
> - If the page contains a video, a placeholder image of the video is displayed in the snapshot. If there is no placeholder image, a blank area is displayed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [SnapshotInfo](arkts-arkweb-webview-snapshotinfo-i.md) | Yes | Information for obtaining the full drawing result. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SnapshotResult](arkts-arkweb-webview-snapshotresult-i.md)&gt; | Yes | Callback used to return the result. |

## zoom

```TypeScript
zoom(factor: number): void
```

Zooms in or out of this web page. This API is effective only when [zoomAccess](../arkts-components/arkts-arkweb-web-comp-attribute.md#zoomaccess) is **true**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| factor | number | Yes | Relative zoom ratio. The value must be greater than 0. The value **1** indicates that the page is not zoomed. A value smaller than **1** indicates zoom-out, and a value greater than **1** indicates zoom-in.<br>Value range: (0, 100] |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100004](../errorcode-webview.md#17100004-function-not-enabled) | Function not enabled. |

## zoomIn

```TypeScript
zoomIn(): void
```

Zooms in on this web page by 25%.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100004](../errorcode-webview.md#17100004-function-not-enabled) | Function not enabled. |

## zoomOut

```TypeScript
zoomOut(): void
```

Zooms out of this web page by 20%.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The WebviewController must be associated with a Web component. |
| [17100004](../errorcode-webview.md#17100004-function-not-enabled) | Function not enabled. |
