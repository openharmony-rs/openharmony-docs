# @ohos.web.webview

This module provides the capability to manage web modules.

**起始版本：** 9

<!--Device-unnamed-declare namespace webview--><!--Device-unnamed-declare namespace webview-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [once_string](arkts-arkweb-webview-oncestring-f.md#once_string) | 订阅一次指定类型Web事件的回调，Web事件的类型目前仅支持"webInited"，在Web引擎初始化完成时触发。 当应用中开始加载第一个Web组件时，Web引擎初始化，且后续在同一应用中继续加载其他Web组件时不会再触发once回调。当应用销毁最后一个Web组件时，若再加载第一个Web组件，应用重新进入Web引擎初始化流程。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AdsBlockManager](arkts-arkweb-webview-adsblockmanager-c.md) | AdsBlockManager是ArkWeb框架中用于管理Web组件广告过滤功能的类，提供对广告过滤规则的设置、域名黑白名单管理及过滤策略控制等能力。每个应用中的所有Web组件共享一个AdsBlockManager静态类，开发者可 通过该类向Web组件注入符合通用EasyList语法规则的广告过滤配置文件，并灵活控制特定网站的广告过滤启用状态。 AdsBlockManager的核心机制基于域名后缀匹配的AllowedList/DisallowedList双层策略：DisallowedList用于禁用特定网站的广告过滤，而AllowedList具有更高优先级，可在 DisallowedList的范围内重新开启部分子域名的广告过滤。广告过滤规则内部解析成功后会被持久化存储，应用重启后无需重复设置；而域名黑白名单不会持久化，应用重启后需重新配置。 |
| [BackForwardCacheOptions](arkts-arkweb-webview-backforwardcacheoptions-c.md) | BackForwardCacheOptions是ArkWeb框架中用于配置Web组件前进后退缓存（BFCache）行为的参数类。BFCache是一种页面缓存机制，当用户在浏览历史中前进或后退时，可将页面完整快照（包括 JavaScript状态）缓存起来，实现瞬时加载效果，显著提升用户体验。通过BackForwardCacheOptions，开发者可以控制每个Web组件允许缓存的最大页面个数以及页面在缓存中的最长停留时间。 |
| [BackForwardCacheSupportedFeatures](arkts-arkweb-webview-backforwardcachesupportedfeatures-c.md) | BackForwardCacheSupportedFeatures是ArkWeb框架中用于选择性控制允许使用了特定Web特性的页面可以进入前进后退缓存（BFCache）的配置类。默认情况下，使用同层渲染或视频托管等特性的页面会被阻 止进入BFCache，因为浏览器无法安全地保存和恢复这些与系统控件绑定的复杂状态。通过设置该类中的属性，开发者可以显式允许这些特性的页面进入BFCache，但需注意自行维护相关系统控件的生命周期，避免造成资源泄漏。完整示例代码参考 [enableBackForwardCache](arkts-arkweb-webview-webviewcontroller-c.md#enablebackforwardcache)。 |
| [GeolocationPermissions](arkts-arkweb-webview-geolocationpermissions-c.md) | GeolocationPermissions是Web组件的地理位置权限管理对象，提供对Web组件中已保存的地理位置权限状态的查询、授权、删除等管理能力。通过GeolocationPermissions，应用可以在网页发起地理位置请 求之前预先授权特定源的访问权限，也可以主动查询或清除已保存的权限记录，而无需依赖网页请求时的弹窗授权流程。 GeolocationPermissions适用于需要主动管理Web组件地理位置权限的场景，例如：应用希望预先授权信任的网站访问地理位置，避免每次访问都弹出授权提示；或应用需要清除用户不再需要的地理位置权限记录。访问地理位置时需添 加权限：ohos.permission.LOCATION、ohos.permission.APPROXIMATELY_LOCATION、ohos.permission.LOCATION_IN_BACKGROUND，具体权限说明请参 考[申请位置权限开发指导](../../../device/location/location-permission-guidelines.md)。 |
| [JsMessageExt](arkts-arkweb-webview-jsmessageext-c.md) | JsMessageExt是ArkWeb框架中用于封装 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 接口执行JavaScript脚本后返回结果的数据类。与常规的runJavaScript接口不同，runJavaScriptExt支持更丰富的返回值类型，JsMessageExt则为这些多样化的返回结果提供了类型安全的访问方式。开发 者通过JsMessageExt的getType方法先获取数据类型，再调用对应的get方法获取具体值。 JsMessageExt支持多种JavaScript返回值类型的解析：字符串（getString）、数值（getNumber）、布尔值（getBoolean）、原始二进制数据（getArrayBuffer）、数组（getArray ）等。当获取的数据类型与实际存储类型不匹配时（例如对数值类型调用getString），会抛出错误码17100014。从API version 22开始，JsMessageExt还提供了getErrorDescription方法，用 于获取JavaScript执行过程中的异常信息，如果返回值为object类型则统一格式化为描述字符串。 |
| [MediaSourceInfo](arkts-arkweb-webview-mediasourceinfo-c.md) | MediaSourceInfo 是表示媒体源信息的数据类。在 Web 媒体播放场景中，MediaSourceInfo 类封装了媒体源的基本信息，帮助应用了解媒体源的类型、地址和格式，应用根据这些信息创建自定义播放器并开始播放。 |
| [NativeMediaPlayerSurfaceInfo](arkts-arkweb-webview-nativemediaplayersurfaceinfo-c.md) | NativeMediaPlayerSurfaceInfo 使用enableNativeMediaPlayer来进行同层渲染的 surface 信息配置。该类允许应用接管网页媒体播放功能，通过配置 surface 的 id 和位置信息，实现网页媒体内容与应用界面的同层渲染融合，提升媒体播放体验。 |
| [PdfData](arkts-arkweb-webview-pdfdata-c.md) | PdfData是Web组件用于封装网页生成的PDF数据流的类。当应用需要将Web组件加载的网页内容以PDF格式保存时，通过[WebviewController](arkts-arkweb-webview-webviewcontroller-c.md)的 [createPdf](arkts-arkweb-webview-webviewcontroller-c.md#createpdf) 方法将网页内容转换为PDF数据流，该方法在回调或Promise中以PdfData对象返回。应用再通过PdfData的pdfArrayBuffer方法获取Uint8Array格式的数据流，结合文件IO接口将数据写入本地PDF文件。 PdfData适用于需要离线保存网页内容、生成网页PDF报告等场景。使用时需先加载Web组件并确保网页内容已渲染完成，再调用createPdf生成PDF数据流。 |
| [PrefetchOptions](arkts-arkweb-webview-prefetchoptions-c.md) | PrefetchOptions是ArkWeb框架中用于自定义网页预取行为的配置类，通过 [prefetchPage](arkts-arkweb-webview-webviewcontroller-c.md#prefetchpage) 的预取相关接口设置，自定义内容包括是否忽略响应头中的Cache-Control: no-store和设置两次预取间的最小时间间隔。 |
| [ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md) | ProxyConfig是ArkWeb框架中用于配置网络代理规则的类，配合[ProxyController](arkts-arkweb-webview-proxycontroller-c.md)实现对应用中所有Web组件网络请求的代理控制。通过 ProxyConfig，开发者可以灵活定义多种代理规则：指定特定URL使用特定代理服务器、指定某些URL直连服务器、定义绕过代理的规则等。 |
| [ProxyController](arkts-arkweb-webview-proxycontroller-c.md) | ProxyController是ArkWeb框架中用于管理应用中所有Web组件代理配置的静态类。通过ProxyController，开发者可以统一为应用中的所有Web请求设置或移除代理配置，适用于需要将Web流量路由到特定代理服务 器的场景（如企业网络环境、内容过滤、流量监控等）。 ProxyController提供两个核心方法：applyProxyOverride用于应用代理配置，接受一个[ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md)对象和代理设置成功的回调函数； removeProxyOverride用于移除当前代理配置，恢复为默认网络连接方式。需要注意的是，代理设置或移除后不会立即生效，在加载页面之前需等待回调函数触发，该回调函数会在UI线程上被调用。 |
| [ProxyRule](arkts-arkweb-webview-proxyrule-c.md) | ProxyRule是ArkWeb框架中代理规则只读信息的类，通过[getProxyRules](arkts-arkweb-webview-proxyconfig-c.md#getproxyrules)方法获取。当开发者通过ProxyConfig配置了代理 规则后，可通过getProxyRules获取已配置的规则列表，每条规则对应一个ProxyRule对象，用于查询规则的详细信息。 ProxyRule提供两个方法：getSchemeFilter用于获取该代理规则对应的协议过滤器（如MATCH_ALL_SCHEMES、MATCH_HTTP、MATCH_HTTPS等），getUrl用于获取该代理规则中指定的代理服 务器URL信息。ProxyRule对象为只读，由系统在配置代理规则时创建，应用只能查询其内容而不能修改。 |
| [UserAgentBrandVersion](arkts-arkweb-webview-useragentbrandversion-c.md) | UserAgentBrandVersion是ArkWeb框架中用于配置User-Agent客户端提示信息中品牌名称和版本号的数据类，配合 [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md)使用。在User-Agent Client Hints机制中，浏览器通过Sec-CH-UA-Full-Version-List 等请求标头向服务器报告品牌和版本信息，UserAgentBrandVersion用于定义其中的单个品牌条目。 UserAgentBrandVersion提供品牌名称和版本号的设置与获取方法：setBrand/getBrand用于设置和获取品牌名称（如“ArkWeb”等），setMajorVersion/getMajorVersion用于设 置和获取主版本号（如“126”），setFullVersion/getFullVersion用于设置和获取完整版本号（如“126.0.0.0”）。应用可通过修改这些值来定制Web组件向服务器报告的浏览器身份信息。 |
| [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md) | UserAgentMetadata是ArkWeb框架中用于配置User-Agent Client Hints（UA客户端提示）完整元数据的类。User-Agent Client Hints是一种现代化的HTTP请求标头机制，通过一 组Sec-CH-UA系列标头向服务器报告客户端信息，替代传统User-Agent字符串实现更安全、更细粒度的浏览器身份标识。通过UserAgentMetadata，应用可以自定义Web组件向服务器报告的所有客户端信息字段。 |
| [WebCookieManager](arkts-arkweb-webview-webcookiemanager-c.md) | WebCookieManager是Web组件的cookie管理器，提供对Web组件中cookie的全局管理能力。开发者通过该类可以实现cookie的获取、设置、保存、清除以及权限控制等操作。该类的所有方法均为静态方法，应用中的所有 Web组件共享一个WebCookieManager实例。cookie的格式遵循[RFC6265](https://www.rfc-editor.org/info/rfc6265/)标准。 使用隐私模式浏览网页时，cookie、缓存等数据不会写入本地持久化存储；隐私模式的Web组件销毁后，这些数据将被清除，不会保留。 |
| [WebDataBase](arkts-arkweb-webview-webdatabase-c.md) | Web组件数据库管理对象。 |
| [WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md) | WebDownloadDelegate是ArkWeb框架中用于监听和处理Web组件下载任务事件的委托类。当Web组件中的网页触发文件下载时（如用户点击下载链接或通过startDownload方法），下载任务的状态变化会通过该类的回 调接口通知给应用。开发者通过setDownloadDelegate将WebDownloadDelegate实例注册到Web组件，从而接管下载流程的完整生命周期管理。 WebDownloadDelegate定义了四个下载生命周期回调： [onBeforeDownload](arkts-arkweb-webview-webdownloaddelegate-c.md#onbeforedownload)在下载开始前触 发，应用需要在此回调中调用[WebDownloadItem.start](arkts-arkweb-webview-webdownloaditem-c.md#start)并指定下载路径，否则下载将一直处于PENDING状态； [onDownloadUpdated](arkts-arkweb-webview-webdownloaddelegate-c.md#ondownloadupdated)在下载过程中 触发，可获取下载进度（百分比）、已接收字节数等更新信息； [onDownloadFinish](arkts-arkweb-webview-webdownloaddelegate-c.md#ondownloadfinish)在下载完成时触 发；[onDownloadFailed](arkts-arkweb-webview-webdownloaddelegate-c.md#ondownloadfailed)在下载失败时 触发，可通过[WebDownloadItem.serialize](arkts-arkweb-webview-webdownloaditem-c.md#serialize)保存失败任务以便后续恢复。 |
| [WebDownloadItem](arkts-arkweb-webview-webdownloaditem-c.md) | WebDownloadItem是ArkWeb框架中用于表示和管理单个下载任务的类。通过[WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md)的回调参数，应用可以获取到 WebDownloadItem实例，进而对下载任务进行查询和控制，包括启动下载到指定路径、查询下载进度和状态、暂停/恢复/取消任务、序列化失败任务以便后续恢复等。 |
| [WebDownloadManager](arkts-arkweb-webview-webdownloadmanager-c.md) | WebDownloadManager是ArkWeb框架下Web组件下载任务的静态管理类，负责管理所有通过Web组件触发的文件下载流程。开发者可以通过该类设置下载委托以接收下载进度回调，以及恢复失败的下载任务。该类的所有方法均为静态 方法，在整个应用范围内全局生效。 WebDownloadManager与[WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md)、 [WebDownloadItem](arkts-arkweb-webview-webdownloaditem-c.md)配合使用：WebDownloadManager负责下载任务的生命周期管理和委托设置，WebDownloadDelegate负责向应用层 报告下载进度和状态变更事件，WebDownloadItem代表单个下载任务实体，支持暂停、恢复、取消等操作。 |
| [WebHttpBodyStream](arkts-arkweb-webview-webhttpbodystream-c.md) | WebHttpBodyStream是HTTP请求体数据流对象，用于在自定义scheme拦截场景中读取POST、PUT等请求的请求体数据。该对象通过WebSchemeHandlerRequest的getHttpBodyStream方 法获取，支持BYTES、FILE、BLOB、CHUNKED类型的数据。开发者可以通过该接口在自定义协议拦截器中读取上行数据，实现对请求体的检视或转发。注意本类中的其他接口需要在 [initialize](arkts-arkweb-webview-webhttpbodystream-c.md#initialize)成功后才能调用。 WebHttpBodyStream与[WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md)配合使用：WebSchemeHandlerRequest代表被拦截 的请求，WebHttpBodyStream代表该请求的HTTP body数据流。通过读取流中的数据，开发者可以获取完整的请求体内容。 |
| [WebMessageExt](arkts-arkweb-webview-webmessageext-c.md) | WebMessageExt是[WebMessagePort](arkts-arkweb-webview-webmessageport-i.md)接口中用于接收和发送的拓展数据对象，支持多种数据类型：字符串（STRING）、数值（NUMBER）、布尔值（ BOOLEAN）、二进制数据（ARRAY_BUFFER）、数组（ARRAY）和错误对象（ERROR）。该类为ArkTS侧与HTML5侧之间的跨语言消息通信提供了结构化的数据载体，通过setType/getType设置和获取数据类 型，再通过对应的setter/getter方法读写具体数据。 WebMessageExt与WebMessagePort配合使用：WebMessagePort负责消息通道的建立和消息的收发，WebMessageExt作为消息的有效载荷在不同语言运行时之间传递。使用扩展接口 [postMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#postmessageeventext)/ onMessageEventExt时，消息载 体即为WebMessageExt对象。 |
| [WebResourceHandler](arkts-arkweb-webview-webresourcehandler-c.md) | WebResourceHandler是自定义scheme拦截场景中用于向Web组件返回拦截请求结果的处理器。当WebSchemeHandler决定拦截一个请求后，开发者通过WebResourceHandler向Web组件提供自定义 的响应头（didReceiveResponse）、响应体数据（didReceiveResponseBody），并通知请求完成（didFinish）或失败（didFail）。其中didFail支持重载方法（API version 2 0+）以简化错误处理流程。该接口实现了应用层对网络请求的完全自定义响应。 WebResourceHandler与[WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md)、 [WebSchemeHandlerResponse](arkts-arkweb-webview-webschemehandlerresponse-c.md)配合使用：WebSchemeHandler的onRequestStart回调中接收 WebResourceHandler实例，开发者构造WebSchemeHandlerResponse对象，通过WebResourceHandler的didReceiveResponse和didReceiveResponseBody 传入响应头和响应体数据，最后调用didFinish或didFail结束请求。 |
| [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) | WebSchemeHandler是用于拦截指定scheme（协议）的网络请求的拦截器类，支持自定义协议处理、本地资源替换、特定请求拦截等场景。开发者通过实现onRequestStart回调来决定是否拦截某个请求，被拦截的请求可通过 WebResourceHandler自定义响应内容。通过WebviewController的 [setWebSchemeHandler](arkts-arkweb-webview-webviewcontroller-c.md#setwebschemehandler)方法将WebSchemeHandler实例注册到指定的scheme上，从而实现对该 scheme所有请求的截获和处理。 WebSchemeHandler与[WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md)、 [WebResourceHandler](arkts-arkweb-webview-webresourcehandler-c.md)、 [WebSchemeHandlerResponse](arkts-arkweb-webview-webschemehandlerresponse-c.md)配合使用：onRequestStart回调接收WebSchemeHandlerRequest（被拦 截的请求信息）和WebResourceHandler（用于返回自定义响应的处理器），返回boolean值表示是否拦截。onRequestStop在请求结束时触发（仅对已拦截的请求），用于资源清理。 |
| [WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md) | WebSchemeHandlerRequest类模块定义了通过WebSchemeHandler拦截到的资源请求的封装对象。当开发者注册自定义协议处理器（WebSchemeHandler）后，Web内核在拦截到匹配协议的请求时会创建 WebSchemeHandlerRequest实例并传递给回调方法。该对象提供以下请求信息查询方法：获取请求头信息、请求URL、请求方法、来源URL、判断是否为主框架请求、是否关联用户手势、获取请求体流、资源类型以及触发该请求的 Frame URL，从而据此决定是否拦截该请求并构造相应响应。 |
| [WebSchemeHandlerResponse](arkts-arkweb-webview-webschemehandlerresponse-c.md) | WebSchemeHandlerResponse是自定义scheme拦截场景中用于构造HTTP响应数据的类。开发者通过该类创建Response对象，设置HTTP状态码、状态文本、媒体类型、字符集、自定义响应头、网络错误码以及重定向 URL等属性，然后通过WebResourceHandler将自定义响应返回给Web组件。该类是自定义资源拦截的核心数据载体。 WebSchemeHandlerResponse与WebResourceHandler配合使用：开发者构造WebSchemeHandlerResponse对象并填充响应属性，然后通过WebResourceHandler的 didReceiveResponse方法将响应头发送给被拦截的请求。 |
| [WebStorage](arkts-arkweb-webview-webstorage-c.md) | 通过WebStorage可管理Web SQL数据库接口和HTML5 Web存储接口，每个应用中的所有Web组件共享一个WebStorage。 |
| [WebviewController](arkts-arkweb-webview-webviewcontroller-c.md) | WebviewController是Web组件各种行为的核心控制器，提供网页加载与导航控制、JavaScript交互、生命周期、滚动控制、页面缩放与内容查找、消息端口通信、缓存与证书管理等广泛功能。一个 WebviewController对象只能控制一个Web组件，且必须在Web组件和WebviewController绑定后，才能调用WebviewController上的方法（静态方法除外）。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackForwardList](arkts-arkweb-webview-backforwardlist-i.md) | BackForwardList是ArkWeb框架中用于访问Web组件浏览历史列表的接口，通过 [getBackForwardEntries](arkts-arkweb-webview-webviewcontroller-c.md#getbackforwardentries)方法获取。该接口提供对页面导航历史记录的只读访问能力，开发者可以获取当前历 史列表的基本信息（当前索引和历史条目总数），以及通过索引获取指定历史记录项的详细信息。 |
| [BlanklessFrameInterpolationInfo](arkts-arkweb-webview-blanklessframeinterpolationinfo-i.md) | 无白屏加载插帧状态信息，作为[BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md)中的回调入参使用。 |
| [BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md) | 页面首屏加载预测信息，主要包括首屏相似度预测值、首屏加载耗时预测值、预测错误码，应用需根据此信息来决策是否启用无白屏加载插帧方案。 |
| [BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md) | 无白屏加载插帧方案的加载参数。 |
| [CacheOptions](arkts-arkweb-webview-cacheoptions-i.md) | Web组件预编译JavaScript生成字节码缓存的配置对象，用于控制字节码缓存更新。 |
| [HistoryItem](arkts-arkweb-webview-historyitem-i.md) | 页面历史记录项。 |
| [HitTestValue](arkts-arkweb-webview-hittestvalue-i.md) | 提供点击区域的元素信息。示例代码参考[getLastHitTest](arkts-arkweb-webview-webviewcontroller-c.md#getlasthittest)。 |
| [MediaInfo](arkts-arkweb-webview-mediainfo-i.md) | [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的一个参数。包含了网页中媒体的信息。应用可以根据这些信息来创建 接管网页媒体播放的播放器。 |
| [NativeMediaPlayerBridge](arkts-arkweb-webview-nativemediaplayerbridge-i.md) | NativeMediaPlayerBridge 是[CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的返回值类 型，是接管网页媒体的播放器和 ArkWeb 内核之间的一个接口类。ArkWeb 内核通过该接口类的实例对象控制应用创建的用于接管网页媒体的播放器。该接口允许应用使用自定义的媒体播放器接管网页中的媒体内容播放，同时，该接口还支持播放 器的挂起和恢复机制。 |
| [NativeMediaPlayerHandler](arkts-arkweb-webview-nativemediaplayerhandler-i.md) | NativeMediaPlayerHandler 是[CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的参数。当 应用使用[NativeMediaPlayerBridge](arkts-arkweb-webview-nativemediaplayerbridge-i.md)接管网页媒体播放时，需要通过将播放器的各种状态变化实时同步给 ArkWeb 内核，确保网页 JavaScript 能够获取正确的播放器状态，ArkWeb 内核会将这些状态转换为标准的 HTML5 Media Events，触发网页中注册的事件监听器，从而保证网页功能的正常运行。 |
| [OfflineResourceMap](arkts-arkweb-webview-offlineresourcemap-i.md) | 本地离线资源配置对象，用于配置将被[injectOfflineResources](arkts-arkweb-webview-webviewcontroller-c.md#injectofflineresources)接口注入到内存缓存的本地离线资源的相 关信息，内核会根据此信息生成资源缓存，并据此控制缓存的有效期。 |
| [PdfConfiguration](arkts-arkweb-webview-pdfconfiguration-i.md) | [createPdf](arkts-arkweb-webview-webviewcontroller-c.md#createpdf) 函数输入参数。 |
| [RectEvent](arkts-arkweb-webview-rectevent-i.md) | 矩形定义。 |
| [RequestInfo](arkts-arkweb-webview-requestinfo-i.md) | Web组件发送的资源请求信息。 |
| [ScrollOffset](arkts-arkweb-webview-scrolloffset-i.md) | 网页当前的滚动偏移量。 |
| [SecurityParams](arkts-arkweb-webview-securityparams-i.md) | 安全特性选项配置。该类提供了一组布尔开关，用于控制 ArkWeb 内核中特定 Web 功能的启用状态。通过关闭业务非必需的高风险模块（如 JIT编译、WebAssembly、WebGL 等），可减小攻击面、降低潜在漏洞利用风险。所 有属性均为可选，默认 false（不禁用），请根据具体业务场景按需配置。 |
| [SnapshotInfo](arkts-arkweb-webview-snapshotinfo-i.md) | 获取全量绘制结果入参。 |
| [SnapshotResult](arkts-arkweb-webview-snapshotresult-i.md) | 全量绘制回调结果。 |
| [WebCustomScheme](arkts-arkweb-webview-webcustomscheme-i.md) | 自定义协议配置。 |
| [WebHeader](arkts-arkweb-webview-webheader-i.md) | Web组件返回的请求/响应头对象。 |
| [WebHttpCookie](arkts-arkweb-webview-webhttpcookie-i.md) | cookie的相关字段。 |
| [WebMessagePort](arkts-arkweb-webview-webmessageport-i.md) | WebMessagePort是Web组件中用于应用侧（ArkTS）与HTML5侧（JavaScript）之间双向通信的消息端口接口。通过createWebMessagePorts创建一对关联的端口，将一个端口发送到HTML5侧，另 一个保留在应用侧，实现跨运行时消息传递。WebMessagePort支持两种消息协议：基础协议使用WebMessage作为消息载体（postMessageEvent/onMessageEvent），扩展协议使用 WebMessageExt支持更丰富的数据类型（postMessageEventExt/onMessageEventExt）。 |
| [WebStorageOrigin](arkts-arkweb-webview-webstorageorigin-i.md) | 提供Web SQL数据库的使用信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArkWebEngineVersion](arkts-arkweb-webview-arkwebengineversion-e.md) | ArkWeb内核版本，请参考 [M114内核在OpenHarmony 6.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md)， [M132内核在OpenHarmony 7.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md)。 |
| [BlanklessFrameInterpolationState](arkts-arkweb-webview-blanklessframeinterpolationstate-e.md) | 白屏插帧状态。 |
| [ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md) | WebviewController与Web组件的绑定状态。 |
| [JsMessageType](arkts-arkweb-webview-jsmessagetype-e.md) | [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 接口脚本执行后返回的结果的类型。 |
| [MediaError](arkts-arkweb-webview-mediaerror-e.md) | 播放器的错误类型。 |
| [MediaPlaybackState](arkts-arkweb-webview-mediaplaybackstate-e.md) | 当前网页的播放控制状态。 |
| [MediaType](arkts-arkweb-webview-mediatype-e.md) | 表示媒体类型。 |
| [NetworkState](arkts-arkweb-webview-networkstate-e.md) | 播放器的网络状态。 |
| [OfflineResourceType](arkts-arkweb-webview-offlineresourcetype-e.md) | [OfflineResourceMap](arkts-arkweb-webview-offlineresourcemap-i.md)对象对应的本地离线资源的接口类型。 |
| [PlaybackStatus](arkts-arkweb-webview-playbackstatus-e.md) | [handleStatusChanged](arkts-arkweb-webview-nativemediaplayerhandler-i.md#handlestatuschanged) 接口参数， 用于表示播放器的播放状态。 |
| [Preload](arkts-arkweb-webview-preload-e.md) | 播放器预加载媒体数据。 |
| [PressureLevel](arkts-arkweb-webview-pressurelevel-e.md) | 内存压力等级。在应用主动清理Web组件占用的缓存时，Web内核会根据内存压力等级，进行缓存释放。 |
| [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | 使用代理的请求的scheme信息。 |
| [ReadyState](arkts-arkweb-webview-readystate-e.md) | 播放器的缓存状态。 |
| [RenderProcessMode](arkts-arkweb-webview-renderprocessmode-e.md) | ArkWeb渲染子进程模式类型，可根据应用对内存占用与渲染进程隔离的需求选择对应的模式。 |
| [ScrollType](arkts-arkweb-webview-scrolltype-e.md) | Scroll滚动类型，用于[setScrollable](arkts-arkweb-webview-webviewcontroller-c.md#setscrollable)。 |
| [ScrollbarMode](arkts-arkweb-webview-scrollbarmode-e.md) | Web页面场景下，全局滚动条模式。 |
| [SecureDnsMode](arkts-arkweb-webview-securednsmode-e.md) | Web组件使用HTTPDNS的模式。 |
| [SecurityLevel](arkts-arkweb-webview-securitylevel-e.md) | 当前网页的安全级别。 |
| [SiteIsolationMode](arkts-arkweb-webview-siteisolationmode-e.md) | 站点隔离机制将不同源的网站隔离在不同的渲染子进程中，减少跨域攻击面。例如，PC上原有进程模型是每一个Tab对应一个渲染子进程，站点隔离打开后，让不同源的Iframe运行在独立的渲染子进程中。 |
| [SourceType](arkts-arkweb-webview-sourcetype-e.md) | 表示媒体源的类型。 |
| [SuspendType](arkts-arkweb-webview-suspendtype-e.md) | 表示播放器的挂起类型。 |
| [UserAgentFormFactor](arkts-arkweb-webview-useragentformfactor-e.md) | 用户设备形态。 |
| [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md) | 无白屏加载的异常错误码。 |
| [WebDestroyMode](arkts-arkweb-webview-webdestroymode-e.md) | Web组件的销毁模式，当Web组件销毁时，销毁模式会影响Web内核的资源释放时机，例如JavaScript运行上下文、渲染上下文等等。 |
| [WebDownloadErrorCode](arkts-arkweb-webview-webdownloaderrorcode-e.md) | 下载任务的错误码。 |
| [WebDownloadState](arkts-arkweb-webview-webdownloadstate-e.md) | 下载任务的状态。 |
| [WebHitTestType](arkts-arkweb-webview-webhittesttype-e.md) | 指示光标命中的节点类型。 |
| [WebHttpCookieSameSitePolicy](arkts-arkweb-webview-webhttpcookiesamesitepolicy-e.md) | 控制cookie在跨站请求中的发送行为。 |
| [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) | [WebMessagePort](arkts-arkweb-webview-webmessageport-i.md)接口所支持的数据类型。 |
| [WebResourceType](arkts-arkweb-webview-webresourcetype-e.md) | 资源请求的资源类型。 |
| [WebSoftKeyboardBehaviorMode](arkts-arkweb-webview-websoftkeyboardbehaviormode-e.md) | Web软键盘自动控制模式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md) | [onCreateNativeMediaPlayer](arkts-arkweb-webview-webviewcontroller-c.md#oncreatenativemediaplayer)方法的参数。一个回调函数，在网页需要播放媒体时被调用，用于 创建一个播放器接管网页中的媒体播放。通过接管机制，应用可以使用自定义播放器实现特殊功能或优化性能。 |
| [OnProxyConfigChangeCallback](arkts-arkweb-webview-onproxyconfigchangecallback-t.md) | 回调函数，在代理配置发生改变时被调用，回调成功表示代理设置成功。 |
| [WebMessage](arkts-arkweb-webview-webmessage-t.md) | 用于描述[WebMessagePort](arkts-arkweb-webview-webmessageport-i.md)所支持的数据类型。 |

