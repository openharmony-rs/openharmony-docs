# WebviewController

WebviewController是Web组件各种行为的核心控制器，提供网页加载与导航控制、JavaScript交互、生命周期、滚动控制、页面缩放与内容查找、消息端口通信、缓存与证书管理等广泛功能。一个 WebviewController对象只能控制一个Web组件，且必须在Web组件和WebviewController绑定后，才能调用WebviewController上的方法（静态方法除外）。

**起始版本：** 9

<!--Device-webview-class WebviewController--><!--Device-webview-class WebviewController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## accessBackward

```TypeScript
accessBackward(): boolean
```

当前页面是否可后退，即当前页面是否有返回历史记录。 可以结合使用[getBackForwardEntries](#getbackforwardentries)来获取当前WebView的历史信息列表，以及使用 [accessStep](#accessstep)来判断是否可以按照给定的步数前进或后退。 > **说明：** > > 在Web组件首次加载过程中调用[setCustomUserAgent](#setcustomuseragent)，可能会导致在当前存在多个历史节点的情况下，获取 > 的accessBackward实际为false，即没有后退节点。建议先调用setCustomUserAgent方法设置UserAgent，再通过loadUrl加载具体页面。 > > 该现象是由于在Web组件首次加载时，调用[setCustomUserAgent](#setcustomuseragent)会导致组件重新加载并保持初始历史节点的 > 状态。随后新增的节点将替换初始历史节点，不会生成新的历史节点，导致accessBackward为false。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-accessBackward(): boolean--><!--Device-WebviewController-accessBackward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前页面可以后退返回true,否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## accessForward

```TypeScript
accessForward(): boolean
```

当前页面是否可前进，即当前页面是否有前进历史记录。 可以结合使用[getBackForwardEntries](#getbackforwardentries)来获取当前WebView的历史信息列表，以及使用 [accessStep](#accessstep)来判断是否可以按照给定的步数前进或后退。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-accessForward(): boolean--><!--Device-WebviewController-accessForward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 可以前进返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## accessStep

```TypeScript
accessStep(step: number): boolean
```

当前页面是否可前进或者后退给定的step步。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-accessStep(step: number): boolean--><!--Device-WebviewController-accessStep(step: number): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | number | 是 | 要跳转的步数，正数代表前进，负数代表后退。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 页面是否前进或后退。 <br>返回true表示可以前进或者后退，返回false表示不可以前进或后退。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## addIntelligentTrackingPreventionBypassingList

```TypeScript
static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

添加智能防跟踪功能绕过的域名列表。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void--><!--Device-WebviewController-static addIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | 是 | 绕过智能防跟踪功能的域名列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## avoidVisibleViewportBottom

```TypeScript
avoidVisibleViewportBottom(avoidHeight: number): void
```

设置Web网页可视视口底部避让高度。 > **说明：** > > - avoidHeight有效值区间为[0, Web组件高度]，超出有效值区间时取边界值。 > > - 该接口高度设置为非0时，Web组件位置和尺寸不变，可视视口向上避让avoidHeight，表现为Web网页内容抬升avoidHeight。该接口一般用于应用自定义网页底部避让区，不建议和点击web网页可编辑区拉起键盘的 > 场景同时使用。同时使用时，键盘弹起避让模式将使用OVERLAYS_CONTENT。 > > - 该接口高度设置为0时，Web网页内容可恢复，键盘弹起避让模式将使用keyboardAvoidMode()声明的模式。

**起始版本：** 20

<!--Device-WebviewController-avoidVisibleViewportBottom(avoidHeight: number): void--><!--Device-WebviewController-avoidVisibleViewportBottom(avoidHeight: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| avoidHeight | number | 是 | 设置Web网页可视视口底部避让高度。 <br>单位：vp <br>合法取值范围：0~Web组件高度 <br>非法值设置行为：小于0取值为0，大于Web组件高度取值为Web组件高度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This functionality is not supported. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## backOrForward

```TypeScript
backOrForward(step: number): void
```

按照历史栈，前进或者后退指定步长的页面，当历史栈中不存在对应步长的页面时，不会进行页面跳转。 前进或者后退页面时，直接使用已加载过的网页，无需重新加载网页。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-backOrForward(step: number): void--><!--Device-WebviewController-backOrForward(step: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | number | 是 | 需要前进或后退的步长。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## backward

```TypeScript
backward(): void
```

按照历史栈，后退一个页面。一般结合[accessBackward](#accessbackward)一起使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-backward(): void--><!--Device-WebviewController-backward(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearBlanklessLoadingCache

```TypeScript
static clearBlanklessLoadingCache(keys?: Array<string>) : void
```

清除指定key值页面无白屏优化缓存，本接口只清除缓存。 在小程序或Web应用场景中，当页面加载时内容变化显著，可能会出现一次明显的跳变。若对此跳变有所顾虑，可使用该接口清除页面缓存。 > **说明：** > > - 清除之后的页面，需在第三次加载页面时才会产生优化效果。

**起始版本：** 20

<!--Device-WebviewController-static clearBlanklessLoadingCache(keys?: Array<string>) : void--><!--Device-WebviewController-static clearBlanklessLoadingCache(keys?: Array<string>) : void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 否 | 清除Blankless优化方案页面的key值列表， key值为[getBlanklessInfoWithKey](#getblanklessinfowithkey)中指定过的。 <br>默认值：所有Blankless优化方案缓存的页面key列表。 <br>合法取值范围：长度不超过2048，key列表长度&lt;=100。key和加载页面时输入给ArkWeb的相同。 <br>非法值设置行为：传入undefined/null会抛出异常错误码401；key长度超过2048时该key不生效；长度超过100时，取前100个；当为空时，使用默认值。 |

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-clearClientAuthenticationCache(): void--><!--Device-WebviewController-clearClientAuthenticationCache(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearHistory

```TypeScript
clearHistory(): void
```

删除所有前进后退记录，不建议在onErrorReceive与onPageBegin中调用clearHistory，会造成异常退出。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-clearHistory(): void--><!--Device-WebviewController-clearHistory(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearHostIP

```TypeScript
static clearHostIP(hostName: string): void
```

清除指定主机域名解析后的IP地址。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static clearHostIP(hostName: string): void--><!--Device-WebviewController-static clearHostIP(hostName: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostName | string | 是 | 要清除DNS记录的主机域名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

## clearIntelligentTrackingPreventionBypassingList

```TypeScript
static clearIntelligentTrackingPreventionBypassingList(): void
```

删除通过addIntelligentTrackingPreventionBypassingList接口添加的所有域名。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static clearIntelligentTrackingPreventionBypassingList(): void--><!--Device-WebviewController-static clearIntelligentTrackingPreventionBypassingList(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## clearMatches

```TypeScript
clearMatches(): void
```

清除所有通过[searchAllAsync](#searchallasync)匹配到的高亮字符查找结果。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-clearMatches(): void--><!--Device-WebviewController-clearMatches(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearPrefetchedResource

```TypeScript
static clearPrefetchedResource(cacheKeyList: Array<string>): void
```

根据指定的缓存key列表清除对应的预获取资源缓存。入参中的缓存key必须是[prefetchResource](#prefetchresource)指定预获取到的资 源缓存key。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static clearPrefetchedResource(cacheKeyList: Array<string>): void--><!--Device-WebviewController-static clearPrefetchedResource(cacheKeyList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cacheKeyList | Array&lt;string&gt; | 是 | 用于后续查询预获取资源缓存的key。仅支持字母和数字，未传入或传入空则取默认值url作为key。 |

## clearServiceWorkerWebSchemeHandler

```TypeScript
static clearServiceWorkerWebSchemeHandler(): void
```

清除应用中设置的所有用于拦截ServiceWorker的WebSchemeHandler。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static clearServiceWorkerWebSchemeHandler(): void--><!--Device-WebviewController-static clearServiceWorkerWebSchemeHandler(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## clearSslCache

```TypeScript
clearSslCache(): void
```

清除Web组件记录的SSL证书错误事件对应的用户操作行为。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-clearSslCache(): void--><!--Device-WebviewController-clearSslCache(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## clearWebSchemeHandler

```TypeScript
clearWebSchemeHandler(): void
```

清除Web组件设置的所有WebSchemeHandler。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-clearWebSchemeHandler(): void--><!--Device-WebviewController-clearWebSchemeHandler(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## closeAllMediaPresentations

```TypeScript
closeAllMediaPresentations(): void
```

控制网页所有全屏视频关闭。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-closeAllMediaPresentations(): void--><!--Device-WebviewController-closeAllMediaPresentations(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## closeCamera

```TypeScript
closeCamera(): void
```

关闭当前网页摄像头捕获。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-closeCamera(): void--><!--Device-WebviewController-closeCamera(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## constructor

```TypeScript
constructor(webTag?: string)
```

用于创建 WebviewController 对象的构造函数。 > **说明：** > > 不传参：new webview.WebviewController()表示构造函数为空，不使用C API时不需要传参。 > > 传参且参数是合法字符串：new webview.WebviewController("xxx")，用于开发者区分多实例，并调用对应实例下的方法。 > > 传入参数为空：new webview.WebviewController("")或new webview.WebviewController(undefined)，该场景下参数无意义，无法区分多个实例，直接返回 > undefined，需要开发者判断返回值是否正常。 > > Web组件销毁后会解绑WebViewController，之后调用WebviewController的非静态方法会抛出 > [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联)异常，应注意调 > 用时机和捕获异常，防止进程异常退出。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-constructor(webTag?: string)--><!--Device-WebviewController-constructor(webTag?: string)-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webTag | string | 否 | 指定了 Web 组件的名称。 |

## createPdf

```TypeScript
createPdf(configuration: PdfConfiguration, callback: AsyncCallback<PdfData>): void
```

异步callback方式获取指定网页的数据流。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-createPdf(configuration: PdfConfiguration, callback: AsyncCallback<PdfData>): void--><!--Device-WebviewController-createPdf(configuration: PdfConfiguration, callback: AsyncCallback<PdfData>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | [PdfConfiguration](arkts-arkweb-webview-pdfconfiguration-i.md) | 是 | 生成PDF所需参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[PdfData](arkts-arkweb-webview-pdfdata-c.md)&gt; | 是 | 回调返回网页PDF数据流。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## createPdf

```TypeScript
createPdf(configuration: PdfConfiguration): Promise<PdfData>
```

以Promise方式异步获取指定网页的数据流。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-createPdf(configuration: PdfConfiguration): Promise<PdfData>--><!--Device-WebviewController-createPdf(configuration: PdfConfiguration): Promise<PdfData>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | [PdfConfiguration](arkts-arkweb-webview-pdfconfiguration-i.md) | 是 | 生成PDF所需参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PdfData](arkts-arkweb-webview-pdfdata-c.md)&gt; | Promise实例，返回网页PDF数据流（PdfData对象，包含ArrayBuffer表示的PDF二进制数据）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## createWebMessagePorts

```TypeScript
createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>
```

创建Web消息端口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>--><!--Device-WebviewController-createWebMessagePorts(isExtentionType?: boolean): Array<WebMessagePort>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isExtentionType | boolean | 否 | 是否使用扩展增强接口。 <br>true表示使用扩展增强接口，false表示不使用扩展增强接口。 <br>默认值：false。 <br>传入undefined或null会抛出异常错误码401。<br>**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[WebMessagePort](arkts-arkweb-webview-webmessageport-i.md)&gt; | web消息端口列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed.<br>**适用版本：** 10+ |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## createWebPrintDocumentAdapter

```TypeScript
createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter
```

创建web相关打印功能。

**起始版本：** 11

<!--Device-WebviewController-createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter--><!--Device-WebviewController-createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobName | string | 是 | 需要打印的文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| print.PrintDocumentAdapter | 打印文档的适配器，用于控制打印行为和打印任务，可通过打印服务打印当前网页内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>): void
```

对Web内核赋予自定义协议URL的跨域请求与fetch请求的权限。当Web在跨域fetch自定义协议URL时，该fetch请求可被 onInterceptRequest事件接口所拦截，从而开发者可以进一步处理该请求。建议在任何Web组件初始化之前调用该接口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>): void--><!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemes | Array&lt;[WebCustomScheme](arkts-arkweb-webview-webcustomscheme-i.md)&gt; | 是 | 自定义协议配置，最多支持同时配置10个自定义协议。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100020](../errorcode-webview.md#17100020-注册自定义协议失败) | Failed to register custom schemes.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## customizeSchemes

```TypeScript
static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void
```

对Web内核赋予自定义协议URL的跨域请求与fetch请求的权限。当Web在跨域fetch自定义协议URL时，该fetch请求可被 onInterceptRequest事件接口所拦截，从而开发者可以进一步处理该请求。建议在任何Web组件初始化之前调用该接口。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void--><!--Device-WebviewController-static customizeSchemes(schemes: Array<WebCustomScheme>, lazyInitWebEngine: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemes | Array&lt;[WebCustomScheme](arkts-arkweb-webview-webcustomscheme-i.md)&gt; | 是 | 自定义协议配置，最多支持同时配置10个自定义协议。 |
| lazyInitWebEngine | boolean | 是 | 表示接口内部是否跳过初始化WebEngine。 <br>true表示接口内部跳过初始化WebEngine，并将注册的Schemes暂存，当它真正初始化时，这些Schemes将传递给WebEngine。false表示接口内部自动进行WebEngine初始化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100020](../errorcode-webview.md#17100020-注册自定义协议失败) | Failed to register custom schemes. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. The length of the schemes array is greater than 10. 2. The character length of the scheme is greater than 32. 3. The character in the scheme is not within the allowed range of lowercase English letters, numbers, and the symbols ".", "+", "-". |

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string): void
```

删除通过[registerJavaScriptProxy](#registerjavascriptproxy)或者 javaScriptProxy注册到window上的指定name的应用侧JavaScript对象。删除操作在页面下次（重新）加载后生效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-deleteJavaScriptRegister(name: string): void--><!--Device-WebviewController-deleteJavaScriptRegister(name: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 注册对象的名称，可在网页侧JavaScript中通过此名称调用应用侧JavaScript对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100008](../errorcode-webview.md#17100008-删除不存在的javascriptproxy) | Failed to delete JavaScriptProxy because it does not exist. |

## enableAdsBlock

```TypeScript
enableAdsBlock(enable: boolean): void
```

启用广告过滤功能。 > **说明：** > > - 广告过滤功能需要release包，使用debug包不生效。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-enableAdsBlock(enable: boolean): void--><!--Device-WebviewController-enableAdsBlock(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用广告过滤功能。 <br>true表示启用广告过滤功能，false表示取消广告过滤功能。 <br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Parameter string is too long. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## enableAdvancedSecurityMode

```TypeScript
static enableAdvancedSecurityMode(securityParams: SecurityParams): void
```

通过配置安全特性选项禁用特定的Web引擎能力，以降低攻击面。典型使用场景包括：高安全要求的应用（如金融、政务类应用）应启用高级安全模式以禁用不必要的Web引擎能力。 > **说明：** > > - 该接口为全局静态API，在整个APP生命周期中调用一次即可，不需要重复调用。 > > - 必须在[initializeWebEngine()](#initializewebengine)之前调用，否则设置无效。 > 26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-static enableAdvancedSecurityMode(securityParams: SecurityParams): void--><!--Device-WebviewController-static enableAdvancedSecurityMode(securityParams: SecurityParams): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| securityParams | [SecurityParams](arkts-arkweb-webview-securityparams-i.md) | 是 | 安全特性选项配置。 |

## enableBackForwardCache

```TypeScript
static enableBackForwardCache(features: BackForwardCacheSupportedFeatures): void
```

开启Web组件前进后退缓存功能，通过参数指定是否允许使用特定的页面进入前进后退缓存。 需要在[initializeWebEngine()](#initializewebengine)初始化内核之前调用。

**起始版本：** 12

<!--Device-WebviewController-static enableBackForwardCache(features: BackForwardCacheSupportedFeatures): void--><!--Device-WebviewController-static enableBackForwardCache(features: BackForwardCacheSupportedFeatures): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| features | [BackForwardCacheSupportedFeatures](arkts-arkweb-webview-backforwardcachesupportedfeatures-c.md) | 是 | 允许使用特定的页面进入前进后退缓存中。 |

## enableIntelligentTrackingPrevention

```TypeScript
enableIntelligentTrackingPrevention(enable: boolean): void
```

启用智能防跟踪功能。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-enableIntelligentTrackingPrevention(enable: boolean): void--><!--Device-WebviewController-enableIntelligentTrackingPrevention(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用智能防跟踪功能。 <br>true表示启用智能防跟踪功能，false表示不启用智能防跟踪功能。 <br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## enablePrivateNetworkAccess

```TypeScript
static enablePrivateNetworkAccess(enable: boolean): void
```

设置私有网络访问检查功能（Private Network Access）的启用状态。 启用后，Web组件将对私有网络请求（如访问本地服务器或内网资源）进行CORS预检。它会先发送OPTIONS预检请求，获取目标服务器的显式授权，然后传输实际数据。禁用此功能将跳过安全检查。 > **说明：** > > 当前私有网络访问检查功能主要针对Web Worker场景生效。

**起始版本：** 20

<!--Device-WebviewController-static enablePrivateNetworkAccess(enable: boolean): void--><!--Device-WebviewController-static enablePrivateNetworkAccess(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用私有网络访问检查功能开关。true表示启用，false表示禁用。 |

## enableSafeBrowsing

```TypeScript
enableSafeBrowsing(enable: boolean): void
```

启用检查网站安全风险的功能，非法和欺诈网站是强制启用的，不能通过此功能禁用。 本功能默认不生效，OpenHarmony只提供恶意网址拦截页WebUI，网址风险检测以及显示WebUI的功能由Vendor实现。推荐在WebContentsObserver中监听跳转 [DidStartNavigation](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/content/public/browser/web_contents_observer.h) 、 [DidRedirectNavigation](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/content/public/browser/web_contents_observer.h) 进行检测。 > **说明：** > > 该接口不生效，调用不会产生任何实际效果。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-enableSafeBrowsing(enable: boolean): void--><!--Device-WebviewController-enableSafeBrowsing(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用检查网站安全风险的功能。 <br>true表示启用检查网站安全风险的功能，false表示不启用检查网站安全风险的功能。 <br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## enableWholeWebPageDrawing

```TypeScript
static enableWholeWebPageDrawing(): void
```

设置开启网页全量绘制能力。仅在web初始化时设置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static enableWholeWebPageDrawing(): void--><!--Device-WebviewController-static enableWholeWebPageDrawing(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## executeAIPageCommand

```TypeScript
executeAIPageCommand(command: string): Promise<string>
```

异步执行`AIPageCommand`。该接口通过JSON字符串形式的`command`参数指定命令类型和命令参数，使用Promise异步回调。 > **说明：** > > - 不同命令的返回格式不同，详细说明请参见[AIPageCommand](../../../reference/apis-arkweb/arkts-apis-webview-AIPageCommand.md)和 > [AIPageInteraction](../../../reference/apis-arkweb/arkts-apis-webview-AIPageInteraction.md)。 > > - 当命令无法分发或无结果返回时，Promise可能返回空字符串。 > > - 返回值非空时为JSON字符串，应用可通过`JSON.parse`解析后使用。 > 26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-executeAIPageCommand(command: string): Promise<string>--><!--Device-WebviewController-executeAIPageCommand(command: string): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | JSON格式的命令参数。不同命令的参数格式不同，查询类命令请参见 [AIPageCommand](../../../reference/apis-arkweb/arkts-apis-webview-AIPageCommand.md)，交互类命令请参见 [AIPageInteraction](../../../reference/apis-arkweb/arkts-apis-webview-AIPageInteraction.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回JSON格式的命令执行结果。不同命令的返回格式不同。命令无法分发或无返回值时，返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100024](../errorcode-webview.md#17100024-aipagecommand格式错误) | Command format error. The command parameter does not conform to the JSON format requirements. |

## forward

```TypeScript
forward(): void
```

按照历史栈，前进一个页面。一般结合[accessForward](#accessforward)一起使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-forward(): void--><!--Device-WebviewController-forward(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getActiveWebEngineVersion

```TypeScript
static getActiveWebEngineVersion(): ArkWebEngineVersion
```

获取当前ArkWeb内核版本。

**起始版本：** 20

<!--Device-WebviewController-static getActiveWebEngineVersion(): ArkWebEngineVersion--><!--Device-WebviewController-static getActiveWebEngineVersion(): ArkWebEngineVersion-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArkWebEngineVersion](arkts-arkweb-webview-arkwebengineversion-e.md) | 返回由[ArkWebEngineVersion]{ |

## getAttachState

```TypeScript
getAttachState(): ControllerAttachState
```

查询当前WebViewController是否绑定一个Web组件。

**起始版本：** 20

<!--Device-WebviewController-getAttachState(): ControllerAttachState--><!--Device-WebviewController-getAttachState(): ControllerAttachState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md) | WebViewController与Web组件的绑定状态。 |

## getBackForwardEntries

```TypeScript
getBackForwardEntries(): BackForwardList
```

获取当前WebView的历史信息列表。 > **说明：** > > onLoadIntercept在加载开始的时候触发，该时刻还未生成历史节点，所以在onLoadIntercept中调用 > getBackForwardEntries拿到的历史栈不包括当前正在加载中的跳转。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getBackForwardEntries(): BackForwardList--><!--Device-WebviewController-getBackForwardEntries(): BackForwardList-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BackForwardList](arkts-arkweb-webview-backforwardlist-i.md) | 当前WebView的历史信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getBlanklessInfoWithKey

```TypeScript
getBlanklessInfoWithKey(key: string) : BlanklessInfo
```

获取页面首屏加载预测信息（详细说明见[BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md)），并开始本次加载过渡帧生成，应用根据此信息确定是否需要启用无白屏加载。 必须与[setBlanklessLoadingWithKey](#setblanklessloadingwithkey)接口配套使用，并且必须在触发加载页面的接口之前或在`onLoadIntercept`中调用。 需在`WebViewController`与Web组件绑定后才能使用。 > **说明：** > > - 持久缓存容量：默认大小为30MB（约30页），可以通过接口[setBlanklessLoadingCacheCapacity](#setblanklessloadingcachecapacity)设置缓存容量，具体见该接口说明。 > 超过容量时根据LRU（Least Recently Used，淘汰不常用缓存的策略）机制更新缓存。自动清理超过7天的持久缓存数据，缓存清除后第三次加载页面开始有优化效果。 > > - 如果发现快照相似度（即[BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md)极低，请确认key值是否传递正确。 > > - 调用本接口后，将启用页面加载快照检测及生成过渡帧计算，会产生一定的资源开销。 > > - 启用无白屏加载的页面会带来一定的资源开销，开销的大小与Web组件的分辨率相关。假设分辨率的宽度和高度分别为：w, h。页面在打开阶段会增加峰值内存，增加约12 * w * h B，页面打开后内存回收，不影响稳态内存。 > 增加固态应用缓存的大小，每个页面增加的缓存约w * h / 10 B，缓存位于应用缓存的位置。 > > - 请在module.json5中添加权限: ohos.permission.INTERNET和ohos.permission.GET_NETWORK_INFO， > 具体权限的添加方法请参考[在配置文件中声明权限](../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 20

<!--Device-WebviewController-getBlanklessInfoWithKey(key: string) : BlanklessInfo--><!--Device-WebviewController-getBlanklessInfoWithKey(key: string) : BlanklessInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 唯一标识本页面的key值。 <br>合法取值范围：非空，长度不超过2048个字符。 <br>设置非法值时不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md) | 页面首屏加载预测信息对象，应用需根据此信息来决策是否启用无白屏加载插帧。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) |  |

## getCertificate

```TypeScript
getCertificate(): Promise<Array<cert.X509Cert>>
```

获取当前网站的证书信息。使用Web组件加载https网站，会进行SSL证书校验，该接口会通过Promise异步返回当前网站的X509格式证书（X509Cert证书类型定义见 [X509Cert](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-x509cert-i.md)定义），便于开发者展示网站证书信息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getCertificate(): Promise<Array<cert.X509Cert>>--><!--Device-WebviewController-getCertificate(): Promise<Array<cert.X509Cert>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;cert.X509Cert&gt;&gt; | Promise实例，用于获取当前加载的https网站的X509格式证书数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a web component. |

## getCertificate

```TypeScript
getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void
```

获取当前网站的证书信息。使用Web组件加载https网站，会进行SSL证书校验，该接口会通过AsyncCallback异步返回当前网站的X509格式证书（X509Cert证书类型定义见 [X509Cert](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-x509cert-i.md)），便于开发者展示网站证书信息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void--><!--Device-WebviewController-getCertificate(callback: AsyncCallback<Array<cert.X509Cert>>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;cert.X509Cert&gt;&gt; | 是 | 通过AsyncCallback异步返回当前网站的X509格式证书。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a web component. |

## getCustomUserAgent

```TypeScript
getCustomUserAgent(): string
```

获取自定义用户代理。 默认User-Agent定义与使用场景请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getCustomUserAgent(): string--><!--Device-WebviewController-getCustomUserAgent(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 用户自定义代理信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getDefaultUserAgent

```TypeScript
static getDefaultUserAgent(): string
```

获取默认用户代理。 此接口只允许在UI线程调用。 默认User-Agent定义与使用场景请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)

**起始版本：** 14

<!--Device-WebviewController-static getDefaultUserAgent(): string--><!--Device-WebviewController-static getDefaultUserAgent(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ArkWeb默认User-Agent字符串。 |

## getErrorPageEnabled

```TypeScript
getErrorPageEnabled(): boolean
```

查询是否启用了默认错误页功能。

**起始版本：** 20

<!--Device-WebviewController-getErrorPageEnabled(): boolean--><!--Device-WebviewController-getErrorPageEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否启用默认错误页功能。 <br>true：已启用；false：未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getFavicon

```TypeScript
getFavicon(): image.PixelMap
```

获取页面的favicon图标。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getFavicon(): image.PixelMap--><!--Device-WebviewController-getFavicon(): image.PixelMap-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | 页面favicon图标的PixelMap对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getHitTest

```TypeScript
getHitTest(): WebHitTestType
```

获取当前被点击区域的元素类型。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** [getLastHitTest](#getlasthittest)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getHitTest(): WebHitTestType--><!--Device-WebviewController-getHitTest(): WebHitTestType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebHitTestType](arkts-arkweb-webview-webhittesttype-e.md) | 被点击区域的元素类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getHitTestValue

```TypeScript
getHitTestValue(): HitTestValue
```

获取当前被点击区域的元素信息。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** [getLastHitTest](#getlasthittest)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getHitTestValue(): HitTestValue--><!--Device-WebviewController-getHitTestValue(): HitTestValue-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HitTestValue](arkts-arkweb-webview-hittestvalue-i.md) | 点击区域的元素信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getLastHitTest

```TypeScript
getLastHitTest(): HitTestValue
```

获取上一次被点击区域的元素信息。

**起始版本：** 18

<!--Device-WebviewController-getLastHitTest(): HitTestValue--><!--Device-WebviewController-getLastHitTest(): HitTestValue-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HitTestValue](arkts-arkweb-webview-hittestvalue-i.md) | 点击区域的元素信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getLastJavascriptProxyCallingFrameUrl

```TypeScript
getLastJavascriptProxyCallingFrameUrl(): string
```

通过[registerJavaScriptProxy](#registerjavascriptproxy)或者 javaScriptProxy注入JavaScript对象到window对象中。该接口可以获取最后一次调用注入的对象的frame的URL。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getLastJavascriptProxyCallingFrameUrl(): string--><!--Device-WebviewController-getLastJavascriptProxyCallingFrameUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 最后一次调用注入的对象的frame的URL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getMediaPlaybackState

```TypeScript
getMediaPlaybackState(): MediaPlaybackState
```

查询当前网页音视频播放状态。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getMediaPlaybackState(): MediaPlaybackState--><!--Device-WebviewController-getMediaPlaybackState(): MediaPlaybackState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaPlaybackState](arkts-arkweb-webview-mediaplaybackstate-e.md) | 当前网页的播放状态，具体值为NONE、PLAYING、PAUSED、STOPPED。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getOriginalUrl

```TypeScript
getOriginalUrl(): string
```

获取当前页面的原始URL地址。 风险提示：如果想获取URL来做JavascriptProxy通信接口认证，请使用 [getLastJavascriptProxyCallingFrameUrl&lt;sup&gt;12+&lt;/sup&gt;](#getlastjavascriptproxycallingframeurl)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getOriginalUrl(): string--><!--Device-WebviewController-getOriginalUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前页面的原始URL地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getPageHeight

```TypeScript
getPageHeight(): number
```

获取当前网页的页面高度。具体使用详情请参考[获取网页内容高度](../../../web/web-getpage-height.md)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getPageHeight(): number--><!--Device-WebviewController-getPageHeight(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前网页的页面高度。单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getPageOffset

```TypeScript
getPageOffset(): ScrollOffset
```

获取网页当前的滚动偏移量（不包含过滚动偏移量）。

**起始版本：** 20

<!--Device-WebviewController-getPageOffset(): ScrollOffset--><!--Device-WebviewController-getPageOffset(): ScrollOffset-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScrollOffset](arkts-arkweb-webview-scrolloffset-i.md) | 网页当前的滚动偏移量（不包含过滚动偏移量），包含x和y坐标，单位为vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## getPrintBackground

```TypeScript
getPrintBackground(): boolean
```

查询webview是否打印网页背景。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getPrintBackground(): boolean--><!--Device-WebviewController-getPrintBackground(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回webview是否打印网页背景。 <br>true:打印网页背景；false:不打印网页背景。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getProgress

```TypeScript
getProgress() : number
```

获取当前网页加载进度。

**起始版本：** 20

<!--Device-WebviewController-getProgress() : number--><!--Device-WebviewController-getProgress() : number-End-->

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

查询ArkWeb的渲染子进程模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static getRenderProcessMode(): RenderProcessMode--><!--Device-WebviewController-static getRenderProcessMode(): RenderProcessMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderProcessMode](arkts-arkweb-webview-renderprocessmode-e.md) | 渲染子进程模式类型。 <br>调用getRenderProcessMode()获取当前设备的ArkWeb渲染子进程模式，枚举值0为单子进程模式，枚举值1为多子进程模式。 <br>如果获取的值不在RenderProcessMode枚举值范围内，则默认为多渲染子进程模式。 |

## getScrollOffset

```TypeScript
getScrollOffset(): ScrollOffset
```

获取网页当前的滚动偏移量（包含过滚动偏移量）。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getScrollOffset(): ScrollOffset--><!--Device-WebviewController-getScrollOffset(): ScrollOffset-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScrollOffset](arkts-arkweb-webview-scrolloffset-i.md) | 网页当前的滚动偏移量（包含过滚动偏移量），包含x和y坐标，单位为vp。 |

## getScrollable

```TypeScript
getScrollable(): boolean
```

获取当前网页是否允许滚动。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getScrollable(): boolean--><!--Device-WebviewController-getScrollable(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前网页是否允许滚动。 <br>true为允许滚动，false为禁止滚动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getSecurityLevel

```TypeScript
getSecurityLevel(): SecurityLevel
```

获取当前网页的安全级别。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getSecurityLevel(): SecurityLevel--><!--Device-WebviewController-getSecurityLevel(): SecurityLevel-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SecurityLevel | 当前网页的安全级别，具体值为NONE、SECURE、WARNING、DANGEROUS。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getSiteIsolationMode

```TypeScript
static getSiteIsolationMode(): SiteIsolationMode
```

查询当前生效的站点隔离模式。

**起始版本：** 21

<!--Device-WebviewController-static getSiteIsolationMode(): SiteIsolationMode--><!--Device-WebviewController-static getSiteIsolationMode(): SiteIsolationMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SiteIsolationMode](arkts-arkweb-webview-siteisolationmode-e.md) | 站点隔离模式类型。 <br>getSiteIsolationMode()查询当前生效的站点隔离模式。 |

## getSubframeErrorPageEnabled

```TypeScript
getSubframeErrorPageEnabled(): boolean
```

查询是否启用了subframe错误页功能。 26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-getSubframeErrorPageEnabled(): boolean--><!--Device-WebviewController-getSubframeErrorPageEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否启用subframe错误页功能。 <br>- true：已启用subframe错误页功能（即enable和includeSubframe均为true）； <br>- false：未启用subframe错误页功能（包括未启用错误页功能、或启用了错误页功能但未启用subframe错误页功能两种情况）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getSurfaceId

```TypeScript
getSurfaceId(): string
```

获取ArkWeb对应Surface的ID，此ID可用于网页截图。 > **说明：** > > 仅Web组件渲染模式是ASYNC_RENDER时有效。getSurfaceId需要在Web组件初始化之后才能获取到值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getSurfaceId(): string--><!--Device-WebviewController-getSurfaceId(): string-End-->

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getTitle(): string--><!--Device-WebviewController-getTitle(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前网页的标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getUrl

```TypeScript
getUrl(): string
```

获取当前页面的URL地址。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getUrl(): string--><!--Device-WebviewController-getUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前页面的URL地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getUserAgent

```TypeScript
getUserAgent(): string
```

获取当前默认用户代理。 默认User-Agent定义与使用场景请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getUserAgent(): string--><!--Device-WebviewController-getUserAgent(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 默认用户代理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## getUserAgentClientHintsEnabled

```TypeScript
static getUserAgentClientHintsEnabled(): boolean
```

查询User-Agent Client Hints功能当前是否开启。

**起始版本：** 24

<!--Device-WebviewController-static getUserAgentClientHintsEnabled(): boolean--><!--Device-WebviewController-static getUserAgentClientHintsEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回User-Agent Client Hints功能开启状态。true表示已开启；false表示已关闭。 |

## getUserAgentMetadata

```TypeScript
getUserAgentMetadata(userAgent: string): UserAgentMetadata
```

查询userAgent对应的UserAgent Metadata信息。

**起始版本：** 24

<!--Device-WebviewController-getUserAgentMetadata(userAgent: string): UserAgentMetadata--><!--Device-WebviewController-getUserAgentMetadata(userAgent: string): UserAgentMetadata-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | 用户自定义代理信息。可以使用[getUserAgent](#getuseragent)获取当前默认用户代 理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md) | userAgent对应的[UserAgentMetadata]{ |

## getWebId

```TypeScript
getWebId(): number
```

获取Web组件的索引值，用于多个Web组件的管理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-getWebId(): number--><!--Device-WebviewController-getWebId(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Web组件的索引值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(): Promise<boolean>
```

通过Promise方式异步查找当前页面是否存在图像。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-hasImage(): Promise<boolean>--><!--Device-WebviewController-hasImage(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise实例，返回查找页面是否存在图像。 <br> true表示页面存在图像；false表示页面不存在图像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## hasImage

```TypeScript
hasImage(callback: AsyncCallback<boolean>): void
```

通过Callback方式异步查找当前页面是否存在图像。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-hasImage(callback: AsyncCallback<boolean>): void--><!--Device-WebviewController-hasImage(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 返回查找页面是否存在图像。 <br> true表示页面存在图像；false表示页面不存在图像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## initializeWebEngine

```TypeScript
static initializeWebEngine(): void
```

在Web组件初始化之前，通过此接口加载Web引擎的动态库文件，以提高启动性能。自动预连接历史访问过的高频网站。 > **说明：** > > - initializeWebEngine不支持在异步线程中调用，否则会造成崩溃。 > > - initializeWebEngine全局生效，在整个APP生命周期中调用一次即可，不需要重复调用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static initializeWebEngine(): void--><!--Device-WebviewController-static initializeWebEngine(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## injectOfflineResources

```TypeScript
injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void
```

将本地离线资源注入到内存缓存中，以提升页面首次启动速度。 内存缓存中的资源由内核自动管理，当注入的资源过多导致内存压力过大，内核自动释放未使用的资源，应避免注入大量资源到内存缓存中。 正常情况下，资源的有效期由提供的Cache-Control或Expires响应头控制其有效期，默认的有效期为86400秒，即1天。 资源的MIMEType通过提供的Content-Type响应头配置，Content-Type需符合标准，否则无法正常使用，MODULE_JS必须提供有效的MIMEType，其他类型可不提供。 以此方式注入的资源，仅支持通过HTML中的标签加载。如果业务网页中的script标签使用了crossorigin属性，则必须在接口的responseHeaders参数中设置Cross-Origin响应头的值为anonymous 或use-credentials。 当调用`webview.WebviewController.SetRenderProcessMode(webview.RenderProcessMode.MULTIPLE)`接口后，应用会启动多渲染进程模式，此接口在此场景下不 会生效。

**起始版本：** 12

<!--Device-WebviewController-injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void--><!--Device-WebviewController-injectOfflineResources(resourceMaps: Array<OfflineResourceMap>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceMaps | Array&lt;[OfflineResourceMap](arkts-arkweb-webview-offlineresourcemap-i.md)&gt; | 是 | 本地离线资源配置对象，单次调用最大支持注入30个资源，单个资源最大支持10Mb。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**适用版本：** 22+ |

## isActiveWebEngineEvergreen

```TypeScript
static isActiveWebEngineEvergreen(): boolean
```

判断当前系统是否正在使用常青内核，即系统的最新内核。

**起始版本：** 23

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

查询广告过滤功能是否开启。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-isAdsBlockEnabled(): boolean--><!--Device-WebviewController-isAdsBlockEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true代表广告过滤功能已开启，返回false代表广告过滤功能关闭。 <br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## isAdsBlockEnabledForCurPage

```TypeScript
isAdsBlockEnabledForCurPage(): boolean
```

查询当前网页是否开启广告过滤功能。 当Web组件使能广告过滤功能后，默认所有页面都是开启广告过滤的，支持通过 [addAdsBlockDisallowedList](arkts-arkweb-webview-adsblockmanager-c.md#addadsblockdisallowedlist)指定域名禁用广告过滤。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-isAdsBlockEnabledForCurPage(): boolean--><!--Device-WebviewController-isAdsBlockEnabledForCurPage(): boolean-End-->

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

查询Web内核的自动预连接状态。 如果没有使用[setAutoPreconnect](#setautopreconnect)设置Web内核自动预连接的状态，则默认启用自动预连接，返回true。

**起始版本：** 21

<!--Device-WebviewController-static isAutoPreconnectEnabled(): boolean--><!--Device-WebviewController-static isAutoPreconnectEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回Web内核是否启用了自动预连接。true表示已启用；false表示已禁用。 |

## isIncognitoMode

```TypeScript
isIncognitoMode(): boolean
```

查询当前是否是隐私模式的Webview。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-isIncognitoMode(): boolean--><!--Device-WebviewController-isIncognitoMode(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否是隐私模式的Webview。 <br>true表示是隐私模式，false表示不是隐私模式。 <br>默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## isIntelligentTrackingPreventionEnabled

```TypeScript
isIntelligentTrackingPreventionEnabled(): boolean
```

获取Web组件是否启用了智能防跟踪功能。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-isIntelligentTrackingPreventionEnabled(): boolean--><!--Device-WebviewController-isIntelligentTrackingPreventionEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Web组件是否启用了智能防跟踪功能。 <br>true表示启用了智能防跟踪功能，false表示未启用智能防跟踪功能。 <br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## isPrivateNetworkAccessEnabled

```TypeScript
static isPrivateNetworkAccessEnabled(): boolean
```

获取Web组件是否启用了私有网络访问检查功能。 > **说明：** > > 当前私有网络访问检查功能主要针对Web Worker场景生效。

**起始版本：** 20

<!--Device-WebviewController-static isPrivateNetworkAccessEnabled(): boolean--><!--Device-WebviewController-static isPrivateNetworkAccessEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回Web组件是否启用了私有网络访问检查功能。true表示已启用；false表示已禁用。 |

## isSafeBrowsingEnabled

```TypeScript
isSafeBrowsingEnabled(): boolean
```

获取当前网页是否启用了检查网站安全风险。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-isSafeBrowsingEnabled(): boolean--><!--Device-WebviewController-isSafeBrowsingEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前网页是否启用了检查网站安全风险的功能。 <br>true表示启用了检查网站安全风险的功能，false表示未启用检查网站安全风险的功能。 <br>默认值：false。 |

## loadData

```TypeScript
loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void
```

加载指定的数据。 baseUrl与historyUrl同时为空的情况下： encoding如果为非base64（包括空值），则假定数据对安全URL字符范围内的八位字节使用ASCII编码，对该范围外的八位字节使用URL的标准%xx十六进制编码。 data数据必须使用base64编码或将内容中的任何#字符编码为%23。否则#将被视为内容的结尾而剩余的文本将被用作文档片段标识符。 > **说明：** > > - 若加载本地图片，可以给baseUrl或historyUrl任一参数赋值空格，详情请参考示例代码。 > > - 加载本地图片场景，baseUrl和historyUrl不能同时为空，否则图片无法成功加载。 > > - 若html中的富文本中带有注入#等特殊字符，建议将baseUrl和historyUrl两个参数的值设置为"空格"。 > > - 加载文字场景，需主动设置`&lt;meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8"&gt;`避免文本字体大小不 > 一致。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void--><!--Device-WebviewController-loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 按照"base64"或者"URL"编码后的一段字符串。 |
| mimeType | string | 是 | 媒体类型（MIME）。 |
| encoding | string | 是 | 编码类型，具体为"base64"或者"URL"编码。 |
| baseUrl | string | 否 | 指定的一个URL路径（"http"/"https"/"data"协议），并由Web组件赋值给`window.origin`。当加载大量html文件时，需设置为" data"。 <br>传入undefined或null会抛出异常错误码401。 |
| historyUrl | string | 否 | 用作历史记录所使用的URL。非空时，历史记录以此URL进行管理。当baseUrl为空时，此属性无效。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2048.<br>**适用版本：** 9 - 10 |

## loadUrl

```TypeScript
loadUrl(url: string | Resource, headers?: Array<WebHeader>): void
```

加载指定的URL。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-loadUrl(url: string | Resource, headers?: Array<WebHeader>): void--><!--Device-WebviewController-loadUrl(url: string | Resource, headers?: Array<WebHeader>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 需要加载的URL。 |
| headers | Array&lt;WebHeader&gt; | 否 | URL的附加HTTP请求头。 <br>默认值： []。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## off('controllerAttachStateChange')

```TypeScript
off(type: 'controllerAttachStateChange', callback?: Callback<ControllerAttachState>): void
```

取消WebViewController绑定状态事件的注册，取消后将不再接收Callback通知。

**起始版本：** 20

<!--Device-WebviewController-off(type: 'controllerAttachStateChange', callback?: Callback<ControllerAttachState>): void--><!--Device-WebviewController-off(type: 'controllerAttachStateChange', callback?: Callback<ControllerAttachState>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controllerAttachStateChange' | 是 | 表示注册WebViewController绑定状态事件，固定为"controllerAttachStateChange"。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md)&gt; | 否 | WebViewController绑定状态发生改变时的回调函数，默认情况下不填写回调函数。如果填写了Callback， 将仅取消注册该特定的回调。如果不填写Callback，将取消注册所有回调。 <br>传入null或undefined时会抛出异常错误码401。 |

## onActive

```TypeScript
onActive(): void
```

调用此接口通知Web组件进入前台激活状态。 激活状态是应用与用户互动的状态。应用会保持这种状态，直到发生某些事件（例如收到来电或设备屏幕关闭）时将焦点从应用移开。 若页面此前处于未激活状态，H5页面中通过document.addEventListener('visibilitychange',...)注册的事件监听器将被触发，document.visibilityState 从" hidden"变为"visible"。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-onActive(): void--><!--Device-WebviewController-onActive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## onCreateNativeMediaPlayer

```TypeScript
onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void
```

注册回调函数，使用enableNativeMediaPlayer开启应用接管网页媒体播放功能后，当网页中有播放媒体时，触发注册的回调函 数。 如果应用接管网页媒体播放功能未开启，则注册的回调函数不会被触发。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void--><!--Device-WebviewController-onCreateNativeMediaPlayer(callback: CreateNativeMediaPlayerCallback): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md) | 是 | 接管网页媒体播放的回调函数。 |

## onInactive

```TypeScript
onInactive(): void
```

调用此接口通知Web组件进入未激活状态。开发者可以在此回调中实现应用失去焦点时应表现的恰当行为。 此状态下会尽可能的暂停任何可以安全暂停的内容，例如动画和地理位置。但不会暂停JavaScript，要全局暂停JavaScript，请使用 [pauseAllTimers](#pausealltimers)。要重新激活Web组件，请调用 [onActive](#onactive)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-onInactive(): void--><!--Device-WebviewController-onInactive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## on('controllerAttachStateChange')

```TypeScript
on(type: 'controllerAttachStateChange', callback: Callback<ControllerAttachState>): void
```

注册WebViewController绑定状态事件，通过Callback方式获取WebViewController绑定状态的变化通知。

**起始版本：** 20

<!--Device-WebviewController-on(type: 'controllerAttachStateChange', callback: Callback<ControllerAttachState>): void--><!--Device-WebviewController-on(type: 'controllerAttachStateChange', callback: Callback<ControllerAttachState>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controllerAttachStateChange' | 是 | 表示注册WebViewController绑定状态事件，固定为"controllerAttachStateChange"。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md)&gt; | 是 | WebViewController绑定状态改变时的回调函数。 |

## pageDown

```TypeScript
pageDown(bottom: boolean): void
```

将Webview的内容向下滚动半个视框大小或者跳转到页面最底部，通过bottom入参控制。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-pageDown(bottom: boolean): void--><!--Device-WebviewController-pageDown(bottom: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bottom | boolean | 是 | 是否跳转到页面最底部。 <br>false时表示将页面内容向下滚动半个视框大小，true表示跳转到页面最底部。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pageUp

```TypeScript
pageUp(top: boolean): void
```

将Webview的内容向上滚动半个视框大小或者跳转到页面最顶部，通过top入参控制。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-pageUp(top: boolean): void--><!--Device-WebviewController-pageUp(top: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| top | boolean | 是 | 是否跳转到页面最顶部。 <br>false表示将页面内容向上滚动半个视框大小，true表示跳转到页面最顶部。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pauseAllMedia

```TypeScript
pauseAllMedia(): void
```

控制网页所有音视频暂停。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-pauseAllMedia(): void--><!--Device-WebviewController-pauseAllMedia(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pauseAllTimers

```TypeScript
static pauseAllTimers(): void
```

暂停所有WebView的定时器，定时器暂停期间，网页中的setInterval、setTimeout等定时操作将被挂起。建议在应用进入后台等场景暂停，前台时恢复，以节省资源，可以与 [resumeAllTimers](#resumealltimers)()成对使用，避免定时器状态混乱。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static pauseAllTimers(): void--><!--Device-WebviewController-static pauseAllTimers(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## pauseMicrophone

```TypeScript
pauseMicrophone(): void
```

暂停当前网页麦克风捕获。 > **说明：** > > 与 resumeMicrophone 和 stopMicrophone 的区别： > > pauseMicrophone 仅暂停麦克风捕获，可通过 resumeMicrophone 恢复；stopMicrophone 会停止捕获并释放资源。

**起始版本：** 23

<!--Device-WebviewController-pauseMicrophone(): void--><!--Device-WebviewController-pauseMicrophone(): void-End-->

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-postMessage(name: string, ports: Array<WebMessagePort>, uri: string): void--><!--Device-WebviewController-postMessage(name: string, ports: Array<WebMessagePort>, uri: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要发送的消息名称。 |
| ports | Array&lt;[WebMessagePort](arkts-arkweb-webview-webmessageport-i.md)&gt; | 是 | 要发送的消息端口。 |
| uri | string | 是 | 接收该消息的URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## postUrl

```TypeScript
postUrl(url: string, postData: ArrayBuffer): void
```

使用"POST"方法加载带有postData的URL。如果URL不是网络URL，则会使用[loadUrl](#loadurl)方法加载URL，忽略postData参 数。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-postUrl(url: string, postData: ArrayBuffer): void--><!--Device-WebviewController-postUrl(url: string, postData: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 需要加载的URL。 |
| postData | ArrayBuffer | 是 | 使用"POST"方法传递数据。 该请求必须采用"application/x-www-form-urlencoded"编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid. |

## precompileJavaScript

```TypeScript
precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<number>
```

预编译JavaScript生成字节码缓存或根据提供的参数更新已有的字节码缓存。 接口通过提供的文件信息、E-Tag响应头和Last-Modified响应头判断是否需要更新已有的字节码缓存。

**起始版本：** 12

<!--Device-WebviewController-precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<number>--><!--Device-WebviewController-precompileJavaScript(url: string, script: string | Uint8Array, cacheOptions: CacheOptions): Promise<number>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 本地JavaScript文件对应的网络地址，即业务网页请求该文件的服务器版本时使用的网络地址。网络地址仅支持http或https协议，长度不超过2048。如果该网络地址对应的缓存 失效，则业务网页将通过网络请求对应的资源。 |
| script | string \| Uint8Array | 是 | 本地JavaScript的文本内容。内容不能为空。 |
| cacheOptions | [CacheOptions](arkts-arkweb-webview-cacheoptions-i.md) | 是 | 用于控制字节码缓存更新。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 生成字节码缓存的错误码，0表示无错误，-1表示内部错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void
```

在预测到将要加载的页面之前调用，可提前下载页面所需的资源（包括：主资源和子资源），但不会执行网页JavaScript代码或呈现网页，以加快页面加载速度。 > **说明：** > > - 下载的页面资源会缓存五分钟左右，超过这段时间Web组件会自动释放。 > > - prefetchPage对302重定向页面同样正常预取。 > > - 先执行prefetchPage再加载页面时，已预取的资源将直接从缓存中加载。 > > - 连续prefetchPage多个URL只有第一个生效。 > > - prefetchPage有时间限制，500ms内不能多次预取。 > > - prefetchPage会缓存所有资源，但具有Cache-Control: no-store标头的资源除外。如果存在Vary响应标头、Cache-Control: no-store标头，或者下载的页面资源已超过五分钟， > 则在使用之前会重新验证资源。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void--><!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 预加载的URL。 |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | URL的附加HTTP请求头。 <br>默认值： [] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**适用版本：** 22+ |

## prefetchPage

```TypeScript
prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void
```

在预测到将要加载的页面之前调用，可提前下载页面所需的资源（包括：主资源和子资源），但不会执行网页JavaScript代码或呈现网页，以加快页面加载速度。 > **说明：** > > - 下载的页面资源会缓存五分钟左右，超过这段时间Web组件会自动释放。 > > - prefetchPage对302重定向页面同样正常预取。 > > - 先执行prefetchPage再加载页面时，已预取的资源将直接从缓存中加载。 > > - prefetchPage会缓存所有资源，但具有Cache-Control: no-store标头的资源除外。如果存在Vary响应标头、Cache-Control: no-store标头，或者下载的页面资源已超过五分钟， > 则在使用之前会重新验证资源。

**起始版本：** 21

<!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void--><!--Device-WebviewController-prefetchPage(url: string, additionalHeaders?: Array<WebHeader>, prefetchOptions?: PrefetchOptions): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 预加载的URL。 |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | URL的附加HTTP请求头。 <br>默认值： [] |
| prefetchOptions | [PrefetchOptions](arkts-arkweb-webview-prefetchoptions-c.md) | 否 | 用来自定义预取行为的相关选项。 <br>两次预取间的最小时间间隔为500ms，默认不忽略响应头中的Cache-Control: no-store。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**适用版本：** 22+ |

## prefetchResource

```TypeScript
static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,
                            cacheValidTime?: number): void
```

根据指定的请求信息和附加的HTTP请求头去预获取资源请求，存入内存缓存，并指定其缓存key和有效期，以加快加载速度。目前仅支持Content-Type为application/x-www-form-urlencoded的 POST请求。最多可以预获取6个POST请求。如果要预获取第7个，请通过 [clearPrefetchedResource](#clearprefetchedresource)清除不需要的POST请求缓存，否则会自动清除最早预获取的 POST缓存。如果要使用预获取的资源缓存，开发者需要在正式发起的POST请求的请求头中增加键值“ArkWebPostCacheKey”，其内容为对应缓存的cacheKey。 内存缓存中的资源由内核自动管理。当注入的资源过多，导致内存压力过大时，内核会自动释放未使用的资源，但仍应避免向内存缓存中注入大量资源。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,                            cacheValidTime?: number): void--><!--Device-WebviewController-static prefetchResource(request: RequestInfo, additionalHeaders?: Array<WebHeader>, cacheKey?: string,                            cacheValidTime?: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | RequestInfo | 是 | 预获取请求的信息。 |
| additionalHeaders | Array&lt;WebHeader&gt; | 否 | 预获取请求的附加HTTP请求头。 <br>传入undefined或null会抛出异常错误码401。 |
| cacheKey | string | 否 | 用于后续查询预获取资源缓存的key。仅支持字母和数字，未传入或传入空则取默认值url作为key。 <br>传入undefined或null会抛出异常错误码401。 |
| cacheValidTime | number | 否 | 预获取资源缓存的有效期。 <br>取值范围：(0, 2147483647]。 <br>默认值：300s。 <br>单位：s。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**适用版本：** 22+ |

## prepareForPageLoad

```TypeScript
static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void
```

预连接URL，在加载URL之前调用此API，对URL只进行DNS解析，socket建链操作，并不获取主资源子资源。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void--><!--Device-WebviewController-static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 预连接的URL。 |
| preconnectable | boolean | 是 | 是否进行预连接。如果preconnectable为true，则对URL进行DNS解析，socket建链预连接；如果preconnectable为 false，则不做任何预连接操作。 |
| numSockets | number | 是 | 要预连接的socket数。socket数目连接需要大于0，最多允许6个连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**适用版本：** 22+ |
| [17100013](../errorcode-webview.md#17100013-预连接时输入socket数目无效) | The number of preconnect sockets is invalid. |

## refresh

```TypeScript
refresh(): void
```

调用此接口通知Web组件刷新网页。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-refresh(): void--><!--Device-WebviewController-refresh(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## refresh

```TypeScript
refresh(ignoreCache: boolean): void
```

通知Web组件刷新网页，可以选择是否忽略缓存刷新。

**起始版本：** 24

<!--Device-WebviewController-refresh(ignoreCache: boolean): void--><!--Device-WebviewController-refresh(ignoreCache: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ignoreCache | boolean | 是 | Web组件刷新网页，选择是否忽略缓存刷新。 <br>true表示忽略缓存刷新，false表示不忽略缓存刷新。<br/>**说明：** <br>传入undefined或null时为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,
        asyncMethodList?: Array<string>, permission?: string): void
```

registerJavaScriptProxy提供了应用与Web组件加载的网页之间强大的交互能力。注入JavaScript对象到window对象中，并在window对象中调用该对象的方法。 示例请参考[前端页面调用应用侧函数](../../../web/web-in-page-app-function-invoking.md)。 > **说明：** > > - registerJavaScriptProxy需要和deleteJavaScriptRegister接口配合使用，防止内存泄漏。 > > - 请尽可能只在可信的URL及安全通信HTTPS场景下进行registerJavaScriptProxy注册。在非可信的Web组件中注入JavaScript对象，可能会导致应用被恶意攻击。 > > - 在注册registerJavaScriptProxy后，应用会将JavaScript对象暴露给所有的页面frames。 > > - 同一方法在同步与异步列表中重复注册，将默认异步调用。 > > - 同步函数列表和异步函数列表不可同时为空，否则此次调用接口注册失败。 > > - 异步的作用在于：H5线程将异步JavaScript任务提交给ETS主线程后，无需等待任务执行完成并返回结果，H5线程即可继续执行后续任务。这在执行耗时较长的JavaScript任务或ETS线程较为拥堵的情况下，可以有效 > 减少H5线程因JavaScript任务而被阻塞的情况。然而，异步JavaScript任务无法返回值，且任务执行的顺序无法保证，因此需要根据具体情境判断是否使用同步或异步方式。 > > - 注入的对象在页面下一次（重新）加载前不会出现在JavaScript中。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,        asyncMethodList?: Array<string>, permission?: string): void--><!--Device-WebviewController-registerJavaScriptProxy(jsObject: object, name: string, methodList: Array<string>,        asyncMethodList?: Array<string>, permission?: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jsObject | object | 是 | 参与注册的应用侧JavaScript对象。可以单独声明方法和属性，但无法同时进行注册与使用。对象只包含属性时，H5可以访问对象中的属性。对象只包含方法时，H5可以访问对 象中的方法。 <br>1. 方法的参数和返回类型可以为string，number，boolean。 <br>2. 方法的参数和返回类型支持Dictionary，Array，最多嵌套10层，每层1w个数据。 <br>3. 方法的参数和返回类型支持Object，需要在Object里添加属性methodNameListForJsProxy:[fun1, fun2]，fun1和fun2为可被调用的方法。 <br>4. 方法的参数支持Function，Promise，它们的Callback不能有返回值。 <br>5. 方法的返回类型支持Promise，Promise的Callback不能有返回值。 |
| name | string | 是 | 注册对象的名称，与window中调用的对象名一致。注册后window对象可以通过此名字访问应用侧JavaScript对象。 |
| methodList | Array&lt;string&gt; | 是 | 参与注册的应用侧JavaScript对象的同步方法。 |
| asyncMethodList | Array&lt;string&gt; | 否 | 参与注册的应用侧JavaScript对象的异步方法，默认为空。异步方法无法获取返回值。 <br>传入undefined或null会抛出异常错误码401。<br>**起始版本：** 12 |
| permission | string | 否 | JSON字符串，默认为空，通过该字符串配置JSBridge的权限管控，可以定义object和method级别的URL白名单。 <br>1. scheme（协议）和host（域名）参数不可为空，且host不支持通配符，只能填写完整的host。 <br>2. 可以仅配置object级别的白名单，该白名单对所有JSBridge方法生效。 <br>3. 若JSBridge方法A设置了method级别的白名单，那么方法A最终的白名单是object级别白名单与method级别白名单的交集。 <br>传入undefined或null会抛出异常错误码401。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## removeAllCache

```TypeScript
static removeAllCache(clearRom: boolean): void
```

清除应用内所有Webview(含隐私模式)产生的资源缓存。 > **说明：** > > 可以通过在data/app/el2/100/base/\&lt;applicationPackageName\&gt;/cache/web/目录下查看Webview的缓存。

**起始版本：** 18

<!--Device-WebviewController-static removeAllCache(clearRom: boolean): void--><!--Device-WebviewController-static removeAllCache(clearRom: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearRom | boolean | 是 | 设置为true时同时清除ROM和RAM中的缓存，设置为false时只清除RAM中的缓存。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## removeCache

```TypeScript
removeCache(clearRom: boolean): void
```

清除与当前WebView上下文相关的资源缓存。 > **说明：** > > 可以通过在data/storage/el2/base/cache/web/Cache目录下查看Webview的缓存。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-removeCache(clearRom: boolean): void--><!--Device-WebviewController-removeCache(clearRom: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearRom | boolean | 是 | 设置为true时同时清除ROM和RAM中的缓存，设置为false时只清除RAM中的缓存。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## removeIntelligentTrackingPreventionBypassingList

```TypeScript
static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void
```

删除通过addIntelligentTrackingPreventionBypassingList接口添加的部分域名列表。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void--><!--Device-WebviewController-static removeIntelligentTrackingPreventionBypassingList(hostList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostList | Array&lt;string&gt; | 是 | 绕过智能防跟踪功能的域名列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## requestFocus

```TypeScript
requestFocus(): void
```

使指定组件获取焦点。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-requestFocus(): void--><!--Device-WebviewController-requestFocus(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## restoreWebState

```TypeScript
restoreWebState(state: Uint8Array) : void
```

当前WebView从序列化数据中恢复页面状态历史记录。 如果state过大，可能会导致异常。建议state大于512k时，放弃恢复页面状态历史记录。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-restoreWebState(state: Uint8Array) : void--><!--Device-WebviewController-restoreWebState(state: Uint8Array) : void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | Uint8Array | 是 | 页面状态历史记录序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## resumeAllMedia

```TypeScript
resumeAllMedia(): void
```

控制网页被pauseAllMedia接口暂停的音视频继续播放。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-resumeAllMedia(): void--><!--Device-WebviewController-resumeAllMedia(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## resumeAllTimers

```TypeScript
static resumeAllTimers(): void
```

恢复从pauseAllTimers()接口中被暂停的所有的定时器。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static resumeAllTimers(): void--><!--Device-WebviewController-static resumeAllTimers(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## resumeMicrophone

```TypeScript
resumeMicrophone(): void
```

恢复当前网页麦克风捕获。使用麦克风功能前请在module.json5中添加权限: ohos.permission.MICROPHONE，具体权限的添加方法请参考 [在配置文件中声明权限](../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 23

<!--Device-WebviewController-resumeMicrophone(): void--><!--Device-WebviewController-resumeMicrophone(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## runJavaScript

```TypeScript
runJavaScript(script: string): Promise<string>
```

在当前显示页面的上下文中异步执行JavaScript脚本，脚本执行的结果将通过Promise方式返回。此方法必须在用户界面（UI）线程上使用 ，并且回调也将在用户界面（UI）线程上调用。 > **说明：** > > - 跨导航操作（如loadUrl）时，JavaScript状态 将不再保留，例如，调用loadUrl前定义的全局变量和函数在加载的页面中将不存在。 > > - 建议应用程序使用registerJavaScriptProxy来确保JavaScript状态能够在页面导航间保持。 > > - 目前不支持传递对象，支持传递结构体。 > > - 执行异步方法无法获取返回值，需要根据具体情境判断是否使用同步或异步方式。 > > - 前端页面传到应用侧的string数据类型会被视为JSON格式的数据，需要调用JSON.parse反序列化。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-runJavaScript(script: string): Promise<string>--><!--Device-WebviewController-runJavaScript(script: string): Promise<string>-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScript

```TypeScript
runJavaScript(script: string, callback: AsyncCallback<string>): void
```

在当前显示页面的上下文中异步执行JavaScript脚本，脚本执行的结果将通过异步回调方式返回。此方法必须在用户界面（UI）线程上使用 ，并且回调也将在用户界面（UI）线程上调用。 > **说明：** > > - 跨导航操作（如loadUrl）时，JavaScript状态将不再保留。例如，调用loadUrl前定义的全局变量和函数在加载的页面中将不存在。 > > - 建议应用程序使用registerJavaScriptProxy来确保JavaScript状态能够在页面导航间保持。 > > - 目前不支持传递对象，支持传递结构体。 > > - 执行异步方法无法获取返回值，需要根据具体情境判断是否使用同步或异步方式。 > > - 前端页面传到应用侧的string数据类型会被视为JSON格式的数据，需要调用JSON.parse反序列化。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-runJavaScript(script: string, callback: AsyncCallback<string>): void--><!--Device-WebviewController-runJavaScript(script: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string | 是 | JavaScript脚本。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调执行JavaScript脚本结果。JavaScript脚本若执行失败或无返回值时，返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Calling a JS method that returns an empty ArrayBuffer via runJavaScript. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>
```

异步执行JavaScript脚本，并通过Promise方式返回脚本执行的结果。runJavaScriptExt需要在loadUrl完成后，比如onPageEnd中 调用。 > **说明：** > > - 前端页面传到应用侧的string数据类型会被视为JSON格式的数据，需要调用JSON.parse反序列化。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>--><!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer): Promise<JsMessageExt>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string \| ArrayBuffer | 是 | JavaScript脚本。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[JsMessageExt](arkts-arkweb-webview-jsmessageext-c.md)&gt; | Promise实例，返回脚本执行的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## runJavaScriptExt

```TypeScript
runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void
```

异步执行JavaScript脚本，并通过回调方式返回脚本执行的结果。runJavaScriptExt需要在loadUrl完成后，比如onPageEnd中调用。 > **说明：** > > - 前端页面传到应用侧的string数据类型会被视为JSON格式的数据，需要调用JSON.parse反序列化。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void--><!--Device-WebviewController-runJavaScriptExt(script: string | ArrayBuffer, callback: AsyncCallback<JsMessageExt>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| script | string \| ArrayBuffer | 是 | JavaScript脚本。<br>**起始版本：** 12 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[JsMessageExt](arkts-arkweb-webview-jsmessageext-c.md)&gt; | 是 | 回调执行JavaScript脚本结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## scrollBy

```TypeScript
scrollBy(deltaX: number, deltaY: number, duration?: number): void
```

在指定时间内将页面滚动指定的偏移量。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-scrollBy(deltaX: number, deltaY: number, duration?: number): void--><!--Device-WebviewController-scrollBy(deltaX: number, deltaY: number, duration?: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deltaX | number | 是 | 水平偏移量，其中水平向右为正方向。 <br>单位：vp。 |
| deltaY | number | 是 | 垂直偏移量，其中垂直向下为正方向。 <br>单位：vp。 |
| duration | number | 否 | 滚动动画时间。 <br>单位：ms。 <br>不传入为无动画，当传入数值为负数或传入0时，按照不传入处理。 <br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 14 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## scrollByWithResult

```TypeScript
scrollByWithResult(deltaX: number, deltaY: number): boolean
```

将页面滚动指定的偏移量，返回值表示此次滚动是否执行成功。

**起始版本：** 12

<!--Device-WebviewController-scrollByWithResult(deltaX: number, deltaY: number): boolean--><!--Device-WebviewController-scrollByWithResult(deltaX: number, deltaY: number): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deltaX | number | 是 | 水平偏移量，其中水平向右为正方向。 <br>单位：vp。 |
| deltaY | number | 是 | 垂直偏移量，其中垂直向下为正方向。 <br>单位：vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示当前网页可以滑动，false表示当前网页不可以滑动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## scrollTo

```TypeScript
scrollTo(x: number, y: number, duration?: number): void
```

在指定时间内，将页面滚动到指定的绝对位置。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-scrollTo(x: number, y: number, duration?: number): void--><!--Device-WebviewController-scrollTo(x: number, y: number, duration?: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 绝对位置的水平坐标，当传入数值为负数时，按照传入0处理。 <br>单位：vp。 |
| y | number | 是 | 绝对位置的垂直坐标，当传入数值为负数时，按照传入0处理。 <br>单位：vp。 |
| duration | number | 否 | 滚动动画时间。 <br>单位：ms。 <br>不传入为无动画，当传入数值为负数或传入0时，按照不传入处理。 <br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 14 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## searchAllAsync

```TypeScript
searchAllAsync(searchString: string): void
```

异步查找网页中所有匹配关键字'searchString'的内容并高亮，结果通过onSearchResultReceive异步返回。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-searchAllAsync(searchString: string): void--><!--Device-WebviewController-searchAllAsync(searchString: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchString | string | 是 | 查找的关键字。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## searchNext

```TypeScript
searchNext(forward: boolean): void
```

滚动到下一个匹配的查找结果并高亮。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-searchNext(forward: boolean): void--><!--Device-WebviewController-searchNext(forward: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forward | boolean | 是 | 从前向后或者逆向查找方式。 <br>true表示从前向后查找，false表示从后向前查找。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## serializeWebState

```TypeScript
serializeWebState() : Uint8Array
```

将当前WebView的页面状态历史记录信息序列化。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-serializeWebState() : Uint8Array--><!--Device-WebviewController-serializeWebState() : Uint8Array-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 当前WebView的页面状态历史记录序列化后的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setActiveWebEngineVersion

```TypeScript
static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void
```

设置ArkWeb内核版本。若系统不支持指定版本，则设置无效，使用系统默认内核（可参考[约束与限制](../../../web/web-component-overview.md#约束与限制)）。该接口为全局静态API，须在调 用initializeWebEngine前执行，若已加载任何Web组件，则该设置无效。典型使用场景：使用特定内核版本的特性或兼容性需求时，可切换到对应内核版本。 > **说明：** > > - setActiveWebEngineVersion不支持在异步线程中调用。 > > - setActiveWebEngineVersion全局生效，在整个APP生命周期中调用一次即可，不需要重复调用。

**起始版本：** 20

<!--Device-WebviewController-static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void--><!--Device-WebviewController-static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| engineVersion | [ArkWebEngineVersion](arkts-arkweb-webview-arkwebengineversion-e.md) | 是 | ArkWeb内核版本。 |

## setAppCustomUserAgent

```TypeScript
static setAppCustomUserAgent(userAgent: string) : void
```

设置应用级自定义用户代理，会覆盖系统的用户代理，应用内所有Web组件生效。 当需要设置应用级自定义用户代理时，建议在Web组件创建前调用setAppCustomUserAgent方法设置User-Agent，再创建指定src的Web组件或通过 [loadUrl](#loadurl)加载具体页面。 默认User-Agent定义与使用场景，及相关User-Agent接口定义优先级请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)。

**起始版本：** 20

<!--Device-WebviewController-static setAppCustomUserAgent(userAgent: string) : void--><!--Device-WebviewController-static setAppCustomUserAgent(userAgent: string) : void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | 用户自定义代理信息。建议先使用 [getDefaultUserAgent](#getdefaultuseragent)获取当前默认用户代理，在此基础上追加自定义用户代理信息。 |

## setAudioMuted

```TypeScript
setAudioMuted(mute: boolean): void
```

设置网页静音。典型使用场景包括：应用需要控制网页音量（如提供静音开关）、后台播放时需要静音等。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setAudioMuted(mute: boolean): void--><!--Device-WebviewController-setAudioMuted(mute: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 表示是否将网页设置为静音状态。 <br>true表示将网页设置为静音状态，false表示将网页取消静音状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setAutoPreconnect

```TypeScript
static setAutoPreconnect(enabled: boolean): void
```

设置Web内核的自动预连接状态。若未设置，默认启用自动预连接。 需要在[initializeWebEngine()](#initializewebengine)初始化内核或者创建Web组件之前调用。若已加载任何Web组件，则该设 置无效。

**起始版本：** 21

<!--Device-WebviewController-static setAutoPreconnect(enabled: boolean): void--><!--Device-WebviewController-static setAutoPreconnect(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否启用Web内核自动预连接的开关。true表示启用，false表示禁用。 |

## setBackForwardCacheOptions

```TypeScript
setBackForwardCacheOptions(options: BackForwardCacheOptions): void
```

可以设置Web组件中前进后退缓存的相关选项。

**起始版本：** 12

<!--Device-WebviewController-setBackForwardCacheOptions(options: BackForwardCacheOptions): void--><!--Device-WebviewController-setBackForwardCacheOptions(options: BackForwardCacheOptions): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [BackForwardCacheOptions](arkts-arkweb-webview-backforwardcacheoptions-c.md) | 是 | 用来控制Web组件前进后退缓存相关选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setBlanklessLoadingCacheCapacity

```TypeScript
static setBlanklessLoadingCacheCapacity(capacity: number) : number
```

设置无白屏加载方案的持久化缓存容量，返回实际生效值。当接口没有显式调用时，默认缓存容量为30MB。当实际缓存超过容量时，将采用淘汰不常用的过渡帧的方式清理。

**起始版本：** 20

<!--Device-WebviewController-static setBlanklessLoadingCacheCapacity(capacity: number) : number--><!--Device-WebviewController-static setBlanklessLoadingCacheCapacity(capacity: number) : number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 是 | 设置持久化缓存设置，单位MB，最大设置不超过100MB。 <br>合法取值范围：[0, 100]，当设置为0时，无缓存空间，则功能全局不开启。 <br>非法值设置行为：小于0时生效值为0，大于100时生效值为100。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际生效的容量值，范围0~100。 <br>小于0时生效值为0，大于100时生效值为100。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) |  |

## setBlanklessLoadingWithKey

```TypeScript
setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode
```

设置无白屏加载是否启用，本接口必须与[getBlanklessInfoWithKey](#getblanklessinfowithkey)接口配套使用。 > **说明：** > > - 需在触发页面加载的接口之后调用，其他约束同[getBlanklessInfoWithKey](#getblanklessinfowithkey)。 > > - 页面加载必须在调用本接口的组件中进行。 > > - 当相似度较低时，系统将判定为跳变过大，启用插帧会失败。 > > - 请在module.json5中添加权限: ohos.permission.INTERNET和ohos.permission.GET_NETWORK_INFO， > 具体权限的添加方法请参考[在配置文件中声明权限](../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 20

<!--Device-WebviewController-setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode--><!--Device-WebviewController-setBlanklessLoadingWithKey(key: string, is_start: boolean) : WebBlanklessErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 唯一标识本页面的key值。必须与getBlanklessInfoWithKey接口的key值相同。 <br>合法取值范围：非空，长度不超过2048个字符。 <br>非法值设置行为：返回错误码WebBlanklessErrorCode，方案不生效。 |
| is_start | boolean | 是 | 是否启用开始插帧。true：启用，false：不启用。 <br>传入undefined或null时为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md) | 返回接口调用是否成功，具体见 [WebBlanklessErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) |  |

## setBlanklessLoadingWithParams

```TypeScript
setBlanklessLoadingWithParams(key: string,
      param: BlanklessLoadingParam) : WebBlanklessErrorCode
```

设置白屏插帧的配置参数，本接口必须与[getBlanklessInfoWithKey](#getblanklessinfowithkey)接口配套使用。相比于 [setBlanklessLoadingWithKey](#setblanklessloadingwithkey)，本接口支持白屏插帧更多的参数设置，包括插帧持续时 间，缓存数据有效时间，插帧完成后的自定义回调。 > **说明：** > > - 需在触发页面加载的接口之后调用，其他约束同[getBlanklessInfoWithKey](#getblanklessinfowithkey)。 > > - 页面加载必须在调用本接口的组件中进行。 > > - 当相似度较低时，系统将判定为跳变过大，启用插帧会失败。 > > - 请在module.json5中添加权限: ohos.permission.INTERNET和ohos.permission.GET_NETWORK_INFO，具体权限的添加方法请参考 > [在配置文件中声明权限](../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-setBlanklessLoadingWithParams(key: string,      param: BlanklessLoadingParam) : WebBlanklessErrorCode--><!--Device-WebviewController-setBlanklessLoadingWithParams(key: string,      param: BlanklessLoadingParam) : WebBlanklessErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 唯一标识本页面的key值。必须与getBlanklessInfoWithKey接口的key值相同。 <br>合法取值范围：非空，长度不超过2048个字符。 <br>非法值设置行为：返回错误码WebBlanklessErrorCode，方案不生效。 |
| param | [BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md) | 是 | 白屏插帧加载的各项参数设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md) | 返回接口调用结果。 |

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static setConnectionTimeout(timeout: number): void--><!--Device-WebviewController-static setConnectionTimeout(timeout: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | socket连接超时时间，单位：s，必须为大于0的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3. Parameter verification failed. |

## setCustomUserAgent

```TypeScript
setCustomUserAgent(userAgent: string): void
```

设置自定义用户代理，会覆盖系统的用户代理。 > **说明：** > > - 当Web组件src设置了URL时，建议在onControllerAttached回调中设置User-Agent。不要在 > onLoadIntercept回调中设置，否则可能会设置失败或导致不可预期的后果。 > > - 若未在onControllerAttached回调中设置User-Agent，再调用setCustomUserAgent方法时，可能会出现加载的页面与实际设置User-Agent不符的异常现象。 > > - 当Web组件src未设置URL时，建议先调用setCustomUserAgent方法设置User-Agent，再通过loadUrl加载具体页面。 > > - 默认User-Agent定义与使用场景请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setCustomUserAgent(userAgent: string): void--><!--Device-WebviewController-setCustomUserAgent(userAgent: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | 用户自定义代理信息。建议先使用[getUserAgent](#getuseragent)获取当前默认用户 代理，在此基础上追加自定义用户代理信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setDownloadDelegate

```TypeScript
setDownloadDelegate(delegate: WebDownloadDelegate): void
```

为当前的Web组件设置一个WebDownloadDelegate，该delegate用来接收页面内触发的下载进度的委托。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setDownloadDelegate(delegate: WebDownloadDelegate): void--><!--Device-WebviewController-setDownloadDelegate(delegate: WebDownloadDelegate): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | [WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md) | 是 | 用来接收下载进度的委托。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setErrorPageEnabled

```TypeScript
setErrorPageEnabled(enable: boolean): void
```

设置是否启用默认错误页。 在当前接口设置为true时如果页面加载发生错误将触发onOverrideErrorPage回调，可在该回调接口中设置自定义的错误展示页面。

**起始版本：** 20

<!--Device-WebviewController-setErrorPageEnabled(enable: boolean): void--><!--Device-WebviewController-setErrorPageEnabled(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示是否启用默认错误页。true表示启用，false表示不启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setErrorPageEnabled

```TypeScript
setErrorPageEnabled(enable: boolean, includeSubframe: boolean): void
```

设置是否启用mainframe错误页功能，并可控制是否同时启用subframe错误页功能。 当enable设置为true时，mainframe加载发生错误将展示错误页：若设置了onOverrideErrorPage回调，则展示用户自定 义的错误页；若未设置，则展示ArkWeb提供的默认错误页。当enable和includeSubframe同时设置为true时，subframe加载发生错误也会展示错误页，onOverrideErrorPage回调对 subframe同样生效。 > **说明：** > > - 当enable设置为false时，无论includeSubframe取何值，mainframe和subframe的错误页功能均不启用。 > > - 当includeSubframe设置为false时，本接口行为与 > [setErrorPageEnabled](#seterrorpageenabled)一致，即仅启用mainframe错误页功 > 能，不启用subframe错误页功能。 > > - 可通过errorPageEvent.request.isMainFrame()判断错误来源是mainframe还是subframe，以便在 > onOverrideErrorPage回调中分别设置对应的自定义错误页。 > 26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebviewController-setErrorPageEnabled(enable: boolean, includeSubframe: boolean): void--><!--Device-WebviewController-setErrorPageEnabled(enable: boolean, includeSubframe: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示是否启用mainframe错误页功能。true表示启用，false表示不启用。启用后mainframe加载出错将展示错误页。 |
| includeSubframe | boolean | 是 | 表示是否同时启用subframe错误页功能。true表示启用，false表示不启用。启用后subframe加载出错也将展示错误页。仅在enable为 true时有效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setHostIP

```TypeScript
static setHostIP(hostName: string, address: string, aliveTime: number): void
```

设置主机域名解析后的IP地址。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static setHostIP(hostName: string, address: string, aliveTime: number): void--><!--Device-WebviewController-static setHostIP(hostName: string, address: string, aliveTime: number): void-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

## setHttpDns

```TypeScript
static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void
```

设置Web组件是否使用HTTPDNS解析DNS。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void--><!--Device-WebviewController-static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| secureDnsMode | [SecureDnsMode](arkts-arkweb-webview-securednsmode-e.md) | 是 | 使用HTTPDNS的模式。 |
| secureDnsConfig | string | 是 | HTTPDNS server的配置，必须是https协议并且只允许配置一个server。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3. Parameter verification failed. |

## setNetworkAvailable

```TypeScript
setNetworkAvailable(enable: boolean): void
```

设置JavaScript中的`window.navigator.onLine`属性。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setNetworkAvailable(enable: boolean): void--><!--Device-WebviewController-setNetworkAvailable(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置JavaScript中的`window.navigator.onLine`属性。 <br>true表示设置JavaScript中的`window.navigator.onLine`属性为true，false表示设置JavaScript中的`window.navigator.onLine`属性为 false。 <br>默认值：true。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setPathAllowingUniversalAccess

```TypeScript
setPathAllowingUniversalAccess(pathList: Array<string>): void
```

设置一个路径列表，当file协议访问该路径列表中的资源时，允许跨域访问本地文件，也允许跨域访问其他在线资源。此外，当设置了路径列表时，file协议仅允许访问路径列表中的资源。典型使用场景：用于需要允许Web组件跨域访问本地资源 文件，同时限制访问范围以保证安全的场景。（fileAccess的行为将会被此接口行为覆盖）。 setPathAllowingUniversalAccess放开目录的跨域访问限制是一个高风险操作。基于最小权限原则，当前el1，el2放开的路径是固定的，路径列表中的路径应符合以下任一路径格式： 1.应用文件目录的子目录（应用文件目录通过Ability Kit中的 [Context.filesDir](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)获取），例如： * /data/storage/el2/base/files/example * /data/storage/el2/base/haps/entry/files/example 2.应用资源目录及其子目录（应用资源目录通过Ability Kit中的 [Context.resourceDir](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)获取），例如： * /data/storage/el1/bundle/entry/resources/resfile * /data/storage/el1/bundle/entry/resources/resfile/example 3.从API version 21开始，还包括了应用缓存目录及其子目录（应用缓存目录通过Ability Kit中的 [Context.cacheDir](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)获取），例如： * /data/storage/el2/base/cache * /data/storage/el2/base/haps/entry/cache/example * 设置的目录路径中，不允许包含cache/web，否则会抛出异常码401。如果设置目录路径是cache，cache/web也不允许访问。 4.从API version 21开始，还包括了应用临时目录及其子目录（应用临时目录通过Ability Kit中的 [Context.tempDir](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)获取），例如： * /data/storage/el2/base/temp * /data/storage/el2/base/haps/entry/temp/example 当路径列表中有其中一个路径不满足以上条件之一，则会抛出异常码401，并且设置路径列表失败。当设置的路径列表为空，则file协议可访问范围以fileAccess的 行为为准。

**起始版本：** 12

<!--Device-WebviewController-setPathAllowingUniversalAccess(pathList: Array<string>): void--><!--Device-WebviewController-setPathAllowingUniversalAccess(pathList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathList | Array&lt;string&gt; | 是 | 路径列表 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Parameter string is too long. <br>3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setPrintBackground

```TypeScript
setPrintBackground(enable: boolean): void
```

设置是否打印网页背景，该接口与[PrintAttributes](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-print-printattributes-i.md)打印参数配置不一致时，本接口设置优先级高于打印参数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setPrintBackground(enable: boolean): void--><!--Device-WebviewController-setPrintBackground(enable: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示是否打印网页背景。 <br>true表示设置为打印网页背景，false表示取消网页背景打印。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setRenderProcessMode

```TypeScript
static setRenderProcessMode(mode: RenderProcessMode): void
```

设置ArkWeb渲染子进程模式，可根据应用对内存占用与渲染进程隔离的需求选择对应的模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static setRenderProcessMode(mode: RenderProcessMode): void--><!--Device-WebviewController-static setRenderProcessMode(mode: RenderProcessMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [RenderProcessMode](arkts-arkweb-webview-renderprocessmode-e.md) | 是 | 渲染子进程模式。 <br>可以先调用[getRenderProcessMode()](#getrenderprocessmode)查看当前设备的ArkWeb渲染子进程模式，枚 举值0为单子进程模式，枚举值1为多子进程模式。 <br>手机默认为单渲染子进程模式，平板和PC/2in1默认为多渲染子进程模式。 <br>如果传入RenderProcessMode枚举值之外的非法数字，则默认识别为多渲染子进程模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## setScrollable

```TypeScript
setScrollable(enable: boolean, type?: ScrollType): void
```

设置网页是否允许滚动。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setScrollable(enable: boolean, type?: ScrollType): void--><!--Device-WebviewController-setScrollable(enable: boolean, type?: ScrollType): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示是否将网页设置为允许滚动。 <br>true表示设置为允许滚动，false表示禁止滚动。 <br>默认值：true。 |
| type | [ScrollType](arkts-arkweb-webview-scrolltype-e.md) | 否 | 网页可触发的滚动类型，支持缺省配置。<br/> - enable为false时，表示禁止ScrollType类型的滚动，当ScrollType缺省时表示禁止所有类型网页 滚动。<br/> - enable为true时，ScrollType缺省与否，都表示允许所有类型的网页滚动。 <br>传入null或undefined时会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setScrollbarMode

```TypeScript
static setScrollbarMode(scrollbarMode: ScrollbarMode): void
```

在Web页面场景，设置全局滚动条模式。不显式调用时，默认为[ScrollbarMode.OVERLAY_LAYOUT_SCROLLBAR](arkts-arkweb-webview-scrollbarmode-e.md)（非常驻滚动条）。 > **说明：** > > - 根据滚动条模式，改变当前应用所有web滚动条模式为常驻滚动条或非常驻滚动条。 > > - 若forceDisplayScrollBar接口与当前接口同时设置，forceDisplayScrollBar接口设置不生效。 > > - 该接口需要在WebViewController绑定Web组件之前调用。

**起始版本：** 23

<!--Device-WebviewController-static setScrollbarMode(scrollbarMode: ScrollbarMode): void--><!--Device-WebviewController-static setScrollbarMode(scrollbarMode: ScrollbarMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollbarMode | [ScrollbarMode](arkts-arkweb-webview-scrollbarmode-e.md) | 是 | 滚动条模式。 |

## setServiceWorkerWebSchemeHandler

```TypeScript
static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

为当前应用的所有Web组件设置用于拦截ServiceWorker的WebSchemeHandler。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void--><!--Device-WebviewController-static setServiceWorkerWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scheme | string | 是 | 要拦截的协议。 |
| handler | [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) | 是 | 拦截此协议的拦截器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setSiteIsolationMode

```TypeScript
static setSiteIsolationMode(mode: SiteIsolationMode): void
```

设置站点隔离模式。站点隔离机制将不同源的网站隔离在不同的渲染进程中，减少跨域攻击面。例如：PC等设备上，在未启用站点隔离模式时，原有进程模型是每一个Tab对应一个渲染进程，开启站点隔离后，一个Tab下不同源的Iframe可在独 立的渲染进程中运行。 对于仅加载可信网页的第三方应用，可以关闭此功能，以提升性能并减少内存占用，同时减少跨域访问的拦截。默认值根据不同的设备而定，PC/Table采用严格站点隔离 [SiteIsolationMode.STRICT](arkts-arkweb-webview-siteisolationmode-e.md)，Phone默认部分站点隔离 [SiteIsolationMode.PARTIAL](arkts-arkweb-webview-siteisolationmode-e.md)。[坚盾守护模式](../../../web/web-secure-shield-mode.md)下采用 严格站点隔离。 > **说明：** > > 不能在单子进程模式下设置严格站点隔离。 > > 接口只能在初始化时调用一次，不支持反复修改。

**起始版本：** 21

<!--Device-WebviewController-static setSiteIsolationMode(mode: SiteIsolationMode): void--><!--Device-WebviewController-static setSiteIsolationMode(mode: SiteIsolationMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [SiteIsolationMode](arkts-arkweb-webview-siteisolationmode-e.md) | 是 | 设置站点隔离模式。 <br>默认值取决于设备类型和设备模式：PC/Tablet默认严格站点隔离，Phone默认部分站点隔离；坚盾守护模式默认严格站点隔离。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. Possible causes: 1. Site Isolation mode is already set by the developer. 2. Site Isolation mode cannot be strict in single-render-process mode. 3. Site Isolation mode cannot be changed while Secure Shield mode is active. |

## setSocketIdleTimeout

```TypeScript
static setSocketIdleTimeout(timeout: number): void
```

设置ArkWeb中已使用过的空闲socket的超时时间，即已使用过的socket可以处于空闲状态的最大时长。如果设置的值与已存在的空闲socket超时时间不同，则根据新的值对已存在的空闲socket进行清理。 未使用该接口设置空闲socket的超时时间时，ArkWeb的默认值为300s。

**起始版本：** 21

<!--Device-WebviewController-static setSocketIdleTimeout(timeout: number): void--><!--Device-WebviewController-static setSocketIdleTimeout(timeout: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | ArkWeb中已经使用过的空闲socket的超时时间。 <br>取值范围：[30,300]，单位：s。 <br>小于30时生效值为30，大于300时生效值为300。 |

## setSoftKeyboardBehaviorMode

```TypeScript
setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void
```

设置软键盘自动控制模式，当接口没有显式调用时，Web组件失去焦点或获得焦点、状态切换为inactive或active时，系统均会尝试触发软键盘自动隐藏或拉起。典型使用场景：不希望Web组件在inactive或active状态切 换时自动隐藏或重新拉起软键盘时，可使用DISABLE_AUTO_KEYBOARD_ON_ACTIVE；需要保留默认自动管理行为时，可使用DEFAULT。

**起始版本：** 22

<!--Device-WebviewController-setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void--><!--Device-WebviewController-setSoftKeyboardBehaviorMode(mode: WebSoftKeyboardBehaviorMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebSoftKeyboardBehaviorMode](arkts-arkweb-webview-websoftkeyboardbehaviormode-e.md) | 是 | Web软键盘自动控制模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string): void
```

设置Web的URL白名单，只有白名单内的URL才能允许加载/跳转，否则将拦截并弹出告警页。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setUrlTrustList(urlTrustList: string): void--><!--Device-WebviewController-setUrlTrustList(urlTrustList: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| urlTrustList | string | 是 | URL白名单列表，使用json格式配置，最大支持10MB。<br/>白名单设置接口为覆盖方式，多次调用接口时，以最后一次设置为准。<br/>当本参数为空字符串 时，表示取消白名单，放行所有URL的访问。 <br/>json格式示例： <br/>{ <br>  "UrlPermissionList": [ <br/>    { <br/>      "scheme": "https", <br/>      "host": "www.example1.com", <br/>      "port": 443, <br/>      "path": "pathA/pathB" <br/>    }, <br/>    { <br/>      "scheme": "http", <br/>      "host": "www.example2.com", <br/>      "port": 80, <br/>      "path": "test1/test2/test3"<br/>    } <br/>  ] <br/>} |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Parameter string is too long. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## setUrlTrustList

```TypeScript
setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void
```

设置Web的URL白名单，只有白名单内的URL才能允许加载/跳转，否则将拦截并弹出告警页。扩展了对Opaque Origin URL以及通配符规则的控制能力。

**起始版本：** 24

<!--Device-WebviewController-setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void--><!--Device-WebviewController-setUrlTrustList(urlTrustList: string, allowOpaqueOrigin: boolean, supportWildcard: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| urlTrustList | string | 是 | URL白名单列表，使用json格式配置，最大支持10MB。<br/>白名单设置接口为覆盖方式，多次调用接口时，以最后一次设置为准。<br/>当本参数为空字符串 时，表示取消白名单，放行所有URL的访问。 <br/>json格式示例： <br/>{ <br>  "UrlPermissionList": [ <br/>    { <br/>      "scheme": "https", <br/>      "host": "www.example1.com", <br/>      "port": 443, <br/>      "path": "pathA/pathB" <br/>    }, <br/>    { <br/>      "scheme": "http", <br/>      "host": "www.example2.com", <br/>      "port": 80, <br/>      "path": "test1/test2/test3"<br/>    } <br/>  ] <br/>} |
| allowOpaqueOrigin | boolean | 是 | true表示允许loadUrl直接加载javascript/data等 [不透明源URL](https://mdn.org.cn/en-US/docs/Web/URI/Reference/Schemes)，false表示不允许加载不透明源URL。 |
| supportWildcard | boolean | 是 | true表示支持对host、path的通配符匹配能力，例如白名单配置了`*.example.com`，则访问`a.example.com`和 `b.example.com`都是允许的。false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Initialization error. The WebviewController must be associated with a Web component. |

## setUserAgentClientHintsEnabled

```TypeScript
static setUserAgentClientHintsEnabled(enabled: boolean): void
```

设置是否开启User-Agent Client Hints功能。 > **说明：** > > User-Agent Client Hints（UA-CH）是一种替代传统User-Agent字符串的隐私保护机制，通过按需请求和结构化数据传递客户端信息，减少过度追踪风险。 > > 不使用该方法时，默认不开启User-Agent Client Hints功能。

**起始版本：** 24

<!--Device-WebviewController-static setUserAgentClientHintsEnabled(enabled: boolean): void--><!--Device-WebviewController-static setUserAgentClientHintsEnabled(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否开启User-Agent Client Hints功能。<br/>true表示开启，false表示不开启。 |

## setUserAgentForHosts

```TypeScript
static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void
```

针对特定网站设置自定义用户代理，会覆盖系统的用户代理，应用内所有Web组件生效。 当需要对特定网站设置自定义用户代理时，建议在Web组件创建前调用setUserAgentForHosts方法设置User-Agent，再创建指定src的Web组件或通过 [loadUrl](#loadurl)加载具体页面。 默认User-Agent定义与使用场景，及相关User-Agent接口定义优先级请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)。

**起始版本：** 20

<!--Device-WebviewController-static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void--><!--Device-WebviewController-static setUserAgentForHosts(userAgent: string, hosts : Array<string>) : void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | 用户自定义代理信息。建议先使用 [getDefaultUserAgent](#getdefaultuseragent)获取当前默认用户代理，在此基础上追加自定义用户代理信息。 |
| hosts | Array&lt;string&gt; | 是 | 用户自定义代理的相关域名列表，每次调用时仅保留最新传入的列表，并限制最大条目数为两万，超出部分自动截断。 |

## setUserAgentMetadata

```TypeScript
setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void
```

设置与User-Agent相对应的UserAgent Metadata数据。 > **说明：** > > User-Agent Metadata将用于填充用户代理客户端提示，它们可以提供客户端的品牌和版本信息、底层操作系统的品牌和主要版本，以及底层设备的详细信息。 > > 用户代理可以通过setCustomUserAgent、setAppCustomUserAgent或setUserAgentForHosts来设置。 > > 如果根据覆盖后的User-Agent未找到UserAgentMetadata，且覆盖后的User-Agent包含系统默认的User-Agent，则将使用系统默认值。 > > 如果根据覆盖后的User-Agent未找到UserAgentMetadata，但覆盖后的 User-Agent 不包含系统默认用户代理，则只会生成低级用户代理客户端提示。

**起始版本：** 24

<!--Device-WebviewController-setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void--><!--Device-WebviewController-setUserAgentMetadata(userAgent: string, metaData: UserAgentMetadata): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | 用户自定义代理信息。可以使用[getUserAgent](#getuseragent)获取当前默认用户代 理。 |
| metaData | [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md) | 是 | userAgent对应的UserAgentMetadata。可以先使用 [getUserAgentMetadata](#getuseragentmetadata)获取当前默认值，然后用相应方法进行修改。 |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean): void
```

设置是否启用网页调试功能。详情请参考[DevTools工具](../../../web/web-debugging-with-devtools.md)。 安全提示：启用网页调试功能可以让用户检查修改Web页面内部状态，存在安全隐患，不建议在应用正式发布版本中启用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean): void--><!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | 是 | 设置是否启用网页调试功能。 <br>true表示启用网页调试功能。false表示不启用网页调试功能。 <br>默认值：false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

## setWebDebuggingAccess

```TypeScript
static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void
```

设置是否启用无线网页调试功能，默认不开启。 * 当没有指定端口port时，该接口等同于 [setWebDebuggingAccess](#setwebdebuggingaccess)接口， ArkWeb会启动一个本地domain socket监听。 * 当指定了端口port时，ArkWeb会启动一个tcp socket监听。这时可以无线调试网页。详情请参考[无线调试](../../../web/web-debugging-with-devtools.md#无线调试)。 由于小于1024的端口号作为熟知或系统端口，在操作系统上需要特权才能开启，因此port的取值必须大于1024，否则该接口会抛出异常。 安全提示：启用网页调试功能可以让用户检查修改Web页面内部状态，存在安全隐患，不建议在应用正式发布版本中启用。

**起始版本：** 20

<!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void--><!--Device-WebviewController-static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| webDebuggingAccess | boolean | 是 | 设置是否启用网页调试功能。<br/>true表示开启网页调试功能，false表示关闭网页调试功能。 |
| port | number | 是 | 指定DevTools服务的tcp端口号。如果没有指定port，那么该接口等同于 [setWebDebuggingAccess](#setwebdebuggingaccess)接 口。<br/>取值范围: (1024, 65535]<br/>如果port的值在区间[0, 1024]内，则会抛出BusinessError异常，错误码为17100023。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100023](../errorcode-webview.md#17100023-使用了不被允许的端口号) | The port number is not within the allowed range. |

## setWebDestroyMode

```TypeScript
static setWebDestroyMode(mode: WebDestroyMode): void
```

设置Web组件的销毁模式。当Web组件销毁时，销毁模式会影响Web内核资源释放的时机，例如JavaScript运行上下文、渲染上下文等。默认值： [WebDestroyMode.NORMAL_MODE](arkts-arkweb-webview-webdestroymode-e.md)（普通模式），由系统决定销毁时机。应用可设置 [WebDestroyMode.FAST_MODE](arkts-arkweb-webview-webdestroymode-e.md)（快速模式），以立即销毁资源，从而提升特定场景的性能。 > **说明：** > > [WebDestroyMode.FAST_MODE](arkts-arkweb-webview-webdestroymode-e.md)（快速模式）会改变Web组件销毁时机，应用需关注依赖Web组件销毁时机的错误实现，例如：Web组件销毁后仍调用 > WebviewController的未定义行为，与[WebDestroyMode.NORMAL_MODE](arkts-arkweb-webview-webdestroymode-e.md)（普通模式）相比，销毁时机提前，有更高的几率触发未关联绑 > 定的异常（17100001），建议应用捕捉异常，或者通过[getAttachState](#getattachstate)方法查询是否绑定状态，来避免稳定性问 > 题。

**起始版本：** 20

<!--Device-WebviewController-static setWebDestroyMode(mode: WebDestroyMode): void--><!--Device-WebviewController-static setWebDestroyMode(mode: WebDestroyMode): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebDestroyMode](arkts-arkweb-webview-webdestroymode-e.md) | 是 | 设置Web组件的销毁模式。 <br>默认值：WebDestroyMode.NORMAL_MODE |

## setWebSchemeHandler

```TypeScript
setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void
```

为Web组件设置[WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md), [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md)类用于 拦截指定scheme的请求。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void--><!--Device-WebviewController-setWebSchemeHandler(scheme: string, handler: WebSchemeHandler): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scheme | string | 是 | 要拦截的协议。 |
| handler | [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) | 是 | 拦截此协议的拦截器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## slideScroll

```TypeScript
slideScroll(vx: number, vy: number): void
```

按照指定速度模拟对页面的轻扫滚动动作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-slideScroll(vx: number, vy: number): void--><!--Device-WebviewController-slideScroll(vx: number, vy: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vx | number | 是 | 轻扫滚动的水平速度分量，其中水平向右为速度正方向。 <br>单位：vp/s。 |
| vy | number | 是 | 轻扫滚动的垂直速度分量，其中垂直向下为速度正方向。 <br>单位：vp/s。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## startCamera

```TypeScript
startCamera(): void
```

开启当前网页摄像头捕获。使用摄像头功能前请在module.json5中添加权限: ohos.permission.CAMERA，具体权限的添加方法请参考 [在配置文件中声明权限](../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-startCamera(): void--><!--Device-WebviewController-startCamera(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## startDownload

```TypeScript
startDownload(url: string): void
```

使用Web组件的下载能力来下载指定的URL，比如下载网页中指定的图片。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-startDownload(url: string): void--><!--Device-WebviewController-startDownload(url: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 下载地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**适用版本：** 22+ |

## stop

```TypeScript
stop(): void
```

停止页面加载。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-stop(): void--><!--Device-WebviewController-stop(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## stopAllMedia

```TypeScript
stopAllMedia(): void
```

控制网页所有音视频停止。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-stopAllMedia(): void--><!--Device-WebviewController-stopAllMedia(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## stopCamera

```TypeScript
stopCamera(): void
```

停止当前网页摄像头捕获。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-stopCamera(): void--><!--Device-WebviewController-stopCamera(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## stopMicrophone

```TypeScript
stopMicrophone(): void
```

停止当前网页麦克风捕获。

**起始版本：** 23

<!--Device-WebviewController-stopMicrophone(): void--><!--Device-WebviewController-stopMicrophone(): void-End-->

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean): Promise<string>--><!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| baseName | string | 是 | 生成的离线网页存储位置，该值不能为空。 |
| autoName | boolean | 是 | 决定是否自动生成文件名。 <br>false表示按baseName的文件名存储，true表示根据当前URL自动生成文件名，并按baseName的文件目录存储。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise实例，保存成功返回文件路径，保存失败返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## storeWebArchive

```TypeScript
storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void
```

以回调方式异步保存当前页面。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void--><!--Device-WebviewController-storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| baseName | string | 是 | 生成的离线网页存储位置，该值不能为空。 |
| autoName | boolean | 是 | 决定是否自动生成文件名。 <br>false表示按baseName的文件名存储，true表示根据当前URL自动生成文件名，并按baseName的文件目录存储。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 返回文件存储路径，保存网页失败会返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |
| [17100003](../errorcode-webview.md#17100003-resource路径错误) | Invalid resource path or file type. |

## terminateRenderProcess

```TypeScript
terminateRenderProcess(): boolean
```

销毁渲染进程。 调用该接口将会主动销毁相关联的渲染进程。如果渲染进程尚未启动，或者已销毁则没有任何影响。此外销毁渲染进程会同时影响所有与该渲染进程关联的其他实例。

**起始版本：** 12

<!--Device-WebviewController-terminateRenderProcess(): boolean--><!--Device-WebviewController-terminateRenderProcess(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回销毁渲染进程的结果。 <br>返回true表示渲染进程可以被销毁或已被销毁，返回false表示渲染进程不可以被销毁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## trimMemoryByPressureLevel

```TypeScript
static trimMemoryByPressureLevel(level: PressureLevel): void
```

根据指定的内存压力等级，主动清理Web组件占用的缓存。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static trimMemoryByPressureLevel(level: PressureLevel): void--><!--Device-WebviewController-static trimMemoryByPressureLevel(level: PressureLevel): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [PressureLevel](arkts-arkweb-webview-pressurelevel-e.md) | 是 | 需要清理内存的内存等级。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Parameter string is too long. <br>3.Parameter verification failed. |

## waitForAttached

```TypeScript
waitForAttached(timeout: number): Promise<ControllerAttachState>
```

异步等待WebViewController与Web组件绑定完成，绑定完成或超时触发回调，通过Promise方式返回当前 [ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md)状态。

**起始版本：** 20

<!--Device-WebviewController-waitForAttached(timeout: number): Promise<ControllerAttachState>--><!--Device-WebviewController-waitForAttached(timeout: number): Promise<ControllerAttachState>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 异步等待时长。<br/>取值范围: [0, 65535]<br/>单位: ms |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md)&gt; | Promise实例，返回当前 [ControllerAttachState]{ |

## warmupServiceWorker

```TypeScript
static warmupServiceWorker(url: string): void
```

预热ServiceWorker，以提升首屏页面的加载速度（仅限于会使用ServiceWorker的页面）。在加载URL之前调用此API。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-static warmupServiceWorker(url: string): void--><!--Device-WebviewController-static warmupServiceWorker(url: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 需要预热ServiceWorker的URL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. The webpage corresponding to the URL is invalid, or the URL length exceeds 2*1024*1024.<br>**适用版本：** 22+ |

## webPageSnapshot

```TypeScript
webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void
```

获取网页全量绘制结果。 > **说明：** > > 此接口不支持并发调用。 > > 仅支持对渲染进程上的资源进行截图：静态图片和文本。 > > 如果页面有视频则截图时会显示该视频的占位图片，没有占位图片则显示空白。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void--><!--Device-WebviewController-webPageSnapshot(info: SnapshotInfo, callback: AsyncCallback<SnapshotResult>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [SnapshotInfo](arkts-arkweb-webview-snapshotinfo-i.md) | 是 | 全量绘制结果入参。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SnapshotResult](arkts-arkweb-webview-snapshotresult-i.md)&gt; | 是 | 全量绘制回调结果。 |

## zoom

```TypeScript
zoom(factor: number): void
```

调整当前网页的缩放比例，zoomAccess需为true。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-zoom(factor: number): void--><!--Device-WebviewController-zoom(factor: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factor | number | 是 | 基于当前网页所需调整的相对缩放比例，入参要求大于0，当入参为1时为默认加载网页的缩放比例，入参小于1为缩小，入参大于1为放大。 <br>取值范围：(0，100]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100004](../errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## zoomIn

```TypeScript
zoomIn(): void
```

调用此接口将当前网页进行放大，比例为25%。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-zoomIn(): void--><!--Device-WebviewController-zoomIn(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100004](../errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

## zoomOut

```TypeScript
zoomOut(): void
```

调用此接口将当前网页进行缩小，比例为20%。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebviewController-zoomOut(): void--><!--Device-WebviewController-zoomOut(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100004](../errorcode-webview.md#17100004-功能开关未打开) | Function not enabled. |
| [17100001](../errorcode-webview.md#17100001-webviewcontroller没有和具体的web组件关联) | Init error. The WebviewController must be associated with a Web component. |

