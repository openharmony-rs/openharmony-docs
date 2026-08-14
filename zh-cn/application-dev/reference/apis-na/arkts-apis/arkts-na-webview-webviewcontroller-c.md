# WebviewController

WebviewController can control various behaviors of Web components (including page navigation, declaring cycle state, JavaScript interaction and so on). A WebviewController object can only control one Web component, and methods on the Webviewcontroller (except static methods) can only be called after the web component is bound to the WebviewController.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class WebviewController--><!--Device-webview-class WebviewController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## accessBackward

```TypeScript
accessBackward(): boolean
```

Checks whether the web page can go back.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-accessBackward(): boolean--><!--Device-WebviewController-accessBackward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the web page can go back else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## accessForward

```TypeScript
accessForward(): boolean
```

Checks whether the web page can go forward.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-accessForward(): boolean--><!--Device-WebviewController-accessForward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the web page can go forward else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## accessStep

```TypeScript
accessStep(step: int): boolean
```

Checks whether the web page can go back or forward the given number of steps.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-accessStep(step: int): boolean--><!--Device-WebviewController-accessStep(step: int): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | int | 是 | The number of steps. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the web page can go back else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## addIntelligentTrackingPreventionBypassingList

```TypeScript
static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

Add bypassing hosts for Intelligent Tracking Prevention.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void--><!--Device-WebviewController-static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | 是 | Hosts that bypass the Intelligent Tracking Prevention. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## avoidVisibleViewportBottom

```TypeScript
avoidVisibleViewportBottom(avoidHeight: int): void
```

Sets the bottom avoidance height of the web visible viewport. When setting non-zero height, the position and size of the web component remain unchanged, &lt;br&gt;and the visible viewport upward avoids avoidHeight, as manifested by the web page content raising avoidHeight. &lt;br&gt;This interface is generally used for customizing the bottom avoidance area, and it is not recommended for &lt;br&gt;simultaneous use with clicking the editable area of the web page showing the keyboard. &lt;br&gt;In this case, the keyboardAvoidMode will be OVERLAYS_CONTENT. When setting zero, web page content can be restored and the keyboardAvoidMode will be the value set by keyboardAvoidMode().

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-avoidVisibleViewportBottom(avoidHeight: int): void--><!--Device-WebviewController-avoidVisibleViewportBottom(avoidHeight: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| avoidHeight | int | 是 | the height value of the visible viewport avoidance. The valid interval of avoidHeight is [0, the height of web component]. When avoidHeight is out of the valid interval, it takes the boundary value of the interval. &lt;br&gt;Unit: vp. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## backOrForward

```TypeScript
backOrForward(step: int): void
```

Goes forward or back backOrForward in the history of the web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-backOrForward(step: int): void--><!--Device-WebviewController-backOrForward(step: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | int | 是 | Steps to go forward or backward. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## backward

```TypeScript
backward(): void
```

Goes back in the history of the web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-backward(): void--><!--Device-WebviewController-backward(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearBlanklessLoadingCache

```TypeScript
static clearBlanklessLoadingCache(keys?: Array<string>) : void
```

Clears the blankless loading cache of the page with a specified key value.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static clearBlanklessLoadingCache(keys?: Array<string>) : void--><!--Device-WebviewController-static clearBlanklessLoadingCache(keys?: Array<string>) : void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 否 | The list of key values of pages cached in the blankless loading solution. These key values are specified in getBlanklessInfoKey. The default value is the list of key values of all pages cached in the blankless loading solution. The key length cannot exceed 2048 characters, and the number of keys must be less than or equal to 100. The URL is the same as that input to the Web component during page loading. When the key length exceeds 2048 characters, the key does not take effect. When the number of keys exceeds 100, the first 100 keys are used. If these parameters are left empty, the default values are used. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. @static |

## clearClientAuthenticationCache

```TypeScript
clearClientAuthenticationCache(): void
```

Clears the client authentication certificate cache in the Web.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-clearClientAuthenticationCache(): void--><!--Device-WebviewController-clearClientAuthenticationCache(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearHistory

```TypeScript
clearHistory(): void
```

Clears the history in the Web.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-clearHistory(): void--><!--Device-WebviewController-clearHistory(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearHostIP

```TypeScript
static clearHostIP(hostName: string): void
```

Clear the host name IP address.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static clearHostIP(hostName: string): void--><!--Device-WebviewController-static clearHostIP(hostName: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostName | string | 是 | Which host name to be cleared. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## clearIntelligentTrackingPreventionBypassingList

```TypeScript
static clearIntelligentTrackingPreventionBypassingList(): void
```

Clear bypassing hosts for Intelligent Tracking Prevention.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static clearIntelligentTrackingPreventionBypassingList(): void--><!--Device-WebviewController-static clearIntelligentTrackingPreventionBypassingList(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## clearMatches

```TypeScript
clearMatches(): void
```

Clears the highlighting surrounding text matches created by searchAllAsync.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-clearMatches(): void--><!--Device-WebviewController-clearMatches(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearPrefetchedResource

```TypeScript
static clearPrefetchedResource(cacheKeyList: Array<string>): void
```

Clears the cache of prefetched resources based on the specified cache key list. The cache key in the input parameter must be the prefetched resource cache key specified by API[prefetchResource](#prefetchResource).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static clearPrefetchedResource(cacheKeyList: Array<string>): void--><!--Device-WebviewController-static clearPrefetchedResource(cacheKeyList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cacheKeyList | Array&lt;string&gt; | 是 | The keys for memory cache. The key in cacheKeyList only support number and letters. |

## clearServiceWorkerWebSchemeHandler

```TypeScript
static clearServiceWorkerWebSchemeHandler(): void
```

Clear all web service worker scheme handlers.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static clearServiceWorkerWebSchemeHandler(): void--><!--Device-WebviewController-static clearServiceWorkerWebSchemeHandler(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## clearSslCache

```TypeScript
clearSslCache(): void
```

Clears the ssl cache in the Web.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-clearSslCache(): void--><!--Device-WebviewController-clearSslCache(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearWebSchemeHandler

```TypeScript
clearWebSchemeHandler(): void
```

Clear all web scheme handlers for related web component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-clearWebSchemeHandler(): void--><!--Device-WebviewController-clearWebSchemeHandler(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## closeAllMediaPresentations

```TypeScript
closeAllMediaPresentations(): void
```

控制网页所有全屏视频关闭。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-closeAllMediaPresentations(): void--><!--Device-WebviewController-closeAllMediaPresentations(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## closeCamera

```TypeScript
closeCamera(): void
```

关闭当前网页摄像头捕获。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-closeCamera(): void--><!--Device-WebviewController-closeCamera(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## constructor

```TypeScript
constructor(webTag?: string)
```

A constructor used to create a WebviewController object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-constructor(webTag?: string)--><!--Device-WebviewController-constructor(webTag?: string)-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webTag | string | 否 | specified the name of the web component, Empty by default. |

## createPdf

```TypeScript
createPdf(configuration: PdfConfiguration, callback: AsyncCallback<PdfData>): void
```

Rendering current Web page into Pdf data, return the result in async mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-createPdf(configuration: PdfConfiguration, callback: AsyncCallback<PdfData>): void--><!--Device-WebviewController-createPdf(configuration: PdfConfiguration, callback: AsyncCallback<PdfData>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | [PdfConfiguration](arkts-na-webview-pdfconfiguration-i.md) | 是 | configuration for createPdf, including page width and height, etc. {@Link PdfConfiguration} |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[PdfData](arkts-na-webview-pdfdata-c.md)&gt; | 是 | Callbacks execute createPdf results. PdfData is pdf data stream of current web page in Uint8Array {@Link PdfData}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## createPdf

```TypeScript
createPdf(configuration: PdfConfiguration): Promise<PdfData>
```

Rendering current Web page into Pdf data, return the result in promise mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-createPdf(configuration: PdfConfiguration): Promise<PdfData>--><!--Device-WebviewController-createPdf(configuration: PdfConfiguration): Promise<PdfData>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | [PdfConfiguration](arkts-na-webview-pdfconfiguration-i.md) | 是 | configuration for createPdf, including page width and height, etc. {@Link PdfConfiguration} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PdfData](arkts-na-webview-pdfdata-c.md)&gt; | The promise returned by the function. PdfData is pdf data stream of current web page in Uint8Array { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## createWebMessagePorts

```TypeScript
createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>
```

Create web message ports

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>--><!--Device-WebviewController-createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isExtentionType | boolean | 否 | Set whether the web message port supports extention type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[WebMessagePort](arkts-na-webview-webmessageport-i.md)&gt; | An array represent 2 WebMessagePort, then can use those ports to communication with html pages. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## createWebPrintDocumentAdapter

```TypeScript
createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter
```

Creates a PrintDocumentAdapter instance to provide content for printing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter--><!--Device-WebviewController-createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobName | string | 是 | Name of the file to print. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| print.PrintDocumentAdapter | Return PrintDocumentAdapter instance created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>): void
```

Register Web custom schemes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>): void--><!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemes | Array&lt;[WebCustomScheme](arkts-na-webview-webcustomscheme-i.md)&gt; | 是 | Configuration of web custom scheme. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100020](../../apis-arkweb/errorcode-webview.md#17100020-注册自定义协议失败) | Failed to register custom schemes. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void
```

Register Web custom schemes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void--><!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemes | Array&lt;[WebCustomScheme](arkts-na-webview-webcustomscheme-i.md)&gt; | 是 | Configuration of web custom scheme. |
| lazyInitWebEngine | boolean | 是 | When true: The interface internally skips initializing WebEngine and temporarily stores the registered schemes, which will be passed to WebEngine when it actually initializes. When false: The interface automatically performs WebEngine initialization internally. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100020](../../apis-arkweb/errorcode-webview.md#17100020-注册自定义协议失败) | Failed to register custom schemes. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. The length of the schemes array is greater than 10. 2. The character length of the scheme is greater than 32. 3. The character in the scheme is not within the allowed range of lowercase English letters, numbers, and the symbols ".", "+", "-". @static |

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string): void
```

Deletes a registered JavaScript object with given name.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-deleteJavaScriptRegister(name: string): void--><!--Device-WebviewController-deleteJavaScriptRegister(name: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | The name of a registered JavaScript object to be deleted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100008](../../apis-arkweb/errorcode-webview.md#17100008-删除不存在的javascriptproxy) | Failed to delete JavaScriptProxy because it does not exist. |

## enableAdsBlock

```TypeScript
enableAdsBlock(enable: boolean): void
```

Enable the ability to block Ads, disabled by default.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-enableAdsBlock(enable: boolean): void--><!--Device-WebviewController-enableAdsBlock(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Parameter string is too long. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## enableAdvancedSecurityMode

```TypeScript
static enableAdvancedSecurityMode(securityParams: SecurityParams): void
```

Enable the application disable some features such as PDFViewer to enhance the security level of web application

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-static enableAdvancedSecurityMode(securityParams: SecurityParams): void--><!--Device-WebviewController-static enableAdvancedSecurityMode(securityParams: SecurityParams): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| securityParams | [SecurityParams](arkts-na-webview-securityparams-i.md) | 是 | The options means which supported option or item will be disabled. |

## enableBackForwardCache

```TypeScript
static enableBackForwardCache(features?: BackForwardCacheSupportedFeatures): void
```

Enable the BackForwardCache and indicate features that are allowed to enter BackForwardCache. Default is disabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static enableBackForwardCache(features?: BackForwardCacheSupportedFeatures): void--><!--Device-WebviewController-static enableBackForwardCache(features?: BackForwardCacheSupportedFeatures): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| features | [BackForwardCacheSupportedFeatures](arkts-na-webview-backforwardcachesupportedfeatures-c.md) | 否 | The features that supports BackForwardCache. @static |

## enableIntelligentTrackingPrevention

```TypeScript
enableIntelligentTrackingPrevention(enable: boolean): void
```

Enable the ability to use Intelligent Tracking Prevention; default is disabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-enableIntelligentTrackingPrevention(enable: boolean): void--><!--Device-WebviewController-enableIntelligentTrackingPrevention(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## enablePrivateNetworkAccess

```TypeScript
static enablePrivateNetworkAccess(enable: boolean): void
```

After enable PrivateNetworkAccess feature, ArkWeb will send a CORS preflight request before issuing any sub-resource private network requests to request explicit permission from the target server. After disable PrivateNetworkAccess, ArkWeb will no longer check whether the private network request is legitimate.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static enablePrivateNetworkAccess(enable: boolean): void--><!--Device-WebviewController-static enablePrivateNetworkAccess(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | {@code true} enable the private network access check; {@code false} otherwise. @static |

## enableSafeBrowsing

```TypeScript
enableSafeBrowsing(enable: boolean): void
```

Enable the ability to check website security risks. Illegal and fraudulent websites are mandatory enabled and can't be disabled by this function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-enableSafeBrowsing(enable: boolean): void--><!--Device-WebviewController-enableSafeBrowsing(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | {@code true} enable check the website security risks; {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

## enableWholeWebPageDrawing

```TypeScript
static enableWholeWebPageDrawing(): void
```

Enables the full drawing capability for the web page. This API works only during Web component initialization.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static enableWholeWebPageDrawing(): void--><!--Device-WebviewController-static enableWholeWebPageDrawing(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## forward

```TypeScript
forward(): void
```

Goes forward in the history of the web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-forward(): void--><!--Device-WebviewController-forward(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getActiveWebEngineVersion

```TypeScript
static getActiveWebEngineVersion(): ArkWebEngineVersion
```

获取当前ArkWeb内核版本。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static getActiveWebEngineVersion(): ArkWebEngineVersion--><!--Device-WebviewController-static getActiveWebEngineVersion(): ArkWebEngineVersion-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArkWebEngineVersion](arkts-na-webview-arkwebengineversion-e.md) | 返回由[ArkWebEngineVersion]{ |

## getAttachState

```TypeScript
getAttachState(): ControllerAttachState
```

Get whether webviewController is attached to a web component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getAttachState(): ControllerAttachState--><!--Device-WebviewController-getAttachState(): ControllerAttachState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ControllerAttachState](arkts-na-webview-controllerattachstate-e.md) | the attach state of controller |

## getBackForwardEntries

```TypeScript
getBackForwardEntries(): BackForwardList
```

Get back forward stack list from current webview.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getBackForwardEntries(): BackForwardList--><!--Device-WebviewController-getBackForwardEntries(): BackForwardList-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BackForwardList](arkts-na-webview-backforwardlist-i.md) | Back forward list for current webview. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getBlanklessInfoWithKey

```TypeScript
getBlanklessInfoWithKey(key: string) : BlanklessInfo
```

Obtains the prediction information about the blankless loading solution and enables the generation of the transition frame for the current loading. The application determines whether to enable the blankless loading solution based on the information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getBlanklessInfoWithKey(key: string) : BlanklessInfo--><!--Device-WebviewController-getBlanklessInfoWithKey(key: string) : BlanklessInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | The key value that uniquely identifies the page. Default value: N/A. The value cannot be empty or exceed 2048 characters. When an invalid value is set, this API does not take effect. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BlanklessInfo](arkts-na-webview-blanklessinfo-i.md) | The prediction information about the blankless loading solution. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## getCertificate

```TypeScript
getCertificate(): Promise<Array<cert.X509Cert>>
```

Get certificate for the current website.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getCertificate(): Promise<Array<cert.X509Cert>>--><!--Device-WebviewController-getCertificate(): Promise<Array<cert.X509Cert>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;cert.X509Cert&gt;&gt; | the promise of the current website's certificate. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a web component. |

## getCertificate

```TypeScript
getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void
```

Get certificate for the current website.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void--><!--Device-WebviewController-getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;cert.X509Cert&gt;&gt; | 是 | the callback of getCertificate. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a web component. |

## getCustomUserAgent

```TypeScript
getCustomUserAgent(): string
```

Get custom user agent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getCustomUserAgent(): string--><!--Device-WebviewController-getCustomUserAgent(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Get custom User agent information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getDefaultUserAgent

```TypeScript
static getDefaultUserAgent(): string
```

Get the default user agent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static getDefaultUserAgent(): string--><!--Device-WebviewController-static getDefaultUserAgent(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The default user agent string. |

## getErrorPageEnabled

```TypeScript
getErrorPageEnabled(): boolean
```

Get whether default error page feature is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getErrorPageEnabled(): boolean--><!--Device-WebviewController-getErrorPageEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if enable the default error page feature; else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getFavicon

```TypeScript
getFavicon(): image.PixelMap
```

Gets the favicon of current Web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getFavicon(): image.PixelMap--><!--Device-WebviewController-getFavicon(): image.PixelMap-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | Return the favicon bitmap of the current page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getLastHitTest

```TypeScript
getLastHitTest(): HitTestValue
```

Gets the last hit test value of HitTest.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getLastHitTest(): HitTestValue--><!--Device-WebviewController-getLastHitTest(): HitTestValue-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HitTestValue](arkts-na-webview-hittestvalue-i.md) | Return the element information of the clicked area. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getLastJavascriptProxyCallingFrameUrl

```TypeScript
getLastJavascriptProxyCallingFrameUrl(): string
```

Get the url of the last frame that calls the JavaScriptProxy. This should be called on the UI thread.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getLastJavascriptProxyCallingFrameUrl(): string--><!--Device-WebviewController-getLastJavascriptProxyCallingFrameUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The url of the last frame that calls the JavaScriptProxy. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getLastPostMessageURL

```TypeScript
getLastPostMessageURL(): string
```

Gets URL of frame that sent the last postMessage to native application.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-getLastPostMessageURL(): string--><!--Device-WebviewController-getLastPostMessageURL(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The URL of frame that last sent a postMessage. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getMediaPlaybackState

```TypeScript
getMediaPlaybackState(): MediaPlaybackState
```

查询当前网页音视频播放状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getMediaPlaybackState(): MediaPlaybackState--><!--Device-WebviewController-getMediaPlaybackState(): MediaPlaybackState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaPlaybackState](arkts-na-webview-mediaplaybackstate-e.md) | 当前网页的播放状态，具体值为NONE、PLAYING、PAUSED、STOPPED。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getOriginalUrl

```TypeScript
getOriginalUrl(): string
```

Gets the original url of current Web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getOriginalUrl(): string--><!--Device-WebviewController-getOriginalUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the original url of the current page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getPageHeight

```TypeScript
getPageHeight(): int
```

Obtains the height of this web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getPageHeight(): int--><!--Device-WebviewController-getPageHeight(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Height of the current web page. Unit: vp. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getPageOffset

```TypeScript
getPageOffset(): ScrollOffset
```

Get the page offset. And the unit is virtual pixel.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getPageOffset(): ScrollOffset--><!--Device-WebviewController-getPageOffset(): ScrollOffset-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScrollOffset](arkts-na-webview-scrolloffset-i.md) | page offset |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This functionality is not supported. |

## getPrintBackground

```TypeScript
getPrintBackground(): boolean
```

Get whether print web page background.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getPrintBackground(): boolean--><!--Device-WebviewController-getPrintBackground(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Get whether print web page background. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getProgress

```TypeScript
getProgress() : int
```

Gets the loading progress for the current page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getProgress() : int--><!--Device-WebviewController-getProgress() : int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The loading progress for the current page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## getRenderProcessMode

```TypeScript
static getRenderProcessMode(): RenderProcessMode
```

Get render process mode of the ArkWeb.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static getRenderProcessMode(): RenderProcessMode--><!--Device-WebviewController-static getRenderProcessMode(): RenderProcessMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderProcessMode](arkts-na-webview-renderprocessmode-e.md) | mode - The render process mode of the ArkWeb. Call { |

## getScrollOffset

```TypeScript
getScrollOffset(): ScrollOffset
```

Get the scroll offset of the webpage in view port, the coordinates of the top left corner of the view port are X: 0, Y: 0. And the unit is virtual pixel.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getScrollOffset(): ScrollOffset--><!--Device-WebviewController-getScrollOffset(): ScrollOffset-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScrollOffset](arkts-na-webview-scrolloffset-i.md) | scroll offset |

## getScrollable

```TypeScript
getScrollable(): boolean
```

Get whether scrolling is allowed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getScrollable(): boolean--><!--Device-WebviewController-getScrollable(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Get scrolling is allowed information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getSecurityLevel

```TypeScript
getSecurityLevel(): SecurityLevel
```

Get the security level of the current page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getSecurityLevel(): SecurityLevel--><!--Device-WebviewController-getSecurityLevel(): SecurityLevel-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SecurityLevel | the security level of current page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getSiteIsolationMode

```TypeScript
static getSiteIsolationMode(): SiteIsolationMode
```

Get the site isolation mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static getSiteIsolationMode(): SiteIsolationMode--><!--Device-WebviewController-static getSiteIsolationMode(): SiteIsolationMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SiteIsolationMode](arkts-na-webview-siteisolationmode-e.md) | The site isolation mode of the application. |

## getSurfaceId

```TypeScript
getSurfaceId(): string
```

Get the ID of the surface created by ArkWeb. This ID can be used for web page screenshots.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getSurfaceId(): string--><!--Device-WebviewController-getSurfaceId(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The ID of the surface created by ArkWeb. |

## getTitle

```TypeScript
getTitle(): string
```

Gets the title of current Web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getTitle(): string--><!--Device-WebviewController-getTitle(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return to File Selector Title. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getUrl

```TypeScript
getUrl(): string
```

Gets the url of current Web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getUrl(): string--><!--Device-WebviewController-getUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the url of the current page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getUserAgent

```TypeScript
getUserAgent(): string
```

Gets the default user agent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getUserAgent(): string--><!--Device-WebviewController-getUserAgent(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return user agent information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getUserAgentClientHintsEnabled

```TypeScript
static getUserAgentClientHintsEnabled(): boolean
```

Get if the User-Agent Client Hints enabled.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-static getUserAgentClientHintsEnabled(): boolean--><!--Device-WebviewController-static getUserAgentClientHintsEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If User-Agent Client Hints was enabled. |

## getUserAgentMetadata

```TypeScript
getUserAgentMetadata(userAgent: string): UserAgentMetadata
```

Get the User-Agent metadata corresponding to the User-Agent.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-getUserAgentMetadata(userAgent: string): UserAgentMetadata--><!--Device-WebviewController-getUserAgentMetadata(userAgent: string): UserAgentMetadata-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UserAgentMetadata](arkts-na-webview-useragentmetadata-c.md) | The UserAgentMetadata for the userAgent. |

## getWebId

```TypeScript
getWebId(): int
```

Gets the index value of the current Web component for the management of multiple Web components.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-getWebId(): int--><!--Device-WebviewController-getWebId(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns the index value of the current Web component. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(): Promise<boolean>
```

通过Promise方式异步查找当前页面是否存在图像。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-hasImage(): Promise<boolean>--><!--Device-WebviewController-hasImage(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise实例，返回查找页面是否存在图像。 &lt;br&gt; true表示页面存在图像；false表示页面不存在图像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(callback: AsyncCallback<boolean>): void
```

通过Callback方式异步查找当前页面是否存在图像。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-hasImage(callback: AsyncCallback<boolean>): void--><!--Device-WebviewController-hasImage(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 返回查找页面是否存在图像。&lt;br&gt; true表示页面存在图像；false表示页面不存在图像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## initializeWebEngine

```TypeScript
static initializeWebEngine(): void
```

Initialize the web engine before loading the Web components. This is a global static API that must be called on the UI thread, and it will have no effect if any Web components are loaded.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static initializeWebEngine(): void--><!--Device-WebviewController-static initializeWebEngine(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## injectOfflineResources

```TypeScript
injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void
```

Inject offline resources into cache.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void--><!--Device-WebviewController-injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceMaps | Array&lt;[OfflineResourceMap](arkts-na-webview-offlineresourcemap-i.md)&gt; | 是 | Array of offline resource info maps. The count of array must between 1 and 30. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2 *1024 *1024. |

## isActiveWebEngineEvergreen

```TypeScript
static isActiveWebEngineEvergreen(): boolean
```

判断当前系统是否正在使用常青内核，即系统的最新内核。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static isActiveWebEngineEvergreen(): boolean--><!--Device-WebviewController-static isActiveWebEngineEvergreen(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否正在使用常青内核。正在使用返回true，否则返回false。 |

## isAdsBlockEnabled

```TypeScript
isAdsBlockEnabled(): boolean
```

Get whether Ads block is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-isAdsBlockEnabled(): boolean--><!--Device-WebviewController-isAdsBlockEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the ability of AdsBlock is enabled; else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## isAdsBlockEnabledForCurPage

```TypeScript
isAdsBlockEnabledForCurPage(): boolean
```

Get whether Ads block is enabled for current Webpage.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-isAdsBlockEnabledForCurPage(): boolean--><!--Device-WebviewController-isAdsBlockEnabledForCurPage(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the ability of AdsBlock is enabled for current Webpage; else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## isAutoPreconnectEnabled

```TypeScript
static isAutoPreconnectEnabled(): boolean
```

‌Retrieve whether the automatic pre-connection feature is enabled‌.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static isAutoPreconnectEnabled(): boolean--><!--Device-WebviewController-static isAutoPreconnectEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return true if enabled, false if disabled. |

## isIncognitoMode

```TypeScript
isIncognitoMode(): boolean
```

Whether the incognito mode is set.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-isIncognitoMode(): boolean--><!--Device-WebviewController-isIncognitoMode(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## isIntelligentTrackingPreventionEnabled

```TypeScript
isIntelligentTrackingPreventionEnabled(): boolean
```

Get whether Intelligent Tracking Prevention is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-isIntelligentTrackingPreventionEnabled(): boolean--><!--Device-WebviewController-isIntelligentTrackingPreventionEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if enable the Intelligent Tracking Prevention; else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## isPrivateNetworkAccessEnabled

```TypeScript
static isPrivateNetworkAccessEnabled(): boolean
```

Get whether PrivateNetworkAccess is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static isPrivateNetworkAccessEnabled(): boolean--><!--Device-WebviewController-static isPrivateNetworkAccessEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True is enable the ability to check private network access else false. |

## isSafeBrowsingEnabled

```TypeScript
isSafeBrowsingEnabled(): boolean
```

Get whether checking website security risks is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-isSafeBrowsingEnabled(): boolean--><!--Device-WebviewController-isSafeBrowsingEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if enable the ability to check website security risks else false. |

## loadData

```TypeScript
loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void
```

Loads the data or URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void--><!--Device-WebviewController-loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | A string encoded according to "Base64" or "URL". |
| mimeType | string | 是 | Media type. For example: "text/html". |
| encoding | string | 是 | Encoding type. For example: "UTF-8". |
| baseUrl | string | 否 | A specified URL path ("http"/"https"/"data" protocol), which is assigned to window.origin by the Web component. |
| historyUrl | string | 否 | History URL. When it is not empty, it can be managed by history records to realize the back and forth function. This property is invalid when baseUrl is empty. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## loadUrl

```TypeScript
loadUrl(url: string | Resource, headers?: Array<WebHeader>): void
```

Loads the data or URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-loadUrl(url: string | Resource, headers?: Array<WebHeader>): void--><!--Device-WebviewController-loadUrl(url: string | Resource, headers?: Array<WebHeader>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | The URL to load. |
| headers | Array&lt;WebHeader&gt; | 否 | Additional HTTP request header for URL. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid. |
| [17100003](../../apis-arkweb/errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## offControllerAttachStateChange

```TypeScript
offControllerAttachStateChange(callback?: Callback<ControllerAttachState>): void
```

Unregister the callback for controller attach state change.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-offControllerAttachStateChange(callback?: Callback<ControllerAttachState>): void--><!--Device-WebviewController-offControllerAttachStateChange(callback?: Callback<ControllerAttachState>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ControllerAttachState](arkts-na-webview-controllerattachstate-e.md)&gt; | 否 | Callback used to return the controller attach state. |

## onActive

```TypeScript
onActive(): void
```

Call this interface to notify the Web component to enter the foreground activation state. The activation state is the state in which the application interacts with the user. The application will remain in this state until something happens, such as receiving an incoming call or closing the screen of the device, to shift the focus away from the application.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-onActive(): void--><!--Device-WebviewController-onActive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## onControllerAttachStateChange

```TypeScript
onControllerAttachStateChange(callback: Callback<ControllerAttachState>): void
```

Register the callback for controller attach state change.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-onControllerAttachStateChange(callback: Callback<ControllerAttachState>): void--><!--Device-WebviewController-onControllerAttachStateChange(callback: Callback<ControllerAttachState>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ControllerAttachState](arkts-na-webview-controllerattachstate-e.md)&gt; | 是 | Callback used to return the controller attach state. |

## onCreateNativeMediaPlayer

```TypeScript
onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void
```

注册回调函数，开启 [应用接管网页媒体播放功能](../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#enablenativemediaplayer12) 后，当网页中有播放媒体时，触发注册的回调函数。 如果应用接管网页媒体播放功能未开启，则注册的回调函数不会被触发。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void--><!--Device-WebviewController-onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [CreateNativeMediaPlayerCallback](arkts-na-webview-createnativemediaplayercallback-t.md) | 是 | 接管网页媒体播放的回调函数。 |

## onInactive

```TypeScript
onInactive(): void
```

Call this interface to notify the Web component to enter the inactive state. In this callback, the developer can realize the appropriate behavior when the application loses focus. In this state, any content that can be safely paused will be paused as much as possible, such as animation and geographical location. However, JavaScript will not be paused. To pause JavaScript globally, please use [pauseAllTimers](#pauseAllTimers).To reactivate the Web component, call onActive.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-onInactive(): void--><!--Device-WebviewController-onInactive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pageDown

```TypeScript
pageDown(bottom: boolean): void
```

Scroll the contents of this Webview down by half the view size.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-pageDown(bottom: boolean): void--><!--Device-WebviewController-pageDown(bottom: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bottom | boolean | 是 | Whether to jump to the bottom of the page, if set to false, the page content will scroll down half the size of the view frame, and when set to true, it will jump to the bottom of the page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pageUp

```TypeScript
pageUp(top: boolean): void
```

Scroll the contents of this Webview up by half the view size.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-pageUp(top: boolean): void--><!--Device-WebviewController-pageUp(top: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| top | boolean | 是 | Whether to jump to the top of the page, if set to false, the page content will scroll up half the size of the view frame, and when set to true, it will jump to the top of the page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pauseAllMedia

```TypeScript
pauseAllMedia(): void
```

控制网页所有音视频暂停。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-pauseAllMedia(): void--><!--Device-WebviewController-pauseAllMedia(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pauseAllTimers

```TypeScript
static pauseAllTimers(): void
```

Pause all WebView timers.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static pauseAllTimers(): void--><!--Device-WebviewController-static pauseAllTimers(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pauseMicrophone

```TypeScript
pauseMicrophone(): void
```

暂停当前网页麦克风捕获。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-pauseMicrophone(): void--><!--Device-WebviewController-pauseMicrophone(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## postMessage

```TypeScript
postMessage(name: string, ports: Array<WebMessagePort>, uri: string): void
```

Post web message port to html

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-postMessage(name: string, ports: Array<WebMessagePort>, uri: string): void--><!--Device-WebviewController-postMessage(name: string, ports: Array<WebMessagePort>, uri: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Data name information to send. |
| ports | Array&lt;[WebMessagePort](arkts-na-webview-webmessageport-i.md)&gt; | 是 | Port number array information to send. |
| uri | string | 是 | URI to receive this information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## postUrl

```TypeScript
postUrl(url: string, postData: ArrayBuffer): void
```

Loads the URL use "POST" method with post data.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-postUrl(url: string, postData: ArrayBuffer): void--><!--Device-WebviewController-postUrl(url: string, postData: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | Request the URL use "POST" method. |
| postData | ArrayBuffer | 是 | This data will passed to "POST" request. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid. |

## precompileJavaScript

```TypeScript
precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<int>
```

Compile javascript and generate code cache.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<int>--><!--Device-WebviewController-precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<int>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | Url of the javascript. Only support HTTP/HTTPS protocol and length no longer than 2048. |
| script | string \| Uint8Array | 是 | Javascript source code. script must not be empty. |
| cacheOptions | [CacheOptions](arkts-na-webview-cacheoptions-i.md) | 是 | Generate code cache option. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | The promise returned by the function. 0 means generate code cache successfully, -1 means internal error. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void
```

Prefetch the resources required by the page, but will not execute js or render the page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void--><!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | Which url to preresolve/preconnect. |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | Additional HTTP request header of the URL. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024. |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void
```

Prefetch the resources required by the page, but will not execute js or render the page. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; ‌prefetchPage‌ does not cache resources with Cache-Control: no-store by default, and only allows one prefetch within 500ms. Prefetch behavior can be customized via ‌prefetchOptions‌, including ignoring Cache-Control: no-store and adjusting the throttling interval.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void--><!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | Which url to preresolve/preconnect. |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | Additional HTTP request header of the URL. |
| prefetchOptions | [PrefetchOptions](arkts-na-webview-prefetchoptions-c.md) | 否 | Prefetch behavior can be customized via ‌prefetchOptions‌, including ignoring Cache-Control: no-store and adjusting the throttling interval. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024. |

## prefetchResource

```TypeScript
static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,
        cacheValidTime?: int): void
```

Prefetches resource requests based on specified request information and additional HTTP request headers, saves the requests to the memory cache, and specifies the cache key and validity period to accelerate loading. Currently, only POST requests whose Content-Type is application/x-www-form-urlencoded are supported. A maximum of six POST requests can be pre-obtained. To prefetch the seventh post request, call API[clearPrefetchedResource](#clearPrefetchedResource) to clear the cache of unnecessary post requests. Otherwise, the cache of the earliest prefetched POST request will be automatically cleared. To use the prefetched resource cache, you need to add the key value ArkWebPostCacheKey to the header of the POST request. The content of the key value is the cacheKey of the corresponding cache.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,        cacheValidTime?: int): void--><!--Device-WebviewController-static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,        cacheValidTime?: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | RequestInfo | 是 | The information of the request. |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | Additional HTTP request header of the request. |
| cacheKey | string | 否 | The key for memory cache. Default value is the url of the request. Only support number and letters. |
| cacheValidTime | int | 否 | The valid time of the cache for request, ranges greater than 0. The unit is second. Default value is 300s. The value of cacheValidTime must between 1 and 2147483647. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2 *1024 *1024. |

## prepareForPageLoad

```TypeScript
static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: int): void
```

Preresolve or Preconnect the url. This API can be called before loading the url to make loading faster.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: int): void--><!--Device-WebviewController-static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | Which url to preresolve/preconnect. |
| preconnectable | boolean | 是 | Indicates whether to preconnect. |
| numSockets | int | 是 | If preconnectable is true, this parameter indicates the number of sockets to be preconnected. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2048. |
| [17100013](../../apis-arkweb/errorcode-webview.md#17100013-预连接时输入socket数目无效) | The number of preconnect sockets is invalid. |

## refresh

```TypeScript
refresh(): void
```

Refreshes the current URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-refresh(): void--><!--Device-WebviewController-refresh(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## refresh

```TypeScript
refresh(ignoreCache: boolean): void
```

Refreshes the current URL.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-refresh(ignoreCache: boolean): void--><!--Device-WebviewController-refresh(ignoreCache: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ignoreCache | boolean | 是 | If set to true, it indicates an end-to-end request with "pragma: no-cache"; otherwise, it performs a normal refresh. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,
            asyncMethodList?: Array<string>, permission?: string): void
```

Registers the supplied ArkTS object into this Web component. The object is registered into all frames of the web page, including all iframes, using the specified name. This allows the methods of the ArkTS object to be accessed from JavaScript. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; Registed objects will not appear in JavaScript until the page is next (re)load. To avoid memory leaks, registerJavaScriptProxy must be used together with deleteJavaScriptProxy. To avoid security risks, it is recommended that registerJavaScriptProxy be used with trusted web components. If the same method is registered repeatedly in both synchronous and asynchronous list, it will default to an asynchronous method. The synchronous function list and asynchronous function list cannot be empty at the same time.&lt;br&gt; otherwise, this registration will fail. &lt;p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,            asyncMethodList?: Array<string>, permission?: string): void--><!--Device-WebviewController-registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,            asyncMethodList?: Array<string>, permission?: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jsObject | object | 是 | Application side JavaScript objects participating in registration. |
| name | string | 是 | The name of the registered object, which is consistent with the object name called in the window. |
| methodList | Array&lt;string&gt; | 是 | The method of the application side JavaScript object participating in the registration. |
| asyncMethodList | Array&lt;string&gt; | 否 | The async method of the application side JavaScript object participating in the registration. |
| permission | string | 否 | permission configuration defining web page URLs that can access JavaScriptProxy methods. The configuration can be defined at two levels, object level and method level. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## removeAllCache

```TypeScript
static removeAllCache(clearRom: boolean): void
```

Remove resource cache in application. So this method will remove all cache for all web components in the same application.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static removeAllCache(clearRom: boolean): void--><!--Device-WebviewController-static removeAllCache(clearRom: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearRom | boolean | 是 | Remove cache in both rom and ram if true. Otherwise only clear cache in ram. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

## removeCache

```TypeScript
removeCache(clearRom: boolean): void
```

Clears the cache in the application. This API will clear the cache for all webviews in the same application. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; You can view the Webview cache in the data/storage/el2/base/cache/web/Cache directory. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-removeCache(clearRom: boolean): void--><!--Device-WebviewController-removeCache(clearRom: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearRom | boolean | 是 | Whether to clear the cache in the ROM and RAM at the same time. {@code true} means to clear the cache in the ROM and RAM at the same time; {@code false} means to only clear the cache in the RAM. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## removeIntelligentTrackingPreventionBypassingList

```TypeScript
static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

Remove bypassing hosts for Intelligent Tracking Prevention.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void--><!--Device-WebviewController-static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | 是 | Hosts needs to remove from bypass list. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## requestFocus

```TypeScript
requestFocus(): void
```

Gets the request focus.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-requestFocus(): void--><!--Device-WebviewController-requestFocus(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## restoreWebState

```TypeScript
restoreWebState(state: Uint8Array): void
```

Restoring the web access stack, that is, the history of access.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-restoreWebState(state: Uint8Array): void--><!--Device-WebviewController-restoreWebState(state: Uint8Array): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | Uint8Array | 是 | Web access stack after serialization. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## resumeAllMedia

```TypeScript
resumeAllMedia(): void
```

控制网页被pauseAllMedia接口暂停的音视频继续播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-resumeAllMedia(): void--><!--Device-WebviewController-resumeAllMedia(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## resumeAllTimers

```TypeScript
static resumeAllTimers(): void
```

Resume all timers suspended from the pauseAllTimers() interface.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static resumeAllTimers(): void--><!--Device-WebviewController-static resumeAllTimers(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## resumeMicrophone

```TypeScript
resumeMicrophone(): void
```

恢复当前网页麦克风捕获。使用麦克风功能前请在module.json5中添加权限: ohos.permission.MICROPHONE，具体权限的添加方法请参考 [在配置文件中声明权限](../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-resumeMicrophone(): void--><!--Device-WebviewController-resumeMicrophone(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## runJavaScript

```TypeScript
runJavaScript(script: string): Promise<string>
```

Asynchronously execute JavaScript in the context of the currently displayed page. The result of the script execution will be returned through a via Promise. This method must be used on the UI thread, and the callback will also be invoked on the UI thread. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; The state of JavaScript is no longer persisted across navigations like loadUrl. For example, global variables and functions defined before calling loadUrl will not exist in the loaded page.&lt;br&gt; It is recommended that applications use registerJavaScriptProxy to ensure that the JavaScript state can be persisted across page navigations.&lt;br&gt; If you cannot obtain the return value by executing the asynchronous method, you need to determine whether to use synchronous or asynchronous mode based on the specific situation. &lt;p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-runJavaScript(script: string): Promise<string>--><!--Device-WebviewController-runJavaScript(script: string): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string | 是 | JavaScript Script. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | A promise is solved after the JavaScript script is executed. This parameter will be the result of JavaScript script execution. If the JavaScript script fails to execute or has no return value, null will be returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../../apis-arkweb/errorcode-webview.md#17100003-resource路径错误) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScript

```TypeScript
runJavaScript(script: string, callback: AsyncCallback<string>): void
```

Asynchronously execute JavaScript in the context of the currently displayed page. The result of the script execution will be returned through an asynchronous callback. This method must be used on the UI thread, and the callback will also be invoked on the UI thread. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; The state of JavaScript is no longer persisted across navigations like loadUrl. For example, global variables and functions defined before calling loadUrl will not exist in the loaded page. It is recommended that applications use registerJavaScriptProxy to ensure that the JavaScript state can be persisted across page navigations. &lt;p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-runJavaScript(script: string, callback: AsyncCallback<string>): void--><!--Device-WebviewController-runJavaScript(script: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string | 是 | JavaScript Script. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | Callbacks execute JavaScript script results. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../../apis-arkweb/errorcode-webview.md#17100003-resource路径错误) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>
```

Execute JavaScript code in the context of the currently displayed page, and return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>--><!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string \| ArrayBuffer | 是 | JavaScript Script. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[JsMessageExt](arkts-na-webview-jsmessageext-c.md)&gt; | A promise is solved after the JavaScript script is executed. This parameter will be the result of JavaScript script execution. If the JavaScript script fails to execute or has no return value, a none type value will be returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void
```

Execute JavaScript code in the context of the currently displayed page, and return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void--><!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string \| ArrayBuffer | 是 | JavaScript Script. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[JsMessageExt](arkts-na-webview-jsmessageext-c.md)&gt; | 是 | Callbacks execute JavaScript script results. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## scrollBy

```TypeScript
scrollBy(deltaX: double, deltaY: double, duration?: int): void
```

Scroll by the delta position within specified time.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-scrollBy(deltaX: double, deltaY: double, duration?: int): void--><!--Device-WebviewController-scrollBy(deltaX: double, deltaY: double, duration?: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deltaX | double | 是 | the delta x of the position &lt;br&gt;Unit: vp. |
| deltaY | double | 是 | the delta y of the position &lt;br&gt;Unit: vp. |
| duration | int | 否 | the scroll animation duration. &lt;br&gt;Unit: millisecond, The value range is all integers, If the value is not passed, or is negative or 0, there is no animation. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## scrollByWithResult

```TypeScript
scrollByWithResult(deltaX: double, deltaY: double): boolean
```

Scrolls by the specified delta position and returns a result indicating whether the scrolling operation was successful or not.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-scrollByWithResult(deltaX: double, deltaY: double): boolean--><!--Device-WebviewController-scrollByWithResult(deltaX: double, deltaY: double): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deltaX | double | 是 | the delta x of the position. The unit is vp |
| deltaY | double | 是 | the delta y of the position. The unit is vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true if the scroll operation is successful, otherwise false. Return value scenario: when the Web page is in the touch state, return false, otherwise return true. In the same layer rendering scene, when the same layer rendering area of ??the Web is in the touching state, the return value is true. In a nested scrolling scenario, calling scrollByWithResult will not trigger nested scrolling of the parent component. This interface does not guarantee sliding frame rate performance. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## scrollTo

```TypeScript
scrollTo(x: double, y: double, duration?: int): void
```

Scroll to the position within specified time.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-scrollTo(x: double, y: double, duration?: int): void--><!--Device-WebviewController-scrollTo(x: double, y: double, duration?: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | the x of the position &lt;br&gt;Unit: vp. |
| y | double | 是 | the y of the position &lt;br&gt;Unit: vp. |
| duration | int | 否 | the scroll animation duration. &lt;br&gt;Unit: millisecond, The value range is all integers, If the value is not passed, or is negative or 0, there is no animation. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## searchAllAsync

```TypeScript
searchAllAsync(searchString: string): void
```

Search all instances of 'searchString' on the page and highlights them, result will be notify through callback onSearchResultReceive.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-searchAllAsync(searchString: string): void--><!--Device-WebviewController-searchAllAsync(searchString: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchString | string | 是 | String to be search. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## searchNext

```TypeScript
searchNext(forward: boolean): void
```

Highlights and scrolls to the next match search.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-searchNext(forward: boolean): void--><!--Device-WebviewController-searchNext(forward: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forward | boolean | 是 | Step of search is back or forward. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## serializeWebState

```TypeScript
serializeWebState(): Uint8Array
```

Serialize the access stack of the web, that is, the history of access.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-serializeWebState(): Uint8Array--><!--Device-WebviewController-serializeWebState(): Uint8Array-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | Web access stack after serialization. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setActiveWebEngineVersion

```TypeScript
static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void
```

设置ArkWeb内核版本。若系统不支持指定版本，则设置无效。该接口为全局静态API，须在调用initializeWebEngine前执行，若已加载任何Web组件，则该设置无效。 > **说明：** > > - setActiveWebEngineVersion不支持在异步线程中调用。 > > - setActiveWebEngineVersion全局生效，在整个APP生命周期中调用一次即可，不需要重复调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void--><!--Device-WebviewController-static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| engineVersion | [ArkWebEngineVersion](arkts-na-webview-arkwebengineversion-e.md) | 是 | ArkWeb内核版本。 |

## setAppCustomUserAgent

```TypeScript
static setAppCustomUserAgent(userAgent: string) : void
```

Set the default User-Agent for the application. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; Unlike setCustomUserAgent, which only takes effect in the current web context, the priority for pages loaded in the web is as follows: 1. The User-Agent set by setCustomUserAgent is used first. 2. If not set, it will check whether a specific User-Agent has been assigned to the current page via setUserAgentForHosts. 3. If no specific User-Agent is assigned, the application will fall back to using the User-Agent set by setAppCustomUserAgent. 4. If the app's default User-Agent is also not specified, the web's default User-Agent will be used as the final fallback. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setAppCustomUserAgent(userAgent: string) : void--><!--Device-WebviewController-static setAppCustomUserAgent(userAgent: string) : void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. @static |

## setAudioMuted

```TypeScript
setAudioMuted(mute: boolean): void
```

设置网页静音。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setAudioMuted(mute: boolean): void--><!--Device-WebviewController-setAudioMuted(mute: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 表示是否将网页设置为静音状态。&lt;br&gt;true表示将网页设置为静音状态，false表示将网页取消静音状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setAutoPreconnect

```TypeScript
static setAutoPreconnect(enabled: boolean): void
```

Configure whether to enable automatic pre-connection to high-frequency URLs accessed during the application's previous lifecycle after web initialization.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setAutoPreconnect(enabled: boolean): void--><!--Device-WebviewController-static setAutoPreconnect(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Enable if true, disable if false. @static |

## setBackForwardCacheOptions

```TypeScript
setBackForwardCacheOptions(options?: BackForwardCacheOptions): void
```

Configure the BackForwardCache.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setBackForwardCacheOptions(options?: BackForwardCacheOptions): void--><!--Device-WebviewController-setBackForwardCacheOptions(options?: BackForwardCacheOptions): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [BackForwardCacheOptions](arkts-na-webview-backforwardcacheoptions-c.md) | 否 | The configuration of BackForwardCache. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setBlanklessLoadingCacheCapacity

```TypeScript
static setBlanklessLoadingCacheCapacity(capacity: int) : int
```

Sets the cache capacity of the blankless loading solution and returns the value that takes effect. If this API is not called, the default capacity 30 MB is used. The maximum capacity cannot exceed 100 MB.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setBlanklessLoadingCacheCapacity(capacity: int) : int--><!--Device-WebviewController-static setBlanklessLoadingCacheCapacity(capacity: int) : int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | int | 是 | Cache capacity, in MB. The maximum value is 100 MB. The default value is 30 MB. The value ranges from 0 to 100. If this parameter is set to 0, no cache capacity is available and the functionality is disabled globally. When the value is set to a number smaller than 0, the value 0 takes effect. When the value is set to a number greater than 100, the value 100 takes effect. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The effective value that ranges from 0 MB to 100 MB. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. @static |

## setBlanklessLoadingWithKey

```TypeScript
setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode
```

Sets whether to enable blankless page loading. This API must be used in pair with the getBlanklessInfoWithKey API.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode--><!--Device-WebviewController-setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | The key value that uniquely identifies the current page. It must be the same as the key value of the getBlanklessInfoWithKey API. Default value: N/A. The value cannot be empty or exceed 2048 characters. When an invalid value is set, the error code WebBlanklessErrorCode is returned, and the API does not take effect. |
| is_start | boolean | 是 | Whether to enable frame interpolation. The value true indicates to enable frame interpolation, and the value false indicates the opposite. The default value is false. The value can be true or false. Action for setting an invalid value: N/A. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebBlanklessErrorCode](arkts-na-webview-webblanklesserrorcode-e.md) | WebBlanklessErrorCode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## setBlanklessLoadingWithParams

```TypeScript
setBlanklessLoadingWithParams(key: string,
            param: BlanklessLoadingParam) : WebBlanklessErrorCode
```

Triggers frame interpolation and sets frame interpolation parameters. This API must be used in pair with the getBlanklessInfoWithKey API. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-setBlanklessLoadingWithParams(key: string,            param: BlanklessLoadingParam) : WebBlanklessErrorCode--><!--Device-WebviewController-setBlanklessLoadingWithParams(key: string,            param: BlanklessLoadingParam) : WebBlanklessErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | Key value that uniquely identifies the current page. The key value must be the same as that of getBlanklessInfoWithKey. &lt;br&gt;Value range: (0, 2048] &lt;br&gt;Value range: (0, 2048] &lt;br&gt;which must be the same as the key value in getBlanklessInfoWithKey |
| param | [BlanklessLoadingParam](arkts-na-webview-blanklessloadingparam-i.md) | 是 | The parameter of blankless. For details see {@Link BlanklessLoadingParam}. &lt;br&gt;na |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebBlanklessErrorCode](arkts-na-webview-webblanklesserrorcode-e.md) | WebBlanklessErrorCode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## setConnectionTimeout

```TypeScript
static setConnectionTimeout(timeout: int): void
```

Set web engine socket connection timeout. Unit: seconds.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setConnectionTimeout(timeout: int): void--><!--Device-WebviewController-static setConnectionTimeout(timeout: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | int | 是 | Socket connection timeout. The value should be an integer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3. Parameter verification failed. |

## setCustomUserAgent

```TypeScript
setCustomUserAgent(userAgent: string): void
```

Set custom user agent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setCustomUserAgent(userAgent: string): void--><!--Device-WebviewController-setCustomUserAgent(userAgent: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | User custom agent information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setDownloadDelegate

```TypeScript
setDownloadDelegate(delegate: WebDownloadDelegate): void
```

Set delegate for download. Used to notify the progress of the download triggered from web.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setDownloadDelegate(delegate: WebDownloadDelegate): void--><!--Device-WebviewController-setDownloadDelegate(delegate: WebDownloadDelegate): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | [WebDownloadDelegate](arkts-na-webview-webdownloaddelegate-c.md) | 是 | Delegate used for download triggered from web. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setErrorPageEnabled

```TypeScript
setErrorPageEnabled(enable: boolean): void
```

Set whether enable the error page. onOverrideErrorPage will be triggered when the page error.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setErrorPageEnabled(enable: boolean): void--><!--Device-WebviewController-setErrorPageEnabled(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Whether to enable the default error page feature. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setHostIP

```TypeScript
static setHostIP(hostName: string, address: string, aliveTime: int): void
```

Set IP address for host name.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setHostIP(hostName: string, address: string, aliveTime: int): void--><!--Device-WebviewController-static setHostIP(hostName: string, address: string, aliveTime: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostName | string | 是 | Which host name to be resolved. |
| address | string | 是 | Resolved IP address. |
| aliveTime | int | 是 | The validity seconds for resolve cache. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## setHttpDns

```TypeScript
static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void
```

Set web engine to use HttpDns server to resolve dns.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void--><!--Device-WebviewController-static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| secureDnsMode | [SecureDnsMode](arkts-na-webview-securednsmode-e.md) | 是 | using HttpDns. |
| secureDnsConfig | string | 是 | The configuration of the HttpDns server. Must be https protocol and only allow one server to be configured. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3. Parameter verification failed. |

## setNetworkAvailable

```TypeScript
setNetworkAvailable(enable: boolean): void
```

Put network state for web. Which is used to set window.navigator.onLine property in JavaScript.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setNetworkAvailable(enable: boolean): void--><!--Device-WebviewController-setNetworkAvailable(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Whether enable window.navigator.onLine. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setPathAllowingUniversalAccess

```TypeScript
setPathAllowingUniversalAccess(pathList: Array<string>): void
```

Sets a path list. When a file protocol accesses resources in the path list, it can access the local files across domains. In addition, when a path list is set, the file protocol can access only the resources in the path list. The behavior of fileAccess will be overwritten by that of this API. The paths in the list must be any of the following(sub path and module name must be provided): 1. The path of subdirectory of the application file directory, like "/data/storage/el2/base/files/example" or "/data/storage/el2/base/haps/entry/files/example". The application file directory is obtained using Context.filesDir in the Ability Kit. 2. The path of application resource directory or its subdirectory, like "/data/storage/el1/bundle/entry/resource/resfile" or "/data/storage/el1/bundle/entry/resource/resfile/example". The application resource directory is obtained from Context.resourceDir in the Ability Kit. If a path in the list is not of the preceding paths, error code 401 is reported and the path list fails to be set. When the path list is set to empty, the accessible files for the file protocol are subject to the behavior of the fileAccess.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setPathAllowingUniversalAccess(pathList: Array<string>): void--><!--Device-WebviewController-setPathAllowingUniversalAccess(pathList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathList | Array&lt;string&gt; | 是 | The path list allow universal access. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Parameter string is too long. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setPrintBackground

```TypeScript
setPrintBackground(enable: boolean): void
```

Set whether print web page background.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setPrintBackground(enable: boolean): void--><!--Device-WebviewController-setPrintBackground(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Set whether print web page background |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setRenderProcessMode

```TypeScript
static setRenderProcessMode(mode: RenderProcessMode): void
```

Set render process mode of the ArkWeb.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setRenderProcessMode(mode: RenderProcessMode): void--><!--Device-WebviewController-static setRenderProcessMode(mode: RenderProcessMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [RenderProcessMode](arkts-na-webview-renderprocessmode-e.md) | 是 | The render process mode for the ArkWeb. Call [getRenderProcessMode](#getRenderProcessMode) to get the ArkWeb rendering subprocess mode of the current device. The enumerated value *0 indicates the single render subprocess mode, and *1 indicates the multi-render subprocess mode. If an invalid number other than the enumerated value of *RenderProcessMode is passed, the multi-render subprocess mode is used by default. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

## setScrollable

```TypeScript
setScrollable(enable: boolean, type?: ScrollType): void
```

Set whether scroll is allowed; default is true.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setScrollable(enable: boolean, type?: ScrollType): void--><!--Device-WebviewController-setScrollable(enable: boolean, type?: ScrollType): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Set whether scrolling is allowed {@code true} means scrolling is allowed. {@code false} means scrolling is disabled. |
| type | [ScrollType](arkts-na-webview-scrolltype-e.md) | 否 | Enable scrolling type When the input parameter enable is false, it indicates that scrolling of the ScrollType type is prohibited. When ScrollType is not specified,it indicates that all types of webpage scrolling are prohibited. When the input parameter enable is true, regardless of whether ScrollType is specified, it indicates that all types of webpage scrolling are allowed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setScrollbarMode

```TypeScript
static setScrollbarMode(scrollbarMode: ScrollbarMode): void
```

Sets whether to switch web scrollbar mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setScrollbarMode(scrollbarMode: ScrollbarMode): void--><!--Device-WebviewController-static setScrollbarMode(scrollbarMode: ScrollbarMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollbarMode | [ScrollbarMode](arkts-na-webview-scrollbarmode-e.md) | 是 | web scrollbar mode, default OVERLAY_LAYOUT_SCROLLBAR. |

## setServiceWorkerWebSchemeHandler

```TypeScript
static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

Set web scheme handler for specific scheme. This is used for service worker.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void--><!--Device-WebviewController-static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scheme | string | 是 | String value for url scheme. |
| handler | [WebSchemeHandler](arkts-na-webview-webschemehandler-c.md) | 是 | Web scheme handler. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setSiteIsolationMode

```TypeScript
static setSiteIsolationMode(mode: SiteIsolationMode): void
```

Set the site isolation mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setSiteIsolationMode(mode: SiteIsolationMode): void--><!--Device-WebviewController-static setSiteIsolationMode(mode: SiteIsolationMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [SiteIsolationMode](arkts-na-webview-siteisolationmode-e.md) | 是 | The site isolation mode of the application, default value depends on different devices type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. Possible causes: 1. Site Isolation mode is already set by the developer. 2. Site Isolation mode cannot be strict in single-render-process mode. 3. Site Isolation mode cannot be changed while Secure Shield mode is active. @static |

## setSocketIdleTimeout

```TypeScript
static setSocketIdleTimeout(timeout: int): void
```

Set web engine socket idle timeout. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; Unit: seconds, minimum 30s, maximum 5 minutes. If not set, the default is five minutes. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setSocketIdleTimeout(timeout: int): void--><!--Device-WebviewController-static setSocketIdleTimeout(timeout: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | int | 是 | Socket idle timeout. @static |

## setSoftKeyboardBehaviorMode

```TypeScript
setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void
```

Set the WebSoftKeyboardBehaviorMode to decide whether the keyboard will be shown/hidden automatically in particular situation, for example, when web is inactive or active.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void--><!--Device-WebviewController-setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebSoftKeyboardBehaviorMode](arkts-na-webview-websoftkeyboardbehaviormode-e.md) | 是 | The WebSoftKeyboardBehaviorMode of this web. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void
```

Sets the URL trust list for the ArkWeb. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; When the URL trust list is set, only the URLs in the list can be accessed. Example of the urlTrustList: { "UrlPermissionList": [ { "scheme": "https", "host": "www.example1.com", "port": 443, "path": "pathA/pathB" }, { "scheme": "http", "host": "*.example2.com", "port": 80, "path": "test1/test2/test3" } ] } &lt;/p&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-WebviewController-setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void--><!--Device-WebviewController-setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| urlTrustList | string | 是 | The URL trust list in JSON format. An empty string means all URLs are allowed. |
| allowOpaqueOrigin | boolean | 是 | If true, loading of opaque origin URLs (e.g., javascript, data) is allowed. If false, it is not allowed. |
| supportWildcard | boolean | 是 | If true, wildcard matching is supported (e.g., *.example.com matches all subdomains). If false, wildcard matching is not supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error, possible causes: 1. Mandatory parameters are left unspecified 2. JSON string exceeds 10MB limit 3. JSON parsing failed (syntax errors, etc.) 4. UrlPermissionList field is missing 5. URL rule validation failed: - scheme must be http or https - host cannot be empty - port must be between 0-65535 - path length cannot exceed 65536 characters |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Initialization error. The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string): void
```

Set the URL trust list for the ArkWeb. When the URL trust list has been set, only the URLs in the list can be accessed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setUrlTrustList(urlTrustList: string): void--><!--Device-WebviewController-setUrlTrustList(urlTrustList: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| urlTrustList | string | 是 | the URL trust list in JSON format. An empty string means that all URLs are allowed to access. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Parameter string is too long. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setUserAgentClientHintsEnabled

```TypeScript
static setUserAgentClientHintsEnabled(enabled: boolean): void
```

Enable the User-Agent Client Hints.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-static setUserAgentClientHintsEnabled(enabled: boolean): void--><!--Device-WebviewController-static setUserAgentClientHintsEnabled(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | User-Agent Client Hints will enabled when set true. @static |

## setUserAgentForHosts

```TypeScript
static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void
```

Set the User-Agent to be used for specified hosts, with a maximum of 20,000 hosts. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; Setting the same host list multiple times for the same User-Agent will override the previous settings. That is, if you want to cancel certain hosts from using the specified User-Agent, you need to reset the host list for that User-Agent. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void--><!--Device-WebviewController-static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. |
| hosts | Array&lt;string&gt; | 是 | The hosts to which the User-Agent apply. @static |

## setUserAgentMetadata

```TypeScript
setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void
```

Sets the User-Agent metadata corresponding to the User-Agent. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; This User-Agent metadata will be used to populate the User-Agent client hints, They can provide the client's branding and version information, the underlying operating system's branding and major version, as well as details about the underlying device. The User-Agent can be set with setCustomUserAgent or setAppCustomUserAgent or setUserAgentForHosts. If the UserAgentMetadata is not found according to the overridden User-Agent and the overridden User-Agent contains the system default User-Agent, the system default value will be used. If the UserAgentMetadata is not found according to the overridden User-Agent but the overridden User-Agent does not contain the system default User-Agent, only the low-entry User-Agent client hints will be generated. &lt;/p&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void--><!--Device-WebviewController-setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. |
| metaData | [UserAgentMetadata](arkts-na-webview-useragentmetadata-c.md) | 是 | The UserAgentMetadata for the userAgent. |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean): void
```

Sets whether to enable web debugging. By default, web debugging is disabled. For details, see Debugging Frontend Pages by Using DevTools. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; Enabling web debugging allows users to check and modify the internal status of the web page, which poses security risks. Therefore, you are advised not to enable this function in the officially released version of the app. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean): void--><!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | 是 | Sets whether to enable web debugging.{@code true} enable web debugging;{@code false} disable web debugging. The default value is false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean, port: int): void
```

Enables debugging of web contents. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; The port numbers from 0 to 1024 are prohibited. Ports less than 0 or greater than 65535 are considered invalid. If an attempt is made to set these disabled or invalid ports, an exception will be thrown. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean, port: int): void--><!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean, port: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | 是 | { |
| port | int | 是 | Indicates the port of the devtools server. After the port is specified, a tcp server socket is created instead of a unix domain socket. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100023](../../apis-arkweb/errorcode-webview.md#17100023-使用了不被允许的端口号) | The port number is not within the allowed range. @static |

## setWebDestroyMode

```TypeScript
static setWebDestroyMode(mode: WebDestroyMode): void
```

Set web destroy mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static setWebDestroyMode(mode: WebDestroyMode): void--><!--Device-WebviewController-static setWebDestroyMode(mode: WebDestroyMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebDestroyMode](arkts-na-webview-webdestroymode-e.md) | 是 | web destroy mode, default NORMAL_MODE. |

## setWebSchemeHandler

```TypeScript
setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

Set web scheme handler for specific scheme. This is only used for related web component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void--><!--Device-WebviewController-setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scheme | string | 是 | String value for url scheme. |
| handler | [WebSchemeHandler](arkts-na-webview-webschemehandler-c.md) | 是 | Web scheme handler. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## slideScroll

```TypeScript
slideScroll(vx: double, vy: double): void
```

Slide by the speed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-slideScroll(vx: double, vy: double): void--><!--Device-WebviewController-slideScroll(vx: double, vy: double): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vx | double | 是 | the x speed of the speed. The unit is vp/s. |
| vy | double | 是 | the y speed of the speed. The unit is vp/s. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## startCamera

```TypeScript
startCamera(): void
```

开启当前网页摄像头捕获。使用摄像头功能前请在module.json5中添加权限: ohos.permission.CAMERA，具体权限的添加方法请参考 [在配置文件中声明权限](../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-startCamera(): void--><!--Device-WebviewController-startCamera(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## startDownload

```TypeScript
startDownload(url: string): void
```

Start a download.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-startDownload(url: string): void--><!--Device-WebviewController-startDownload(url: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The download url. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2 *1024 *1024. |

## stop

```TypeScript
stop(): void
```

Stops the current load.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-stop(): void--><!--Device-WebviewController-stop(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## stopAllMedia

```TypeScript
stopAllMedia(): void
```

控制网页所有音视频停止。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-stopAllMedia(): void--><!--Device-WebviewController-stopAllMedia(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## stopCamera

```TypeScript
stopCamera(): void
```

停止当前网页摄像头捕获。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-stopCamera(): void--><!--Device-WebviewController-stopCamera(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## stopMicrophone

```TypeScript
stopMicrophone(): void
```

停止当前网页麦克风捕获。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-stopMicrophone(): void--><!--Device-WebviewController-stopMicrophone(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## storeWebArchive

```TypeScript
storeWebArchive(baseName: string, autoName: boolean): Promise<string>
```

Stores the current page as a web archive.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean): Promise<string>--><!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| baseName | string | 是 | Where the generated offline webpage is stored, This value cannot be null. |
| autoName | boolean | 是 | Decide whether to automatically generate the file name. If false, it is stored by the file name of baseName. If true, the file name is automatically generated based on the current URL and stored in the file directory of baseName. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | a promise resolved after the web archive has been stored. The parameter will either be the filename under which the file was stored, or empty if storing the file failed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../../apis-arkweb/errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## storeWebArchive

```TypeScript
storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void
```

Stores the current page as a web archive.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void--><!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| baseName | string | 是 | Where the generated offline webpage is stored, This value cannot be null. |
| autoName | boolean | 是 | Decide whether to automatically generate the file name. If false, it is stored by the file name of baseName. If true, the file name is automatically generated based on the current URL and stored in the file directory of baseName. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | called after the web archive has been stored. The parameter will either be the filename under which the file was stored, or empty if storing the file failed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../../apis-arkweb/errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## terminateRenderProcess

```TypeScript
terminateRenderProcess(): boolean
```

Destroy the rendering process. Calling this interface will actively destroy the associated rendering process. If the rendering process has not been started or destroyed, it has no effect. In addition, destroying the rendering process will also affect all other instances associated with the rendering process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-terminateRenderProcess(): boolean--><!--Device-WebviewController-terminateRenderProcess(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true if it was possible to terminate the render process, otherwise false. Calling this on a not yet started, or an already terminated render will have no effect. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## trimMemoryByPressureLevel

```TypeScript
static trimMemoryByPressureLevel(level: PressureLevel): void
```

Trim memory by different memory pressure level.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static trimMemoryByPressureLevel(level: PressureLevel): void--><!--Device-WebviewController-static trimMemoryByPressureLevel(level: PressureLevel): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [PressureLevel](arkts-na-webview-pressurelevel-e.md) | 是 | The memory pressure level for the ArkWeb. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Parameter string is too long. 3.Parameter verification failed. |

## waitForAttached

```TypeScript
waitForAttached(timeout: int): Promise<ControllerAttachState>
```

Wait for the controller to attach a web component until timeout.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-waitForAttached(timeout: int): Promise<ControllerAttachState>--><!--Device-WebviewController-waitForAttached(timeout: int): Promise<ControllerAttachState>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | int | 是 | the wait timeout, if timeout reach, promise will return, the unit is millisecond. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ControllerAttachState](arkts-na-webview-controllerattachstate-e.md)&gt; | Promise used to return the state of attach. |

## warmupServiceWorker

```TypeScript
static warmupServiceWorker(url: string): void
```

Warmup the registered service worker associated the url.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-static warmupServiceWorker(url: string): void--><!--Device-WebviewController-static warmupServiceWorker(url: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The url. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2048. |

## webPageSnapshot

```TypeScript
webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void
```

Web page snapshot. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; Only screenshots of assets on the rendering process are supported: still images and text. If there is a video on the page, the placeholder image of the video will be displayed when you take a screenshot, and blank if there is no placeholder. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void--><!--Device-WebviewController-webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [SnapshotInfo](arkts-na-webview-snapshotinfo-i.md) | 是 | The snapshot info. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SnapshotResult](arkts-na-webview-snapshotresult-i.md)&gt; | 是 | the callback of snapshot. |

## zoom

```TypeScript
zoom(factor: double): void
```

Zooms in or out of this web page. This API is effective only when zoomAccess is true.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-zoom(factor: double): void--><!--Device-WebviewController-zoom(factor: double): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factor | double | 是 | Relative zoom ratio. The value must be greater than 0. The value 1 indicates that the page is not zoomed. A value smaller than 1 indicates zoom-out, and a value greater than 1 indicates zoom-in. &lt;br&gt;Value range: (0, 100]. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100004](../../apis-arkweb/errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## zoomIn

```TypeScript
zoomIn(): void
```

Zooms in on this web page by 25%.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-zoomIn(): void--><!--Device-WebviewController-zoomIn(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100004](../../apis-arkweb/errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## zoomOut

```TypeScript
zoomOut(): void
```

Zooms out of this web page by 20%.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebviewController-zoomOut(): void--><!--Device-WebviewController-zoomOut(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100004](../../apis-arkweb/errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

