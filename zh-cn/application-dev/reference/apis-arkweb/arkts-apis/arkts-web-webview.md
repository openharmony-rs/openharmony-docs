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
| [once](arkts-arkweb-webview-once-f.md#once-1) | Subscribe to a callback of a specified type of web event once. |

### 类

| 名称 | 说明 |
| --- | --- |
| [AdsBlockManager](arkts-arkweb-webview-adsblockmanager-c.md) | This class is used to set adblock config. |
| [BackForwardCacheOptions](arkts-arkweb-webview-backforwardcacheoptions-c.md) | 前进后退缓存相关设置对象，用来控制Web组件前进后退缓存相关选项。 |
| [BackForwardCacheSupportedFeatures](arkts-arkweb-webview-backforwardcachesupportedfeatures-c.md) | This class is used to enable back forward cache supported features. |
| [GeolocationPermissions](arkts-arkweb-webview-geolocationpermissions-c.md) | Provides a method for managing web geographic location permissions. |
| [JsMessageExt](arkts-arkweb-webview-jsmessageext-c.md) | 该消息用于指示JavaScript代码执行结果的状态。 |
| [MediaSourceInfo](arkts-arkweb-webview-mediasourceinfo-c.md) | 表示媒体源的信息。 |
| [NativeMediaPlayerSurfaceInfo](arkts-arkweb-webview-nativemediaplayersurfaceinfo-c.md) | [应用接管网页媒体播放功能](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#enablenativemediaplayer12)中用于同层渲染的 surface 信息。 |
| [PdfData](arkts-arkweb-webview-pdfdata-c.md) | Defines the callback of createPdf, related to {@link createPDF} method. |
| [PrefetchOptions](arkts-arkweb-webview-prefetchoptions-c.md) | Defines the PrefetchOptions class. |
| [ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md) | The ProxyConfig used by applyProxyOverride. |
| [ProxyController](arkts-arkweb-webview-proxycontroller-c.md) | This class is used for set proxy for ArkWeb. |
| [ProxyRule](arkts-arkweb-webview-proxyrule-c.md) | The ProxyRule used by insertProxyRule. |
| [UserAgentBrandVersion](arkts-arkweb-webview-useragentbrandversion-c.md) | Class that holds brand name, major version and full version. Brand name and major version used to generated User-Agent client hints sec-cu-ua. Brand name and full version used to generated user-agent client hint sec-ch-ua-full-version-list. |
| [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md) | Holds User-Agent metadata information and uses to generate User-Agent client hints. |
| [WebCookieManager](arkts-arkweb-webview-webcookiemanager-c.md) | 提供了用于管理网页Cookie的方法。 |
| [WebDataBase](arkts-arkweb-webview-webdatabase-c.md) | Web组件数据库管理对象。 |
| [WebDownloadDelegate](arkts-arkweb-webview-webdownloaddelegate-c.md) | 下载任务的状态会通过该类的回调接口通知给用户。 |
| [WebDownloadItem](arkts-arkweb-webview-webdownloaditem-c.md) | 表示下载任务，您可以使用此对象来操作相应的下载任务。当前WebDownloadItem支持的下载文件名最长长度为255字节。 |
| [WebDownloadManager](arkts-arkweb-webview-webdownloadmanager-c.md) | 可以通过该类提供的接口来恢复失败的下载任务。 |
| [WebHttpBodyStream](arkts-arkweb-webview-webhttpbodystream-c.md) | The http body stream of the request. |
| [WebMessageExt](arkts-arkweb-webview-webmessageext-c.md) | The message received or sent from web message port. |
| [WebResourceHandler](arkts-arkweb-webview-webresourcehandler-c.md) | Used to intercept url requests. Response headers and body can be sent through WebResourceHandler. |
| [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) | This class is used to intercept requests for a specified scheme. |
| [WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md) | 通过WebSchemeHandler拦截到的请求。 |
| [WebSchemeHandlerResponse](arkts-arkweb-webview-webschemehandlerresponse-c.md) | 请求的响应，可以为被拦截的请求创建一个Response并填充自定义的内容返回给Web组件。 |
| [WebStorage](arkts-arkweb-webview-webstorage-c.md) | 通过WebStorage可管理Web SQL数据库接口和HTML5 Web存储接口，每个应用中的所有Web组件共享一个WebStorage。 |
| [WebviewController](arkts-arkweb-webview-webviewcontroller-c.md) | Provides methods for controlling the web controller. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackForwardList](arkts-arkweb-webview-backforwardlist-i.md) | Provides back and forward history list information method. related to {@link HistoryItem}. |
| [BlanklessFrameInterpolationInfo](arkts-arkweb-webview-blanklessframeinterpolationinfo-i.md) | 1.定义插帧状态信息2.ArkWeb使能白屏插帧优化的场景设备行为差异:仅支持手机平台，其他平台返回801 |
| [BlanklessInfo](arkts-arkweb-webview-blanklessinfo-i.md) | 页面首屏加载预测信息，主要包括首屏相似度预测值，首屏加载耗时预测值，预测错误码，应用需根据此信息来决策是否启用无白屏加载插帧方案。 |
| [BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md) | 1.插帧加载参数设备行为差异:仅支持手机平台，其他平台返回801 |
| [CacheOptions](arkts-arkweb-webview-cacheoptions-i.md) | Web组件预编译JavaScript生成字节码缓存的配置对象，用于控制字节码缓存更新。 |
| [HistoryItem](arkts-arkweb-webview-historyitem-i.md) | Provides information for history item in BackForwardList. |
| [HitTestValue](arkts-arkweb-webview-hittestvalue-i.md) | 提供点击区域的元素信息。示例代码参考[getLastHitTest](arkts-arkweb-webview-webviewcontroller-c.md#getlasthittest-1). |
| [MediaInfo](arkts-arkweb-webview-mediainfo-i.md) | [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的一个参数。包含了网页中媒体的信息。应用可以根据这些信息来创建接管网页媒体播放的播放器。 |
| [NativeMediaPlayerBridge](arkts-arkweb-webview-nativemediaplayerbridge-i.md) | [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的返回值类型。接管网页媒体的播放器和ArkWeb内核之间的一个接口类。ArkWeb内核通过该接口类的实例对象来控制应用创建的用来接管网页媒体的播放器。 |
| [NativeMediaPlayerHandler](arkts-arkweb-webview-nativemediaplayerhandler-i.md) | [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的参数。应用通过该对象，将播放器的状态通知给 ArkWeb 内核。 |
| [OfflineResourceMap](arkts-arkweb-webview-offlineresourcemap-i.md) | 本地离线资源配置对象，用于配置将被[injectOfflineResources](arkts-arkweb-webview-webviewcontroller-c.md#injectofflineresources-1)接口注入到内存缓存的本地离线资源的相关信息，内核会根据此信息生成资源缓存，并据此控制缓存的有效期。 |
| [PdfConfiguration](arkts-arkweb-webview-pdfconfiguration-i.md) | Defines the configuration of creating pdf, related to {@Link createPdf} method. |
| [RectEvent](arkts-arkweb-webview-rectevent-i.md) | 矩形定义。 |
| [RequestInfo](arkts-arkweb-webview-requestinfo-i.md) | Web组件发送的资源请求信息。 |
| [ScrollOffset](arkts-arkweb-webview-scrolloffset-i.md) | 网页当前的滚动偏移量。 |
| [SecurityParams](arkts-arkweb-webview-securityparams-i.md) | 定义enableAdvancedSecurityMode参数。 |
| [SnapshotInfo](arkts-arkweb-webview-snapshotinfo-i.md) | 获取全量绘制结果入参。 |
| [SnapshotResult](arkts-arkweb-webview-snapshotresult-i.md) | 全量绘制回调结果。 |
| [WebCustomScheme](arkts-arkweb-webview-webcustomscheme-i.md) | Defines the configuration of web custom scheme, related to {@link customizeSchemes} method. |
| [WebHeader](arkts-arkweb-webview-webheader-i.md) | Web组件返回的请求/响应头对象。 |
| [WebHttpCookie](arkts-arkweb-webview-webhttpcookie-i.md) | Defines the Web's HTTPCookie.&lt;p&gt;<strong>API Note</strong>:<br>The maximum length allowed for each attribute value in a cookie string is 1024.&lt;/p&gt; |
| [WebMessagePort](arkts-arkweb-webview-webmessageport-i.md) | Define html web message port. |
| [WebStorageOrigin](arkts-arkweb-webview-webstorageorigin-i.md) | 提供Web SQL数据库的使用信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArkWebEngineVersion](arkts-arkweb-webview-arkwebengineversion-e.md) | ArkWeb内核版本，请参考[M114内核在OpenHarmony 6.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md)，[M132内核在OpenHarmony 7.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md)。 |
| [BlanklessFrameInterpolationState](arkts-arkweb-webview-blanklessframeinterpolationstate-e.md) | 定义当前插帧状态设备行为差异:仅支持手机平台，其他平台返回801 |
| [ControllerAttachState](arkts-arkweb-webview-controllerattachstate-e.md) | 表示controller的绑定状态枚举 |
| [JsMessageType](arkts-arkweb-webview-jsmessagetype-e.md) | Enum type supplied to {@link runJavaScriptExt} for indicating the result of JavaScript code execution. |
| [MediaError](arkts-arkweb-webview-mediaerror-e.md) | 播放器的错误类型。 |
| [MediaPlaybackState](arkts-arkweb-webview-mediaplaybackstate-e.md) | 当前网页的播控状态。 |
| [MediaType](arkts-arkweb-webview-mediatype-e.md) | 表示媒体类型。 |
| [NetworkState](arkts-arkweb-webview-networkstate-e.md) | 播放器的网络状态。 |
| [OfflineResourceType](arkts-arkweb-webview-offlineresourcetype-e.md) | [OfflineResourceMap](arkts-arkweb-webview-offlineresourcemap-i.md)对象对应的本地离线资源的接口类型。 |
| [PlaybackStatus](arkts-arkweb-webview-playbackstatus-e.md) | [handleStatusChanged](arkts-arkweb-webview-nativemediaplayerhandler-i.md#handlestatuschanged-1) 接口参数， 用于表示播放器的播放状态。 |
| [Preload](arkts-arkweb-webview-preload-e.md) | 播放器预加载媒体数据。 |
| [PressureLevel](arkts-arkweb-webview-pressurelevel-e.md) | 内存压力等级。在应用主动清理Web组件占用的缓存时，Web内核会根据内存压力等级，进行缓存释放。 |
| [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | Enum type supplied to {@link insertProxyRule} for indicating the scheme filter for proxy. |
| [ReadyState](arkts-arkweb-webview-readystate-e.md) | 播放器的缓存状态。 |
| [RenderProcessMode](arkts-arkweb-webview-renderprocessmode-e.md) | Defines the render process mode. |
| [ScrollType](arkts-arkweb-webview-scrolltype-e.md) | Scroll滚动类型，用于[setScrollable](setScrollable)。 |
| [ScrollbarMode](arkts-arkweb-webview-scrollbarmode-e.md) | Web页面场景下，全局滚动条模式。 |
| [SecureDnsMode](arkts-arkweb-webview-securednsmode-e.md) | Web组件使用HTTPDNS的模式。 |
| [SecurityLevel](arkts-arkweb-webview-securitylevel-e.md) | 当前网页的安全级别。 |
| [SiteIsolationMode](arkts-arkweb-webview-siteisolationmode-e.md) | Indicates the site isolation mode of the application, default value depends on different devices type. |
| [SourceType](arkts-arkweb-webview-sourcetype-e.md) | 表示媒体源的类型。 |
| [SuspendType](arkts-arkweb-webview-suspendtype-e.md) | 表示播放器的挂起类型。 |
| [UserAgentFormFactor](arkts-arkweb-webview-useragentformfactor-e.md) | The form factors for User-Agent metadata. |
| [WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md) | 无白屏加载的异常错误码。 |
| [WebDestroyMode](arkts-arkweb-webview-webdestroymode-e.md) | 提供SetWebDestroyMode接口配置web组件的销毁模式 |
| [WebDownloadErrorCode](arkts-arkweb-webview-webdownloaderrorcode-e.md) | 下载任务的错误码。 |
| [WebDownloadState](arkts-arkweb-webview-webdownloadstate-e.md) | Defines the state for download. |
| [WebHitTestType](arkts-arkweb-webview-webhittesttype-e.md) | [getLastHitTest](arkts-arkweb-webview-webviewcontroller-c.md#getlasthittest-1)接口用于指示光标节点。 |
| [WebHttpCookieSameSitePolicy](arkts-arkweb-webview-webhttpcookiesamesitepolicy-e.md) | 指示是否将 cookie 限制为仅创建它的同一站点的请求可以携带。指示是否将 cookie 限制为仅创建它的同一站点的请求可以携带。 |
| [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) | 向 {@link onMessageEventExt} 提供的枚举类型，用于指示网络消息的类型。 |
| [WebResourceType](arkts-arkweb-webview-webresourcetype-e.md) | Defines the resource type of request. |
| [WebSoftKeyboardBehaviorMode](arkts-arkweb-webview-websoftkeyboardbehaviormode-e.md) | Indicates the keyboard behavior mode of the web component, default value is DEFAULT. |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md) | [onCreateNativeMediaPlayer](arkts-arkweb-webview-webviewcontroller-c.md#oncreatenativemediaplayer-1)方法的参数。一个回调函数，创建一个播放器，用于接管网页中的媒体播放。 |
| [OnProxyConfigChangeCallback](arkts-arkweb-webview-onproxyconfigchangecallback-t.md) | The callback for proxy changed. |
| [WebMessage](arkts-arkweb-webview-webmessage-t.md) | 用于描述{@link onMessageEventExt}所支持的数据类型。 |

