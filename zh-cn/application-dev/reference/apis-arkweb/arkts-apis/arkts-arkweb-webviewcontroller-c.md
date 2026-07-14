# WebviewController

Provides methods for controlling the web controller.

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

## accessBackward

```TypeScript
accessBackward(): boolean
```

当前页面是否可后退，即当前页面是否有返回历史记录。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前页面可以后退返回true,否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## accessForward

```TypeScript
accessForward(): boolean
```

当前页面是否可前进，即当前页面是否有前进历史记录。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 可以前进返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## accessStep

```TypeScript
accessStep(step: number): boolean
```

当前页面是否可前进或者后退给定的step步。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | number | 是 | 要跳转的步数，正数代表前进，负数代表后退。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 页面是否前进或后退。<br>返回true表示可以前进或者后退，返回false表示不可以前进或后退。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## addIntelligentTrackingPreventionBypassingList

```TypeScript
static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

添加智能防跟踪功能绕过的域名列表。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | 是 | 绕过智能防跟踪功能的域名列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## avoidVisibleViewportBottom

```TypeScript
avoidVisibleViewportBottom(avoidHeight: number): void
```

设置Web网页可视视口底部避让高度。

> **说明：**
>
> - avoidHeight有效值区间为[0, Web组件高度]，超出有效值区间时取边界值。
>
> - 该接口高度设置为非0时，Web组件位置和尺寸不变，可视视口向上避让avoidHeight，表现为Web网页内容抬升avoidHeight。该接口一般用于应用自定义网页底部避让区，不建议和点击web网页可编辑区拉起键盘的
> 场景同时使用。同时使用时，键盘弹起避让模式将使用OVERLAYS_CONTENT。
>
> - 该接口高度设置为0时，Web网页内容可恢复，键盘弹起避让模式将使用
> [keyboardAvoidMode()](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#keyboardavoidmode12)
> 声明的模式。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| avoidHeight | number | 是 | 设置Web网页可视视口底部避让高度。<br>单位：vp<br>合法取值范围：0~Web组件高度<br>非法值设置行为：小于0取值为0，大于Web组件高度取值为Web组件高度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This functionality is not supported. |

## backOrForward

```TypeScript
backOrForward(step: number): void
```

按照历史栈，前进或者后退指定步长的页面，当历史栈中不存在对应步长的页面时，不会进行页面跳转。

前进或者后退页面时，直接使用已加载过的网页，无需重新加载网页。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | number | 是 | 需要前进或后退的步长。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## backward

```TypeScript
backward(): void
```

按照历史栈，后退一个页面。一般结合[accessBackward](arkts-arkweb-webviewcontroller-c.md#accessbackward-1)一起使用。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## clearBlanklessLoadingCache

```TypeScript
static clearBlanklessLoadingCache(keys?: Array<string>) : void
```

清除指定key值页面无白屏优化缓存，本接口只清除缓存。
在小程序或Web应用场景中，当页面加载时内容变化显著，可能会出现一次明显的跳变。若对此跳变有所顾虑，可使用该接口清除页面缓存。

> **说明：**
>
> - 清除之后的页面，需在第三次加载页面时才会产生优化效果。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 否 | 清除Blankless优化方案页面的key值列表，key值为[getBlanklessInfoWithKey](arkts-arkweb-webviewcontroller-c.md#getblanklessinfowithkey-1)中指定过的。<br>默认值：所有Blankless优化方案缓存的页面key列表。<br>合法取值范围：长度不超过2048，key列表长度&lt;=100。key和加载页面时输入给ArkWeb的相同。<br>非法值设置行为：传入undefined/null会抛出异常错误码401；key长度超过2048时该key不生效；长度超过100时，取前100个；当为空时，使用默认值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) |  |

## clearClientAuthenticationCache

```TypeScript
clearClientAuthenticationCache(): void
```

清除Web组件记录的客户端证书请求事件对应的用户操作行为。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## clearHistory

```TypeScript
clearHistory(): void
```

删除所有前进后退记录。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## clearHostIP

```TypeScript
static clearHostIP(hostName: string): void
```

清除指定主机域名解析后的IP地址。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostName | string | 是 | 要清除DNS记录的主机域名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## clearIntelligentTrackingPreventionBypassingList

```TypeScript
static clearIntelligentTrackingPreventionBypassingList(): void
```

删除通过addIntelligentTrackingPreventionBypassingList接口添加的所有域名。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## clearMatches

```TypeScript
clearMatches(): void
```

清除所有通过[searchAllAsync](arkts-arkweb-webviewcontroller-c.md#searchallasync-1)匹配到的高亮字符查找结果。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## clearPrefetchedResource

```TypeScript
static clearPrefetchedResource(cacheKeyList: Array<string>): void
```

根据指定的缓存key列表清除对应的预获取资源缓存。入参中的缓存key必须是[prefetchResource](arkts-arkweb-webviewcontroller-c.md#prefetchresource-1)指定预获取到的资
源缓存key。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cacheKeyList | Array&lt;string&gt; | 是 | 用于后续查询预获取资源缓存的key。仅支持字母和数字，未传入或传入空则取默认值url作为key。 |

## clearServiceWorkerWebSchemeHandler

```TypeScript
static clearServiceWorkerWebSchemeHandler(): void
```

Clear all web service worker scheme handlers.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## clearSslCache

```TypeScript
clearSslCache(): void
```

清除Web组件记录的SSL证书错误事件对应的用户操作行为。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## clearWebSchemeHandler

```TypeScript
clearWebSchemeHandler(): void
```

Clear all web scheme handlers for related web component.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## closeAllMediaPresentations

```TypeScript
closeAllMediaPresentations(): void
```

控制网页所有全屏视频关闭。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## closeCamera

```TypeScript
closeCamera(): void
```

关闭当前网页摄像头捕获。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## constructor

```TypeScript
constructor(webTag?: string)
```

A constructor used to create a WebviewController object.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

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

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | PdfConfiguration | 是 | Parameters required for creating a PDF file. |
| callback | AsyncCallback&lt;PdfData&gt; | 是 | Callback used to return the data stream of an online PDF file. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## createPdf

```TypeScript
createPdf(configuration: PdfConfiguration): Promise<PdfData>
```

Rendering current Web page into Pdf data, return the result in promise mode.

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | PdfConfiguration | 是 | Parameters required for creating a PDF file. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PdfData&gt; | Promise used to return the data stream of a web page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## createWebMessagePorts

```TypeScript
createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>
```

创建Web消息端口。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isExtentionType | boolean | 否 | 是否使用扩展增强接口。<br>默认值：false。<br>**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WebMessagePort&gt; | web消息端口列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed.<br>**适用版本：** 10+ |

## createWebPrintDocumentAdapter

```TypeScript
createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter
```

Creates a PrintDocumentAdapter instance to provide content for printing.

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobName | string | 是 | Name of the file to print. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| print.PrintDocumentAdapter | **PrintDocumentAdapter** instance created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>): void
```

对Web内核赋予自定义协议URL的跨域请求与fetch请求的权限。当Web在跨域fetch自定义协议URL时，该fetch请求可被
onInterceptRequest事件接口所拦截，从而开发者可以进一步处理该请求。建议在任何Web组件初始化之前调用该接口。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemes | Array&lt;WebCustomScheme&gt; | 是 | 自定义协议配置，最多支持同时配置10个自定义协议。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100020](../errorcode-webview.md#17100020-注册自定义协议失败) | Failed to register custom schemes.<br>**适用版本：** 12+ |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void
```

对Web内核赋予自定义协议URL的跨域请求与fetch请求的权限。当Web在跨域fetch自定义协议URL时，该fetch请求可被
onInterceptRequest事件接口所拦截，从而开发者可以进一步处理该请求。建议在任何Web组件初始化之前调用该接口。

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemes | Array&lt;WebCustomScheme&gt; | 是 | 自定义协议配置，最多支持同时配置10个自定义协议。 |
| lazyInitWebEngine | boolean | 是 | 为true时：接口内部跳过初始化WebEngine。临时存储注册的方案，当它实际被传递给WebEngine时，这些方案将被传递给WebEngine初始化。当false时：接口内部自动进行WebEngine初始化- 表示接口内部是否跳过初始化WebEngine。<br>true表示接口内部跳过初始化WebEngine，并将注册的Schemes暂存，当它真正初始化时，这些Schemes将传递给WebEngine。false表示接口内部自动进行WebEngine初始化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100020](../errorcode-webview.md#17100020-注册自定义协议失败) | Failed to register custom schemes. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. The length of the schemes array is greater than 10.2. The character length of the scheme is greater than 32.3. The character in the scheme is not within the allowed range of lowercase English letters, numbers,and the symbols ".", "+", "-". |

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string): void
```

删除一个已注册的、具有给定名称的JavaScript对象。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要删除的已注册JavaScript对象的名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100008](../errorcode-webview.md#17100008-删除不存在的javascriptproxy) | Failed to delete JavaScriptProxy because it does not exist. |

## enableAdsBlock

```TypeScript
enableAdsBlock(enable: boolean): void
```

启用广告过滤功能。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用广告过滤功能。<br>true表示启用广告过滤功能，false表示取消广告过滤功能。<br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Parameter string is too long. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## enableAdvancedSecurityMode

```TypeScript
static enableAdvancedSecurityMode(securityParams: SecurityParams): void
```

启用应用程序禁用PDFViewer等一些功能，以提高Web应用程序的安全级别

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| securityParams | SecurityParams | 是 | 参数表示将禁用支持的选项或项目。 |

## enableBackForwardCache

```TypeScript
static enableBackForwardCache(features: BackForwardCacheSupportedFeatures): void
```

开启Web组件前进后退缓存功能，通过参数指定是否允许使用特定的页面进入前进后退缓存。
默认设置为禁用。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| features | BackForwardCacheSupportedFeatures | 是 | 允许使用特定的页面进入前进后退缓存中。 |

## enableIntelligentTrackingPrevention

```TypeScript
enableIntelligentTrackingPrevention(enable: boolean): void
```

启用智能防跟踪功能。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用智能防跟踪功能。<br>true表示启用智能防跟踪功能，false表示不启用智能防跟踪功能。<br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## enablePrivateNetworkAccess

```TypeScript
static enablePrivateNetworkAccess(enable: boolean): void
```

After enable PrivateNetworkAccess feature, ArkWeb will send a CORS preflight request before issuing any
sub-resource private network requests to request explicit permission from the target server. After disable
PrivateNetworkAccess, ArkWeb will no longer check whether the private network request is legitimate.
By default, PrivateNetworkAccess feature is enabled.

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | {@code true} enable the private network acccess check; {@code false} otherwise. |

## enableSafeBrowsing

```TypeScript
enableSafeBrowsing(enable: boolean): void
```

启用检查网站安全风险的功能，非法和欺诈网站是强制启用的，不能通过此功能禁用。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | {@code true} 启用检查网站安全风险的功能， {@code false} 表示不启用检查网站安全风险的功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## enableWholeWebPageDrawing

```TypeScript
static enableWholeWebPageDrawing(): void
```

设置开启网页全量绘制能力。仅在web初始化时设置。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## forward

```TypeScript
forward(): void
```

按照历史栈，前进一个页面。一般结合accessForward一起使用。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getActiveWebEngineVersion

```TypeScript
static getActiveWebEngineVersion(): ArkWebEngineVersion
```

获取当前ArkWeb内核版本。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkWebEngineVersion | 返回由[ArkWebEngineVersion](arkts-arkweb-arkwebengineversion-e.md)所定义的当前使用的ArkWeb内核版本。 |

## getAttachState

```TypeScript
getAttachState(): ControllerAttachState
```

获取webview controller是否绑定一个web组件

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ControllerAttachState | 绑定状态 |

## getBackForwardEntries

```TypeScript
getBackForwardEntries(): BackForwardList
```

获取当前Webview的历史信息列表。

> **说明：**
>
> onLoadIntercept在加载开始的时候触发，该时刻还未生成历史节点，所以在onLoadIntercept中调用getBackForwardEntries
> 拿到的历史栈不包括当前正在加载中的跳转。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BackForwardList | 当前Webview的历史信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getBlanklessInfoWithKey

```TypeScript
getBlanklessInfoWithKey(key: string) : BlanklessInfo
```

获取页面首屏加载预测信息（详细说明见[BlanklessInfo](arkts-arkweb-blanklessinfo-i.md)），并开始本次加载过渡帧生成，应用根据此信息确定是否需要启用无白屏
加载。必须与[setBlanklessLoadingWithKey](arkts-arkweb-webviewcontroller-c.md#setblanklessloadingwithkey-1)接口配套使用，并且必须在触发加载页面的
接口之前或在`onLoadIntercept`中调用。需在`WebViewController`与Web组件绑定后才能使用。

> **说明：**
>
> - 持久缓存容量：默认大小为30MB（约30页），可以通过接口
> [setBlanklessLoadingCacheCapacity](arkts-arkweb-webviewcontroller-c.md#setblanklessloadingcachecapacity-1)设置缓存容量，具体见该
> 接口说明。超过容量时根据LRU（Least Recently Used，淘汰不常用缓存的策略）机制更新缓存。自动清理超过7天的持久缓存数据，缓存清除后第三次加载页面开始有优化效果。
>
> - 如果发现快照相似度（即[BlanklessInfo](arkts-arkweb-blanklessinfo-i.md)中的similarity）极低，请确认key值是否传递正确。
>
> - 调用本接口后，将启用页面加载快照检测及生成过渡帧计算，会产生一定的资源开销。
>
> - 启用无白屏加载的页面会带来一定的资源开销，开销的大小与Web组件的分辨率相关。假设分辨率的宽度和高度分别为：w, h。页面在打开阶段会增加峰值内存，增加约12 * w * h B，页面打开后内存回收，不影响稳态内存。增
> 加固态应用缓存的大小，每个页面增加的缓存约w * h / 10 B，缓存位于应用缓存的位置。
>
> - 请在module.json5中添加权限: ohos.permission.INTERNET和ohos.permission.GET_NETWORK_INFO，具体权限的添加方法请参考
> [在配置文件中声明权限](../../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 唯一标识本页面的key值。<br>合法取值范围：非空，长度不超过2048个字符。<br>设置非法值时不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BlanklessInfo | 页面首屏加载预测信息，主要包括首屏相似度预测值，首屏加载耗时预测值，应用需根据此信息来决策是否启用无白屏加载插帧。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) |  |

## getCertificate

```TypeScript
getCertificate(): Promise<Array<cert.X509Cert>>
```

获取当前网站的证书信息。使用Web组件加载https网站，会进行SSL证书校验，该接口会通过Promise异步返回当前网站的X509格式证书。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;cert.X509Cert&gt;&gt; | the promise of the current website's certificate. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a web component. |

## getCertificate

```TypeScript
getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void
```

获取当前网站的证书信息。使用Web组件加载https网站，会进行SSL证书校验，该接口会通过AsyncCallback异步返回当前网站的X509格式证书。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;cert.X509Cert&gt;&gt; | 是 | 通过AsyncCallback异步返回当前网站的X509格式证书。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a web component. |

## getCustomUserAgent

```TypeScript
getCustomUserAgent(): string
```

获取自定义用户代理。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 用户自定义代理信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getDefaultUserAgent

```TypeScript
static getDefaultUserAgent(): string
```

获取默认用户代理。

**起始版本：** 14

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ArkWeb默认User-Agent字符串。 |

## getErrorPageEnabled

```TypeScript
getErrorPageEnabled(): boolean
```

Get whether default error page feature is enabled.

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - True if enable the default error page feature; else false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getFavicon

```TypeScript
getFavicon(): image.PixelMap
```

获取页面的favicon图标。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | Return the favicon bitmap of the current page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getHitTest

```TypeScript
getHitTest(): WebHitTestType
```

获取当前被点击区域的元素类型。

> **说明：**
>
> 从API version11开始支持，从API version 18开始废弃。建议使用[getLastHitTest](arkts-arkweb-webviewcontroller-c.md#getlasthittest-1)替代。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** [getLastHitTest](arkts-arkweb-webviewcontroller-c.md#getlasthittest-1)

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebHitTestType | 被点击区域的元素类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getHitTestValue

```TypeScript
getHitTestValue(): HitTestValue
```

获取当前被点击区域的元素信息。

> **说明：**
>
> 从API version11开始支持，从API version 18开始废弃。建议使用[getLastHitTest](arkts-arkweb-webviewcontroller-c.md#getlasthittest-1)替代。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** [getLastHitTest](arkts-arkweb-webviewcontroller-c.md#getlasthittest-1)

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HitTestValue | 点击区域的元素信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getLastHitTest

```TypeScript
getLastHitTest(): HitTestValue
```

获取上一次被点击区域的元素信息。

**起始版本：** 18

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HitTestValue | 点击区域的元素信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getLastJavascriptProxyCallingFrameUrl

```TypeScript
getLastJavascriptProxyCallingFrameUrl(): string
```

获取最后一次调用注入的对象的frame的URL。该方法应在 UI 线程上调用。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 最后一次调用注入的对象的frame的URL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getLastPostMessageURL

```TypeScript
getLastPostMessageURL(): string
```

获取上一次发送post message给应用的HTML的frame的url

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The URL of frame that last sent a postMessage. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getMediaPlaybackState

```TypeScript
getMediaPlaybackState(): MediaPlaybackState
```

查询当前网页音视频播放状态。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MediaPlaybackState | 当前网页的播放状态，具体值为NONE、PLAYING、PAUSED、STOPPED。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getOriginalUrl

```TypeScript
getOriginalUrl(): string
```

获取当前页面的原始URL地址。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前页面的原始URL地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getPageHeight

```TypeScript
getPageHeight(): number
```

获取当前网页的页面高度。具体使用详情请参考[获取网页内容高度](../../../../web/web-getpage-height.md)。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前网页的页面高度。单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getPageOffset

```TypeScript
getPageOffset(): ScrollOffset
```

获取网页当前的滚动偏移量（不包含过滚动偏移量）。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ScrollOffset | 网页当前的滚动偏移量（不包含过滚动偏移量）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## getPrintBackground

```TypeScript
getPrintBackground(): boolean
```

Get whether print web page background.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the web page background is printed.<br>The value **true** indicates that the web page background is printed, and **false** indicates the opposite. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getProgress

```TypeScript
getProgress() : number
```

Gets the loading progress for the current page.

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前页面加载进度，取值范围[0, 100] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## getRenderProcessMode

```TypeScript
static getRenderProcessMode(): RenderProcessMode
```

Get render process mode of the ArkWeb.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RenderProcessMode | mode - The render process mode of the ArkWeb.Call {@link getRenderProcessMode} to get the ArkWeb rendering subprocess mode of the current device,with an enumeration value of 0 as a single subprocess mode and an enumeration value of 1 as a multi-subprocess mode.If the obtained value is not within the range of the RenderProcessMode enumeration value,it defaults to the multi-rendering subprocess mode. |

## getScrollOffset

```TypeScript
getScrollOffset(): ScrollOffset
```

获取网页当前的滚动偏移量（包含过滚动偏移量）。

**起始版本：** 13

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ScrollOffset | 网页当前的滚动偏移量（包含过滚动偏移量）。 |

## getScrollable

```TypeScript
getScrollable(): boolean
```

获取当前网页是否允许滚动。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前网页是否允许滚动。<br>true为允许滚动，false为禁止滚动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getSecurityLevel

```TypeScript
getSecurityLevel(): SecurityLevel
```

获取当前网页的安全级别。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SecurityLevel | 当前网页的安全级别，具体值为NONE、SECURE、WARNING、DANGEROUS。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getSiteIsolationMode

```TypeScript
static getSiteIsolationMode(): SiteIsolationMode
```

Get the site isolation mode.

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SiteIsolationMode | The site isolation mode of the application.@static |

## getSurfaceId

```TypeScript
getSurfaceId(): string
```

获取ArkWeb对应Surface的ID，此ID可用于网页截图。

> **说明：**
>
> 仅Web组件渲染模式是ASYNC_RENDER时有效。getSurfaceId需要在Web组件初始化之后才能获取到值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ArkWeb持有Surface的ID。 |

## getTitle

```TypeScript
getTitle(): string
```

获取当前网页的标题。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前网页的标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getUrl

```TypeScript
getUrl(): string
```

获取当前页面的URL地址。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前页面的URL地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getUserAgent

```TypeScript
getUserAgent(): string
```

获取当前默认用户代理。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 默认用户代理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## getUserAgentClientHintsEnabled

```TypeScript
static getUserAgentClientHintsEnabled(): boolean
```

Get if the UserAgent Client Hints enabled.

**起始版本：** 24

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If UserAgent Client Hints was enabled. |

## getUserAgentMetadata

```TypeScript
getUserAgentMetadata(userAgent: string): UserAgentMetadata
```

Get the User-Agent metadata corresponding to the User-Agent.

**起始版本：** 24

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UserAgentMetadata | The UserAgentMetadata for the userAgent. |

## getWebId

```TypeScript
getWebId(): number
```

Gets the index value of the current Web component for the management of multiple Web components.

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the index value of the current Web component. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(): Promise<boolean>
```

通过Promise方式异步查找当前页面是否存在图像。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise实例，返回查找页面是否存在图像。<br> true表示页面存在图像；false表示页面不存在图像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(callback: AsyncCallback<boolean>): void
```

通过Callback方式异步查找当前页面是否存在图像。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 返回查找页面是否存在图像。<br> true表示页面存在图像；false表示页面不存在图像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## initializeWebEngine

```TypeScript
static initializeWebEngine(): void
```

Initialize the web engine before loading the Web components.
This is a global static API that must be called on the UI thread, and it will have no effect if any
Web components are loaded.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## injectOfflineResources

```TypeScript
injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void
```

将本地离线资源注入到内存缓存中，以提升页面首次启动速度。
内存缓存中的资源由内核自动管理，当注入的资源过多导致内存压力过大，内核自动释放未使用的资源，应避免注入大量资源到内存缓存中。
正常情况下，资源的有效期由提供的Cache-Control或Expires响应头控制其有效期，默认的有效期为86400秒，即1天。
资源的MIMEType通过提供的Content-Type响应头配置，Content-Type需符合标准，否则无法正常使用，MODULE_JS必须提供有效的MIMEType，其他类型可不提供。
以此方式注入的资源，仅支持通过HTML中的标签加载。如果业务网页中的script标签使用了crossorigin属性，则必须在接口的responseHeaders参数中设置Cross-Origin响应头的值为anonymous
或use-credentials。
当调用`webview.WebviewController.SetRenderProcessMode(webview.RenderProcessMode.MULTIPLE)`接口后，应用会启动多渲染进程模式，此接口在此场景下不
会生效。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceMaps | Array&lt;OfflineResourceMap&gt; | 是 | 本地离线资源配置对象，单次调用最大支持注入30个资源，单个资源最大支持10Mb。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 12 - 21 |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 12 - 21 |

## isActiveWebEngineEvergreen

```TypeScript
static isActiveWebEngineEvergreen(): boolean
```

判断当前系统是否正在使用常青内核，即系统的最新内核。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否正在使用常青内核。正在使用返回true，否则返回false。 |

## isAdsBlockEnabled

```TypeScript
isAdsBlockEnabled(): boolean
```

查询广告过滤功能是否开启。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true代表广告过滤功能已开启，返回false代表广告过滤功能关闭。<br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## isAdsBlockEnabledForCurPage

```TypeScript
isAdsBlockEnabledForCurPage(): boolean
```

查询当前网页是否开启广告过滤功能。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true代表此网页已开启广告过滤，返回false代表当前网页已关闭广告过滤。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## isAutoPreconnectEnabled

```TypeScript
static isAutoPreconnectEnabled(): boolean
```

?Retrieve whether the automatic pre-connection feature is enabled?.

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return true if enabled, false if disabled. |

## isIncognitoMode

```TypeScript
isIncognitoMode(): boolean
```

查询当前是否是隐私模式的Webview。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否是隐私模式的Webview。<br>true表示是隐私模式，false表示不是隐私模式。<br>默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## isIntelligentTrackingPreventionEnabled

```TypeScript
isIntelligentTrackingPreventionEnabled(): boolean
```

获取Web组件是否启用了智能防跟踪功能。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Web组件是否启用了智能防跟踪功能。<br>true表示启用了智能防跟踪功能，false表示未启用智能防跟踪功能。<br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## isPrivateNetworkAccessEnabled

```TypeScript
static isPrivateNetworkAccessEnabled(): boolean
```

Get whether PrivateNetworkAccess is enabled.

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if enable the ability to check private network access else false. |

## isSafeBrowsingEnabled

```TypeScript
isSafeBrowsingEnabled(): boolean
```

获取当前网页是否启用了检查网站安全风险。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示启用了检查网站安全风险的功能，false表示未启用检查网站安全风险的功能。 |

## loadData

```TypeScript
loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void
```

加载指定的数据。

baseUrl与historyUrl同时为空的情况下：

encoding如果为非base64（包括空值），则假定数据对安全URL字符范围内的八位字节使用ASCII编码，对该范围外的八位字节使用URL的标准%xx十六进制编码。
data数据必须使用base64编码或将内容中的任何#字符编码为%23。否则#将被视为内容的结尾而剩余的文本将被用作文档片段标识符。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 按照"base64"或者"URL"编码后的一段字符串。 |
| mimeType | string | 是 | 媒体类型（MIME）。 |
| encoding | string | 是 | 编码类型，具体为"base64"或者"URL"编码。 |
| baseUrl | string | 否 | 按照"base64"或者"URL"编码后的一段字符串。 |
| historyUrl | string | 否 | 用作历史记录所使用的URL。非空时，历史记录以此URL进行管理。当baseUrl为空时，此属性无效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 9 - 10 |

## loadUrl

```TypeScript
loadUrl(url: string | Resource, headers?: Array<WebHeader>): void
```

加载指定的URL。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string \| Resource | 是 | 需要加载的URL。 |
| headers | Array&lt;WebHeader&gt; | 否 | URL的附加HTTP请求头。<br>默认值： []。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## off('controllerAttachStateChange')

```TypeScript
off(type: 'controllerAttachStateChange', callback?: Callback<ControllerAttachState>): void
```

取消注册controller绑定状态变化的回调

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controllerAttachStateChange' | 是 | the event of controller attach state change. |
| callback | Callback&lt;ControllerAttachState&gt; | 否 | Callback used to return the controller attach state. |

## on('controllerAttachStateChange')

```TypeScript
on(type: 'controllerAttachStateChange', callback: Callback<ControllerAttachState>): void
```

注册controller绑定状态变化的回调

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controllerAttachStateChange' | 是 | the event of controller attach state change. |
| callback | Callback&lt;ControllerAttachState&gt; | 是 | Callback used to return the controller attach state. |

## onActive

```TypeScript
onActive(): void
```

Let the Web active.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## onCreateNativeMediaPlayer

```TypeScript
onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void
```

注册回调函数，开启
[应用接管网页媒体播放功能](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#enablenativemediaplayer12)
后，当网页中有播放媒体时，触发注册的回调函数。

如果应用接管网页媒体播放功能未开启，则注册的回调函数不会被触发。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | CreateNativeMediaPlayerCallback | 是 | 接管网页媒体播放的回调函数。 |

## onInactive

```TypeScript
onInactive(): void
```

Let the Web inactive.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## pageDown

```TypeScript
pageDown(bottom: boolean): void
```

将Webview的内容向下滚动半个视框大小或者跳转到页面最底部，通过bottom入参控制。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bottom | boolean | 是 | 是否跳转到页面最底部。<br>false时表示将页面内容向下滚动半个视框大小，true表示跳转到页面最底部。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## pageUp

```TypeScript
pageUp(top: boolean): void
```

将Webview的内容向上滚动半个视框大小或者跳转到页面最顶部，通过top入参控制。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| top | boolean | 是 | 是否跳转到页面最顶部。<br>false表示将页面内容向上滚动半个视框大小，true表示跳转到页面最顶部。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## pauseAllMedia

```TypeScript
pauseAllMedia(): void
```

控制网页所有音视频暂停。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## pauseAllTimers

```TypeScript
static pauseAllTimers(): void
```

暂停所有WebView的定时器。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## pauseMicrophone

```TypeScript
pauseMicrophone(): void
```

暂停当前网页麦克风捕获。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## postMessage

```TypeScript
postMessage(name: string, ports: Array<WebMessagePort>, uri: string): void
```

发送Web消息端口到HTML。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要发送的消息名称。 |
| ports | Array&lt;WebMessagePort&gt; | 是 | 要发送的消息端口。 |
| uri | string | 是 | 接收该消息的URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## postUrl

```TypeScript
postUrl(url: string, postData: ArrayBuffer): void
```

使用"POST"方法加载带有postData的URL。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 需要加载的URL。 |
| postData | ArrayBuffer | 是 | 使用"POST"方法传递数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid. |

## precompileJavaScript

```TypeScript
precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<number>
```

预编译JavaScript生成字节码缓存或根据提供的参数更新已有的字节码缓存。
接口通过提供的文件信息、E-Tag响应头和Last-Modified响应头判断是否需要更新已有的字节码缓存。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 本地JavaScript文件对应的网络地址，即业务网页请求该文件的服务器版本时使用的网络地址。网络地址仅支持http或https协议，长度不超过2048。如果该网络地址对应的缓存失效，则业务网页将通过网络请求对应的资源。 |
| script | string \| Uint8Array | 是 | 本地JavaScript的文本内容。内容不能为空。 |
| cacheOptions | CacheOptions | 是 | 用于控制字节码缓存更新。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 生成字节码缓存的错误码，0表示无错误，-1表示内部错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter.Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void
```

在预测到将要加载的页面之前调用，可提前下载页面所需的资源（包括：主资源和子资源），但不会执行网页JavaScript代码或呈现网页，以加快页面加载速度。

> **说明：**
>
> - 下载的页面资源会缓存五分钟左右，超过这段时间Web组件会自动释放。
>
> - prefetchPage对302重定向页面同样正常预取。
>
> - 先执行prefetchPage再加载页面时，已预取的资源将直接从缓存中加载。
>
> - 连续prefetchPage多个URL只有第一个生效。
>
> - prefetchPage有时间限制，500ms内不能多次预取。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 预加载的URL。 |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | URL的附加HTTP请求头。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 10 - 21 |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 10 - 21 |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void
```

Prefetch the resources required by the page, but will not execute js or render the page.

> **说明：**
>
> - 下载的页面资源会缓存五分钟左右，超过这段时间Web组件会自动释放。
> - prefetchPage对302重定向页面同样正常预取。
?> - prefetchPage默认不缓存Cache-Control: no-store的资源，并且只允许在500ms内进行一次预取。
> - 可以通过prefetchOptions自定义预取行为，包括忽略Cache-Control: no-store和调整节流间隔。

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 预加载的URL。 |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | URL的附加HTTP请求头。<br>默认值： [] |
| prefetchOptions | PrefetchOptions | 否 | 预取行为可以通过 prefetchOptions 进行自定义，包括忽略 Cache-Control: no-store 以及调整节流间隔。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 21+ |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 21+ |

## prefetchResource

```TypeScript
static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,
                            cacheValidTime?: number): void
```

根据指定的请求信息和附加的HTTP请求头去预获取资源请求，存入内存缓存，并指定其缓存key和有效期，以加快加载速度。目前仅支持Content-Type为application/x-www-form-urlencoded的
POST请求。最多可以预获取6个POST请求。如果要预获取第7个，请通过
[clearPrefetchedResource](arkts-arkweb-webviewcontroller-c.md#clearprefetchedresource-1)清除不需要的POST请求缓存，否则会自动清除最早预获取的
POST缓存。如果要使用预获取的资源缓存，开发者需要在正式发起的POST请求的请求头中增加键值“ArkWebPostCacheKey”，其内容为对应缓存的cacheKey。

内存缓存中的资源由内核自动管理，当注入的资源过多导致内存压力过大，内核自动释放未使用的资源，应避免注入大量资源到内存缓存中。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | RequestInfo | 是 | 预获取请求的信息。 |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | 预获取请求的附加HTTP请求头。 <br>传入undefined或null会抛出异常错误码401。 |
| cacheKey | string | 否 | 用于后续查询预获取资源缓存的key。仅支持字母和数字，未传入或传入空则取默认值url作为key。<br>传入undefined或null会抛出异常错误码401。 |
| cacheValidTime | number | 否 | 预获取资源缓存的有效期。<br>取值范围：(0, 2147483647]。<br>默认值：300s。 <br>单位：s。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are leftunspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 12 - 21 |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 12 - 21 |

## prepareForPageLoad

```TypeScript
static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void
```

预连接URL，在加载URL之前调用此API，对URL只进行DNS解析，socket建链操作，并不获取主资源子资源。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 预连接的URL。 |
| preconnectable | boolean | 是 | 是否进行预连接。如果preconnectable为true，则对URL进行DNS解析，socket建链预连接；如果preconnectable为false，则不做任何预连接操作。 |
| numSockets | number | 是 | 要预连接的socket数。socket数目连接需要大于0，最多允许6个连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 10 - 21 |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 10 - 21 |
| [17100013](../errorcode-webview.md#17100013-预连接时输入socket数目无效) | The number of preconnect sockets is invalid. |

## refresh

```TypeScript
refresh(): void
```

调用此接口通知Web组件刷新网页。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## refresh

```TypeScript
refresh(ignoreCache: boolean): void
```

通知Web组件刷新网页，可以选择是否忽略缓存刷新。

**起始版本：** 24

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ignoreCache | boolean | 是 | Web组件刷新网页，选择是否忽略缓存刷新。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,
        asyncMethodList?: Array<string>, permission?: string): void
```

Registers the JavaScript object and method list.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jsObject | object | 是 | Application side JavaScript objects participating in registration.<br>**起始版本：** 9 |
| name | string | 是 | The name of the registered object, which is consistent with theobject name called in the window. |
| methodList | Array&lt;string&gt; | 是 | The method of the application side JavaScript object participatingin the registration. |
| asyncMethodList | Array&lt;string&gt; | 否 | The async method of the application side JavaScript objectparticipating in the registration.<br>**起始版本：** 12 |
| permission | string | 否 | permission configuration defining web page URLs that can access JavaScriptProxymethods.The configuration can be defined at two levels, object level and method level.<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## removeAllCache

```TypeScript
static removeAllCache(clearRom: boolean): void
```

清除应用中的资源缓存文件，此方法将会清除同一应用中所有Webview的缓存文件。

**起始版本：** 18

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearRom | boolean | 是 | 设置为true时同时清除ROM和RAM中的缓存，设置为false时只清除RAM中的缓存。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## removeCache

```TypeScript
removeCache(clearRom: boolean): void
```

清除应用中的资源缓存文件，此方法将会清除同一应用中所有Webview的缓存文件。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearRom | boolean | 是 | 设置为true时同时清除ROM和RAM中的缓存，设置为false时只清除RAM中的缓存。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## removeIntelligentTrackingPreventionBypassingList

```TypeScript
static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

删除通过addIntelligentTrackingPreventionBypassingList接口添加的部分域名列表。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | 是 | 绕过智能防跟踪功能的域名列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## requestFocus

```TypeScript
requestFocus(): void
```

使当前Web页面获取焦点。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## restoreWebState

```TypeScript
restoreWebState(state: Uint8Array) : void
```

当前Webview从序列化数据中恢复页面状态历史记录。
如果state过大，可能会导致异常。建议state大于512k时，放弃恢复页面状态历史记录。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | Uint8Array | 是 | 页面状态历史记录序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## resumeAllMedia

```TypeScript
resumeAllMedia(): void
```

控制网页被pauseAllMedia接口暂停的音视频继续播放。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## resumeAllTimers

```TypeScript
static resumeAllTimers(): void
```

恢复从pauseAllTimers()接口中被暂停的所有的定时器。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## resumeMicrophone

```TypeScript
resumeMicrophone(): void
```

恢复当前网页麦克风捕获。使用麦克风功能前请在module.json5中添加权限: ohos.permission.MICROPHONE，具体权限的添加方法请参考
[在配置文件中声明权限](../../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## runJavaScript

```TypeScript
runJavaScript(script: string): Promise<string>
```

在当前显示页面的上下文中异步执行JavaScript脚本，脚本执行的结果将通过Promise方式返回。此方法必须在用户界面（UI）线程上使用 ，并且回调也将在用户界面（UI）线程上调用。

> **说明：**
>
> - 跨导航操作（如loadUrl）时，JavaScript状态 将不再保留，例如，调用loadUrl前定义的全局变量和函数在加载的页面中将不存在。
>
> - 建议应用程序使用registerJavaScriptProxy来确保JavaScript状态能够在页面导航间保持。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string | 是 | JavaScript脚本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise实例，返回脚本执行的结果，执行失败返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScript

```TypeScript
runJavaScript(script: string, callback: AsyncCallback<string>): void
```

在当前显示页面的上下文中异步执行JavaScript脚本，脚本执行的结果将通过异步回调方式返回。此方法必须在用户界面（UI）线程上使用 ，并且回调也将在用户界面（UI）线程上调用。

> **说明：**
>
> - 跨导航操作（如loadUrl）时，JavaScript状态将不再保留。例如，调用loadUrl前定义的全局变量和函数在加载的页面中将不存在。
>
> - 建议应用程序使用registerJavaScriptProxy来确保JavaScript状态能够在页面导航间保持。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string | 是 | JavaScript脚本。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调执行JavaScript脚本结果。JavaScript脚本若执行失败或无返回值时，返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>
```

异步执行JavaScript脚本，并通过Promise方式返回脚本执行的结果。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string \| ArrayBuffer | 是 | JavaScript脚本。<br>**起始版本：** 10 - 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;JsMessageExt&gt; | Promise实例，返回脚本执行的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void
```

异步执行JavaScript脚本，并通过回调方式返回脚本执行的结果。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string \| ArrayBuffer | 是 | JavaScript脚本。<br>**起始版本：** 10 - 11 |
| callback | AsyncCallback&lt;JsMessageExt&gt; | 是 | 回调执行JavaScript脚本结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## scrollBy

```TypeScript
scrollBy(deltaX: number, deltaY: number, duration?: number): void
```

在指定时间内将页面滚动指定的偏移量。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deltaX | number | 是 | 水平偏移量，其中水平向右为正方向。<br>单位：vp。 |
| deltaY | number | 是 | 垂直偏移量，其中垂直向下为正方向。<br>单位：vp。 |
| duration | number | 否 | 滚动动画时间。<br>单位：ms。<br>不传入为无动画，当传入数值为负数或传入0时，按照不传入处理。<br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 14 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## scrollByWithResult

```TypeScript
scrollByWithResult(deltaX: number, deltaY: number): boolean
```

将页面滚动指定的偏移量，返回值表示此次滚动是否执行成功。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deltaX | number | 是 | 水平偏移量，其中水平向右为正方向。 <br>单位：vp。 |
| deltaY | number | 是 | 垂直偏移量，其中垂直向下为正方向。 <br>单位：vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示当前网页可以滑动，false表示当前网页不可以滑动。<br>默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## scrollTo

```TypeScript
scrollTo(x: number, y: number, duration?: number): void
```

Scrolls the page to the specified absolute position within a specified period.

在指定时间内，将页面滚动到指定的绝对位置。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 绝对位置的水平坐标，当传入数值为负数时，按照传入0处理。<br>单位：vp。 |
| y | number | 是 | 绝对位置的垂直坐标，当传入数值为负数时，按照传入0处理。<br>单位：vp。 |
| duration | number | 否 | 滚动动画时间。<br>单位：ms。<br>不传入为无动画，当传入数值为负数或传入0时，按照不传入处理。<br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 14 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## searchAllAsync

```TypeScript
searchAllAsync(searchString: string): void
```

异步查找网页中所有匹配关键字'searchString'的内容并高亮，结果通过
[onSearchResultReceive](@ohos.web.WebAttribute#onsearchresultreceive)异步返回。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchString | string | 是 | 查找的关键字。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## searchNext

```TypeScript
searchNext(forward: boolean): void
```

滚动到下一个匹配的查找结果并高亮。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forward | boolean | 是 | 从前向后或者逆向查找方式。<br>true表示从前向后查找，false表示从后向前查找。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## serializeWebState

```TypeScript
serializeWebState() : Uint8Array
```

Serialize the access stack of the web, that is, the history of access.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | Web access stack after serialization. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setActiveWebEngineVersion

```TypeScript
static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void
```

设置ArkWeb内核版本。若系统不支持指定版本，则设置无效。该接口为全局静态API，须在调用initializeWebEngine前执行，若已加载任何Web组件，则该设置无效。

> **说明：**
>
> - setActiveWebEngineVersion不支持在异步线程中调用。
>
> - setActiveWebEngineVersion全局生效，在整个APP生命周期中调用一次即可，不需要重复调用。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| engineVersion | ArkWebEngineVersion | 是 | ArkWeb内核版本。 |

## setAppCustomUserAgent

```TypeScript
static setAppCustomUserAgent(userAgent: string) : void
```

Set the default User-Agent for the application.

<p><strong>API Note</strong>:<br>
Unlike setCustomUserAgent, which only takes effect in the current web context, the
priority for pages loaded in the web is as follows:
1. The User-Agent set by setCustomUserAgent is used first.
2. If not set, it will check whether a specific User-Agent has been
assigned to the current page via setUserAgentForHosts.
3. If no specific User-Agent is assigned, the application will fall back
to using the User-Agent set by setAppCustomUserAgent.
4. If the app's default User-Agent is also not specified, the web's default
User-Agent will be used as the final fallback.
</p>

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. |

## setAudioMuted

```TypeScript
setAudioMuted(mute: boolean): void
```

设置网页静音。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 表示是否将网页设置为静音状态。<br>true表示将网页设置为静音状态，false表示将网页取消静音状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setAutoPreconnect

```TypeScript
static setAutoPreconnect(enabled: boolean): void
```

Configure whether to enable automatic pre-connection to high-frequency URLs accessed during the application's
previous lifecycle after web initialization.

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Enable if true, disable if false. |

## setBackForwardCacheOptions

```TypeScript
setBackForwardCacheOptions(options: BackForwardCacheOptions): void
```

可以设置Web组件中前进后退缓存的相关选项。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | BackForwardCacheOptions | 是 | 用来控制Web组件前进后退缓存相关选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setBlanklessLoadingCacheCapacity

```TypeScript
static setBlanklessLoadingCacheCapacity(capacity: number) : number
```

设置无白屏加载方案的持久化缓存容量，返回实际生效值。当接口没有显式调用时，默认缓存容量为30MB。当实际缓存超过容量时，将采用淘汰不常用的过渡帧的方式清理。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 是 | 设置持久化缓存设置，单位MB，最大设置不超过100MB。<br>合法取值范围：[0, 100]，当设置为0时，无缓存空间，则功能全局不开启。<br>非法值设置行为：小于0时生效值为0，大于100时生效值为100。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际生效的容量值，范围0~100。<br>小于0时生效值为0，大于100时生效值为100。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) |  |

## setBlanklessLoadingWithKey

```TypeScript
setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode
```

设置无白屏加载是否启用，本接口必须与[getBlanklessInfoWithKey](arkts-arkweb-webviewcontroller-c.md#getblanklessinfowithkey-1)接口配套使用。

> **说明：**
>
> - 需在触发页面加载的接口之后调用，其他约束同[getBlanklessInfoWithKey](arkts-arkweb-webviewcontroller-c.md#getblanklessinfowithkey-1)。
>
> - 页面加载必须在调用本接口的组件中进行。
>
> - 当相似度较低时，系统将判定为跳变过大，启用插帧会失败。
>
> - 请在module.json5中添加权限: ohos.permission.INTERNET和ohos.permission.GET_NETWORK_INFO，具体权限的添加方法请参考
> [在配置文件中声明权限](../../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 唯一标识本页面的key值。必须与getBlanklessInfoWithKey接口的key值相同。<br>合法取值范围：非空，长度不超过2048个字符。<br>非法值设置行为：返回错误码WebBlanklessErrorCode，方案不生效。 |
| is_start | boolean | 是 | 是否启用开始插帧。true：启用，false：不启用。<br>传入undefined或null时为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebBlanklessErrorCode | 返回接口调用是否成功，具体见[WebBlanklessErrorCode](arkts-arkweb-webblanklesserrorcode-e.md)定义。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) |  |

## setBlanklessLoadingWithParams

```TypeScript
setBlanklessLoadingWithParams(key: string,
      param: BlanklessLoadingParam) : WebBlanklessErrorCode
```

Triggers frame interpolation and sets frame interpolation parameters. This API must be used in pair with the
getBlanklessInfoWithKey API.

Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | Key value that uniquely identifies the current page.<br>Value range: (0, 2048]<br>The key value must be the same as that of getBlanklessInfoWithKey. |
| param | BlanklessLoadingParam | 是 | The blankless loading parameter.<br>None |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebBlanklessErrorCode | WebBlanklessErrorCode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## setConnectionTimeout

```TypeScript
static setConnectionTimeout(timeout: number): void
```

设置网络连接超时时间，使用者可通过Web组件中的onErrorReceive方法获取超时错误码。若未调用该接口则默认超时时间为30秒。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | socket连接超时时间，以秒为单位，必须为大于0的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |

## setCustomUserAgent

```TypeScript
setCustomUserAgent(userAgent: string): void
```

设置自定义用户代理，会覆盖系统的用户代理。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | 用户自定义代理信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setDownloadDelegate

```TypeScript
setDownloadDelegate(delegate: WebDownloadDelegate): void
```

为当前的Web组件设置一个WebDownloadDelegate，该delegate用来接收页面内触发的下载进度的委托。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | WebDownloadDelegate | 是 | 用来接收下载进度的委托。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setErrorPageEnabled

```TypeScript
setErrorPageEnabled(enable: boolean): void
```

是否开启默认错误页，开启后onOverrideErrorPage会在页面发生错误的时候进行回调

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否开启 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setHostIP

```TypeScript
static setHostIP(hostName: string, address: string, aliveTime: number): void
```

设置主机域名解析后的IP地址。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostName | string | 是 | 要添加DNS记录的主机域名。 |
| address | string | 是 | 主机域名解析地址（支持IPv4，IPv6）。 |
| aliveTime | number | 是 | 缓存有效时间（秒）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## setHttpDns

```TypeScript
static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void
```

设置Web组件是否使用HTTPDNS解析DNS。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| secureDnsMode | SecureDnsMode | 是 | 使用HTTPDNS的模式。 |
| secureDnsConfig | string | 是 | HTTPDNS server的配置，必须是https协议并且只允许配置一个server。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |

## setNetworkAvailable

```TypeScript
setNetworkAvailable(enable: boolean): void
```

为网页设置网络状态。该功能用于在JavaScript中设置window.navigator.onLine属性。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置JavaScript中的`window.navigator.onLine`属性。<br>true表示设置JavaScript中的`window.navigator.onLine`属性为true，false表示设置JavaScript中的`window.navigator.onLine`属性为false。<br>默认值：true。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setPathAllowingUniversalAccess

```TypeScript
setPathAllowingUniversalAccess(pathList: Array<string>): void
```

设置一个路径列表，当file协议访问该路径列表中的资源时，允许跨域访问本地文件，也允许跨域访问其他在线资源。此外，当设置了路径列表时，file协议仅允许访问路径列表中的资源（
[fileAccess](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#fileaccess)的行为将会被此接口行为覆盖）。

setPathAllowingUniversalAccess放开目录的跨域访问限制是一个高风险操作。基于最小权限原则，当前el1，el2放开的路径是固定的，路径列表中的路径应符合以下任一路径格式：

1.应用文件目录的子目录（应用文件目录通过Ability Kit中的
[Context.filesDir](../../../../reference/apis-ability-kit/js-apis-inner-application-context.md#属性)获取），例如：

* /data/storage/el2/base/files/example
* /data/storage/el2/base/haps/entry/files/example

2.应用资源目录及其子目录（应用资源目录通过Ability Kit中的
[Context.resourceDir](../../../../reference/apis-ability-kit/js-apis-inner-application-context.md#属性)获取），例如：

* /data/storage/el1/bundle/entry/resources/resfile
* /data/storage/el1/bundle/entry/resources/resfile/example

3.从API version 21开始，还包括了应用缓存目录及其子目录（应用缓存目录通过Ability Kit中的
[Context.cacheDir](../../../../reference/apis-ability-kit/js-apis-inner-application-context.md#属性)获取），例如：

* /data/storage/el2/base/cache
* /data/storage/el2/base/haps/entry/cache/example
* 设置的目录路径中，不允许包含cache/web，否则会抛出异常码401。如果设置目录路径是cache，cache/web也不允许访问。

4.从API version 21开始，还包括了应用临时目录及其子目录（应用临时目录通过Ability Kit中的
[Context.tempDir](../../../../reference/apis-ability-kit/js-apis-inner-application-context.md#属性)获取），例如：

* /data/storage/el2/base/temp
* /data/storage/el2/base/haps/entry/temp/example

当路径列表中有其中一个路径不满足以上条件之一，则会抛出异常码401，并且设置路径列表失败。当设置的路径列表为空，则file协议可访问范围以
[fileAccess](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#fileaccess)的行为为准。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathList | Array&lt;string&gt; | 是 | 路径列表 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Parameter string is too long.<br>3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setPrintBackground

```TypeScript
setPrintBackground(enable: boolean): void
```

Set whether print web page background.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Whether to print the web page background.<br>The value **true** means to print theweb page background, and **false** means the opposite. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setRenderProcessMode

```TypeScript
static setRenderProcessMode(mode: RenderProcessMode): void
```

Set render process mode of the ArkWeb.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | RenderProcessMode | 是 | The render process mode for the ArkWeb.Call {@link getRenderProcessMode} to get the ArkWeb rendering subprocess mode of the current device.The enumerated value **0** indicates the single render subprocess mode,and **1** indicates the multi-render subprocess mode.If an invalid number other than the enumerated value of **RenderProcessMode** is passed,the multi-render subprocess mode is used by default. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.@static |

## setScrollable

```TypeScript
setScrollable(enable: boolean, type?: ScrollType): void
```

设置网页是否允许滚动。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示是否将网页设置为允许滚动。<br>true表示设置为允许滚动，false表示禁止滚动。<br>默认值：true。 |
| type | ScrollType | 否 | 网页可触发的滚动类型，支持缺省配置。<br> - enable为false时，表示禁止ScrollType类型的滚动，当ScrollType缺省时表示禁止所有类型网页滚动。<br> - enable为true时，ScrollType缺省与否，都表示允许所有类型的网页滚动。<br>传入null或undefined时会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setScrollbarMode

```TypeScript
static setScrollbarMode(scrollbarMode: ScrollbarMode): void
```

在Web页面场景，设置全局滚动条模式。不显式调用时，默认为
[ScrollbarMode.OVERLAY_LAYOUT_SCROLLBAR](arkts-arkweb-scrollbarmode-e.md)（非常驻滚动条）。

> **说明：**
>
> - 根据滚动条模式，改变当前应用所有web滚动条模式为常驻滚动条或非常驻滚动条。
>
> - 若[forceDisplayScrollBar](@ohos.web.WebAttribute#forcedisplayscrollbar)
> 接口与当前接口同时设置，forceDisplayScrollBar接口设置不生效。
>
> - 该接口需要在WebViewController绑定Web组件之前调用。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollbarMode | ScrollbarMode | 是 | 滚动条模式。 |

## setServiceWorkerWebSchemeHandler

```TypeScript
static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

Set web scheme handler for specific scheme. This is used for service worker.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scheme | string | 是 | String value for url scheme. |
| handler | WebSchemeHandler | 是 | Web scheme handler. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setSiteIsolationMode

```TypeScript
static setSiteIsolationMode(mode: SiteIsolationMode): void
```

Set the site isolation mode.

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SiteIsolationMode | 是 | The site isolation mode of the application, |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. Possible causes:1. Site Isolation mode is already set by the developer.2. Site Isolation mode cannot be strict in single-render-process mode.3. Site Isolation mode cannot be changed while Secure Shield mode is active.@static |

## setSocketIdleTimeout

```TypeScript
static setSocketIdleTimeout(timeout: number): void
```

设置ArkWeb中已使用过的空闲socket的超时时间。

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | ArkWeb中已经使用过的空闲socket的超时时间。<br>取值范围：[30,300]，单位：s。<br>小于30时生效值为30，大于300时生效值为300。 |

## setSoftKeyboardBehaviorMode

```TypeScript
setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void
```

Set the WebSoftKeyboardBehaviorMode to decide whether the keyboard will be shown/hidden automatically in particular
situation, for example, when web is inactive or active.

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | WebSoftKeyboardBehaviorMode | 是 | The WebSoftKeyboardBehaviorMode of this web. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string): void
```

Set the URL trust list for the ArkWeb.
When the URL trust list has been set, only the URLs in the list can be accessed.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| urlTrustList | string | 是 | the URL trust list in JSON format.An empty string means that all URLs are allowed to access. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Parameter string is too long. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void
```

Sets the URL trust list for the ArkWeb.

<p><strong>API Note</strong>:<br>
When the URL trust list is set, only the URLs in the list can be accessed.

Example of the urlTrustList:

{
"UrlPermissionList": [
{
"scheme": "https",
"host": "www.example1.com",
"port": 443,
"path": "pathA/pathB"
},
{
"scheme": "http",
"host": "*.example2.com",
"port": 80,
"path": "test1/test2/test3"
}
]
}
</p>

**起始版本：** 24

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| urlTrustList | string | 是 | The URL trust list in JSON format.An empty string means all URLs are allowed. |
| allowOpaqueOrigin | boolean | 是 | If true, loading of opaque origin URLs (e.g., javascript, data) isallowed. If false, it is not allowed. |
| supportWildcard | boolean | 是 | If true, wildcard matching is supported (e.g., *.example.com matches allsubdomains). If false, wildcard matching is not supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) |  |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Initialization error.The WebviewController must be associated with a Web component. |

## setUserAgentClientHintsEnabled

```TypeScript
static setUserAgentClientHintsEnabled(enabled: boolean): void
```

Enable the UserAgent Client Hints.

**起始版本：** 24

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | UserAgent Client Hints will enabled when set true. |

## setUserAgentForHosts

```TypeScript
static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void
```

设置用于指定主机的User-Agent，最多支持20,000个主机。

为同一个 User-Agent 多次设置相同的 Host 列表，将会覆盖之前的设置。也就是说，如果您希望取消某些Host使用指定的User-Agent，
您需要重新为该 User-Agent 设置 Host 列表。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. |
| hosts | Array&lt;string&gt; | 是 | The hosts to which the User-Agent apply. |

## setUserAgentMetadata

```TypeScript
setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void
```

Sets the User-Agent metadata corresponding to the User-Agent.

<p><strong>API Note</strong>:<br>
This User-Agent metadata will be used to populate the User-Agent client hints, They can provide the client's
branding and version information, the underlying operating system's branding and major version, as well as
details about the underlying device.

**起始版本：** 24

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The User-Agent string. |
| metaData | UserAgentMetadata | 是 | The UserAgentMetadata for the userAgent. |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean): void
```

设置是否启用网页调试功能。默认情况下，网页调试功能是关闭的。详情请参考DevTools工具。

安全提示：启用网页调试功能可以让用户检查修改Web页面内部状态，存在安全隐患因此，建议在应用正式发布版本时，不要开启此功能。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | 是 | 设置是否启用网页调试功能。<br>true表示启用网页调试功能。false表示不启用网页调试功能。<br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void
```

设置是否启用无线网页调试功能，默认不开启。

当没有指定端口port时，该接口等同于
[setWebDebuggingAccess](arkts-arkweb-webviewcontroller-c.md#setwebdebuggingaccess-1)
接口，ArkWeb会启动一个本地domain socket监听。
当指定了端口port时，ArkWeb会启动一个tcp socket监听。这时可以无线调试网页。

由于小于1024的端口号作为熟知或系统端口，在操作系统上需要特权才能开启，因此port的取值必须大于1024，否则该接口会抛出异常。

安全提示：启用网页调试功能可以让用户检查修改Web页面内部状态，存在安全隐患，不建议在应用正式发布版本中启用。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | 是 | 设置是否启用网页调试功能。<br/>true表示开启网页调试功能，false表示关闭网页调试功能。 |
| port | number | 是 | 表示 devtools 服务器的端口。指定端口后，将创建一个 TCP 服务器套接字，而不是 Unix 域套接字。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100023](../errorcode-webview.md#17100023-使用了不被允许的端口号) | The port number is not within the allowed range. |

## setWebDestroyMode

```TypeScript
static setWebDestroyMode(mode: WebDestroyMode): void
```

设置web组件的销毁模式

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | WebDestroyMode | 是 | web组件销毁模式，默认NORMAL_MODE |

## setWebSchemeHandler

```TypeScript
setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

Set web scheme handler for specific scheme. This is only used for related web component.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scheme | string | 是 | String value for url scheme. |
| handler | WebSchemeHandler | 是 | Web scheme handler. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## slideScroll

```TypeScript
slideScroll(vx: number, vy: number): void
```

按照指定速度模拟对页面的轻扫滚动动作。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vx | number | 是 | 轻扫滚动的水平速度分量，其中水平向右为速度正方向。<br>单位：vp/s。 |
| vy | number | 是 | 轻扫滚动的垂直速度分量，其中垂直向下为速度正方向。<br>单位：vp/s。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## startCamera

```TypeScript
startCamera(): void
```

开启当前网页摄像头捕获。使用摄像头功能前请在module.json5中添加权限: ohos.permission.CAMERA，具体权限的添加方法请参考
[在配置文件中声明权限](../../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## startDownload

```TypeScript
startDownload(url: string): void
```

使用Web组件的下载能力来下载指定的URL，比如下载网页中指定的图片。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 下载地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 11 - 21 |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 11 - 21 |

## stop

```TypeScript
stop(): void
```

停止页面加载。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## stopAllMedia

```TypeScript
stopAllMedia(): void
```

控制网页所有音视频停止。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## stopCamera

```TypeScript
stopCamera(): void
```

停止当前网页摄像头捕获。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## stopMicrophone

```TypeScript
stopMicrophone(): void
```

停止当前网页麦克风捕获。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## storeWebArchive

```TypeScript
storeWebArchive(baseName: string, autoName: boolean): Promise<string>
```

以Promise方式异步保存当前页面。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| baseName | string | 是 | 生成的离线网页存储位置，该值不能为空。 |
| autoName | boolean | 是 | 决定是否自动生成文件名。<br>false表示按baseName的文件名存储，true表示根据当前URL自动生成文件名，并按baseName的文件目录存储。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise实例，保存成功返回文件路径，保存失败返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## storeWebArchive

```TypeScript
storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void
```

以回调方式异步保存当前页面。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| baseName | string | 是 | 生成的离线网页存储位置，该值不能为空。 |
| autoName | boolean | 是 | 决定是否自动生成文件名。<br>false表示按baseName的文件名存储，true表示根据当前URL自动生成文件名，并按baseName的文件目录存储。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 返回文件存储路径，保存网页失败会返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## terminateRenderProcess

```TypeScript
terminateRenderProcess(): boolean
```

Destroy the rendering process.
Calling this interface will actively destroy the associated rendering process.
If the rendering process has not been started or destroyed, it has no effect.
In addition, destroying the rendering process will also affect all other instances associated with
the rendering process.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true if it was possible to terminate the render process, otherwise false.Calling this on a not yet started, or an already terminated render will have no effect. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |

## trimMemoryByPressureLevel

```TypeScript
static trimMemoryByPressureLevel(level: PressureLevel): void
```

根据指定的内存压力等级，主动清理Web组件占用的缓存。

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | PressureLevel | 是 | 需要清理内存的内存等级。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Parameter string is too long.<br>3.Parameter verification failed. |

## waitForAttached

```TypeScript
waitForAttached(timeout: number): Promise<ControllerAttachState>
```

Wait for the controller to attach a web component until timeout.

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 异步等待时长。取值范围: [0, 65535]单位: ms |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ControllerAttachState&gt; | Promise used to return the state of attach. |

## warmupServiceWorker

```TypeScript
static warmupServiceWorker(url: string): void
```

预热ServiceWorker，以提升首屏页面的加载速度（仅限于会使用ServiceWorker的页面）。在加载URL之前调用此API。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 需要预热ServiceWorker的URL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 12 - 21 |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URLlength exceeds 2048.<br>**适用版本：** 12 - 21 |

## webPageSnapshot

```TypeScript
webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void
```

获取网页全量绘制结果。

> **说明：**
>
> 此接口不支持并发调用。
>
> 仅支持对渲染进程上的资源进行截图：静态图片和文本。
>
> 如果页面有视频则截图时会显示该视频的占位图片，没有占位图片则显示空白。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | SnapshotInfo | 是 | 全量绘制结果入参。 |
| callback | AsyncCallback&lt;SnapshotResult&gt; | 是 | 全量绘制回调结果。 |

## zoom

```TypeScript
zoom(factor: number): void
```

调整当前网页的缩放比例，[zoomAccess](@ohos.web.WebAttribute#zoomAccess)需为true.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factor | number | 是 | 基于当前网页所需调整的相对缩放比例，入参要求大于0，当入参为1时为默认加载网页的缩放比例，入参小于1为缩小，入参大于1为放大。<br>取值范围：(0，100]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100004](../errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |

## zoomIn

```TypeScript
zoomIn(): void
```

调用此接口将当前网页进行放大，比例为25%。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100004](../errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |

## zoomOut

```TypeScript
zoomOut(): void
```

调用此接口将当前网页进行缩小，比例为20%。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error.The WebviewController must be associated with a Web component. |
| [17100004](../errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |

