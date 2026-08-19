# @ohos.web.webview

This module provides the capability to manage web modules.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace webview--><!--Device-unnamed-declare namespace webview-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [once_string](arkts-na-webview-oncestring-f.md#once_string) | Subscribe to a callback of a specified type of web event once. |

### 类

| 名称 | 说明 |
| --- | --- |
| [AdsBlockManager](arkts-na-webview-adsblockmanager-c.md) | This class is used to set adblock config. |
| [BackForwardCacheOptions](arkts-na-webview-backforwardcacheoptions-c.md) | This class is used to set back forward cache options. |
| [BackForwardCacheSupportedFeatures](arkts-na-webview-backforwardcachesupportedfeatures-c.md) | This class is used to enable back forward cache supported features. |
| [GeolocationPermissions](arkts-na-webview-geolocationpermissions-c.md) | Implements a GeolocationPermissions object. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> You must load the Web component before calling the APIs in GeolocationPermissions. &lt;/p&gt; |
| [JsMessageExt](arkts-na-webview-jsmessageext-c.md) | The message for indicating the of result of JavaScript code execution. |
| [MediaSourceInfo](arkts-na-webview-mediasourceinfo-c.md) | 表示媒体源的信息。 |
| [NativeMediaPlayerSurfaceInfo](arkts-na-webview-nativemediaplayersurfaceinfo-c.md) | [应用接管网页媒体播放功能](../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#enablenativemediaplayer12) 中用于同层渲染的 surface 信息。 |
| [PdfData](arkts-na-webview-pdfdata-c.md) | Defines the callback of createPdf, related to createPDF method. |
| [PrefetchOptions](arkts-na-webview-prefetchoptions-c.md) | Defines the PrefetchOptions class. |
| [ProxyConfig](arkts-na-webview-proxyconfig-c.md) | The ProxyConfig used by applyProxyOverride. |
| [ProxyController](arkts-na-webview-proxycontroller-c.md) | This class is used for set proxy for ArkWeb. |
| [ProxyRule](arkts-na-webview-proxyrule-c.md) | The ProxyRule used by insertProxyRule. |
| [UserAgentBrandVersion](arkts-na-webview-useragentbrandversion-c.md) | Class that holds brand name, major version and full version. Brand name and major version used to generated User-Agent client hints sec-cu-ua. Brand name and full version used to generated user-agent client hint sec-ch-ua-full-version-list. |
| [UserAgentMetadata](arkts-na-webview-useragentmetadata-c.md) | Holds User-Agent metadata information and uses to generate User-Agent client hints. |
| [WebCookieManager](arkts-na-webview-webcookiemanager-c.md) | Provides methods for managing the web cookies. |
| [WebDataBase](arkts-na-webview-webdatabase-c.md) | Implements a WebDataBase object. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> You must load the Web component before calling the APIs in WebDataBase. &lt;/p&gt; |
| [WebDownloadDelegate](arkts-na-webview-webdownloaddelegate-c.md) | The download state is notified through this delegate. |
| [WebDownloadItem](arkts-na-webview-webdownloaditem-c.md) | Represents a download task, You can use this object to operate the corresponding download task. |
| [WebDownloadManager](arkts-na-webview-webdownloadmanager-c.md) | You can trigger download manually through this interface, or resume failed or canceled downloads. |
| [WebHttpBodyStream](arkts-na-webview-webhttpbodystream-c.md) | The http body stream of the request. |
| [WebMessageExt](arkts-na-webview-webmessageext-c.md) | The message received or sent from web message port. |
| [WebResourceHandler](arkts-na-webview-webresourcehandler-c.md) | Used to intercept url requests. Response headers and body can be sent through WebResourceHandler. |
| [WebSchemeHandler](arkts-na-webview-webschemehandler-c.md) | This class is used to intercept requests for a specified scheme. |
| [WebSchemeHandlerRequest](arkts-na-webview-webschemehandlerrequest-c.md) | Defines the Web resource request used for scheme handler. |
| [WebSchemeHandlerResponse](arkts-na-webview-webschemehandlerresponse-c.md) | Defines the Web resource response used for scheme handler. |
| [WebStorage](arkts-na-webview-webstorage-c.md) | Implements a WebStorage object to manage the Web SQL database and HTML5 Web Storage APIs. All Web components in an application share a WebStorage object. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> You must load the Web component before calling the APIs in WebStorage. &lt;/p&gt; |
| [WebviewController](arkts-na-webview-webviewcontroller-c.md) | WebviewController can control various behaviors of Web components (including page navigation, declaring cycle state, JavaScript interaction and so on). A WebviewController object can only control one Web component, and methods on the Webviewcontroller (except static methods) can only be called after the web component is bound to the WebviewController. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackForwardList](arkts-na-webview-backforwardlist-i.md) | Provides back and forward history list information method. related to [HistoryItem](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-historyitem-i.md). |
| [BlanklessFrameInterpolationInfo](arkts-na-webview-blanklessframeinterpolationinfo-i.md) | Defines the frame interpolation information. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned. |
| [BlanklessInfo](arkts-na-webview-blanklessinfo-i.md) | Defines the blankless information. |
| [BlanklessLoadingParam](arkts-na-webview-blanklessloadingparam-i.md) | Defines the blankless loading parameter. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned. |
| [CacheOptions](arkts-na-webview-cacheoptions-i.md) | Options of generating code cache |
| [HistoryItem](arkts-na-webview-historyitem-i.md) | Provides information for history item in BackForwardList. |
| [HitTestValue](arkts-na-webview-hittestvalue-i.md) | Provides element information of the click area. related to [getLastHitTest](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#getlasthittest) method. |
| [MediaInfo](arkts-na-webview-mediainfo-i.md) | [CreateNativeMediaPlayerCallback](../../../reference/apis-arkweb/arkts-apis-webview-t.md#createnativemediaplayercallback) 回调函数的一个参数。包含了网页中媒体的信息。应用可以根据这些信息来创建接管网页媒体播放的播放器。 |
| [NativeMediaPlayerBridge](arkts-na-webview-nativemediaplayerbridge-i.md) | [CreateNativeMediaPlayerCallback](../../../reference/apis-arkweb/arkts-apis-webview-t.md#createnativemediaplayercallback) 回调函数的返回值类型。接管网页媒体的播放器和ArkWeb内核之间的一个接口类。 ArkWeb内核通过该接口类的实例对象来控制应用创建的用来接管网页媒体的播放器。 |
| [NativeMediaPlayerHandler](arkts-na-webview-nativemediaplayerhandler-i.md) | [CreateNativeMediaPlayerCallback](../../../reference/apis-arkweb/arkts-apis-webview-t.md#createnativemediaplayercallback) 回调函数的参数。应用通过该对象，将播放器的状态通知给 ArkWeb 内核。 |
| [OfflineResourceMap](arkts-na-webview-offlineresourcemap-i.md) | Define offline resource's content and info. |
| [PdfConfiguration](arkts-na-webview-pdfconfiguration-i.md) | Defines the configuration of creating pdf, related to {@Link createPdf} method. |
| [RectEvent](arkts-na-webview-rectevent-i.md) | 矩形定义。 |
| [RequestInfo](arkts-na-webview-requestinfo-i.md) | Defines the Web's request info. |
| [ScrollOffset](arkts-na-webview-scrolloffset-i.md) | Defines the scroll offset of the webpage in view port, the unit is virtual pixel. Related to [getScrollOffset](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#getscrolloffset) method. |
| [SecurityParams](arkts-na-webview-securityparams-i.md) | Defines the parameters for enableAdvancedSecurityMode. |
| [SnapshotInfo](arkts-na-webview-snapshotinfo-i.md) | Defines the snapshot info. |
| [SnapshotResult](arkts-na-webview-snapshotresult-i.md) | Represents a full drawing result. |
| [WebCustomScheme](arkts-na-webview-webcustomscheme-i.md) | Defines the configuration of web custom scheme, related to [customizeSchemes](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#customizeschemes) method. |
| [WebHeader](arkts-na-webview-webheader-i.md) | Defines the Web's request/response header. |
| [WebHttpCookie](arkts-na-webview-webhttpcookie-i.md) | Defines the Web's HTTPCookie. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> The maximum length allowed for each attribute value in a cookie string is 1024. &lt;/p&gt; |
| [WebMessagePort](arkts-na-webview-webmessageport-i.md) | Define html web message port. |
| [WebStorageOrigin](arkts-na-webview-webstorageorigin-i.md) | Provides basic information of web storage. |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArkWebEngineVersion](arkts-na-webview-arkwebengineversion-e.md) | ArkWeb内核版本，请参考 [M114内核在OpenHarmony 6.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md) ， [M132内核在OpenHarmony 7.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md) 。 |
| [BlanklessFrameInterpolationState](arkts-na-webview-blanklessframeinterpolationstate-e.md) | Enumerates the frame interpolation states. &lt;strong&gt;ArkWeb Dual Web Engine Versioning Convention&lt;/strong&gt;: &lt;p&gt;See [ArkWeb Dual Web Engine Versioning Convention] for switching between Legacy and Evergreen Web Engine. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned. |
| [ControllerAttachState](arkts-na-webview-controllerattachstate-e.md) | Enum type supplied to [getAttachState](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#getattachstate) for indicating the attach state of controller. |
| [JsMessageType](arkts-na-webview-jsmessagetype-e.md) | Enum type supplied to [runJavaScriptExt](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) for indicating the result of JavaScript code execution. |
| [MediaError](arkts-na-webview-mediaerror-e.md) | 播放器的错误类型。 |
| [MediaPlaybackState](arkts-na-webview-mediaplaybackstate-e.md) | 当前网页的播控状态。 |
| [MediaType](arkts-na-webview-mediatype-e.md) | 表示媒体类型。 |
| [NetworkState](arkts-na-webview-networkstate-e.md) | 播放器的网络状态。 |
| [OfflineResourceType](arkts-na-webview-offlineresourcetype-e.md) | Enum type supplied to [OfflineResourceMap](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-offlineresourcemap-i.md) for indicating the type of resource. |
| [PlaybackStatus](arkts-na-webview-playbackstatus-e.md) | [handleStatusChanged](../../../reference/apis-arkweb/arkts-apis-webview-NativeMediaPlayerHandler.md#handlestatuschanged) 接口参数， 用于表示播放器的播放状态。 |
| [Preload](arkts-na-webview-preload-e.md) | 播放器预加载媒体数据。 |
| [PressureLevel](arkts-na-webview-pressurelevel-e.md) | The memory pressure level that can be set. |
| [ProxySchemeFilter](arkts-na-webview-proxyschemefilter-e.md) | Enum type supplied to [insertProxyRule](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-proxyconfig-c.md#insertproxyrule) for indicating the scheme filter for proxy. |
| [ReadyState](arkts-na-webview-readystate-e.md) | 播放器的缓存状态。 |
| [RenderProcessMode](arkts-na-webview-renderprocessmode-e.md) | Defines the render process mode. |
| [ScrollType](arkts-na-webview-scrolltype-e.md) | Enum type supplied to [setScrollable](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#setscrollable) for indicating the type of scroll. |
| [ScrollbarMode](arkts-na-webview-scrollbarmode-e.md) | Enum type supplied to [setScrollbarMode](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#setscrollbarmode) for indicating the web component scrollbar mode. |
| [SecureDnsMode](arkts-na-webview-securednsmode-e.md) | Defines the mode for using HttpDns. |
| [SecurityLevel](arkts-na-webview-securitylevel-e.md) | Defines the security level for the page. |
| [SiteIsolationMode](arkts-na-webview-siteisolationmode-e.md) | Indicates the site isolation mode of the application, default value depends on different devices type. |
| [SourceType](arkts-na-webview-sourcetype-e.md) | 表示媒体源的类型。 |
| [SuspendType](arkts-na-webview-suspendtype-e.md) | 表示播放器的挂起类型。 |
| [UserAgentFormFactor](arkts-na-webview-useragentformfactor-e.md) | The form factors for User-Agent metadata. |
| [WebBlanklessErrorCode](arkts-na-webview-webblanklesserrorcode-e.md) | Enumerates the error codes of blankless. For details, see [setBlanklessLoadingWithKey](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#setblanklessloadingwithkey) or [BlanklessInfo](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-blanklessinfo-i.md). |
| [WebDestroyMode](arkts-na-webview-webdestroymode-e.md) | Enum type supplied to SetWebDestroyMode for indicating the web component destroy mode. |
| [WebDownloadErrorCode](arkts-na-webview-webdownloaderrorcode-e.md) | Defines the error code for download. |
| [WebDownloadState](arkts-na-webview-webdownloadstate-e.md) | Defines the state for download. |
| [WebHitTestType](arkts-na-webview-webhittesttype-e.md) | Enum type supplied to [getHitTest](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#gethittest) for indicating the cursor node HitTest. |
| [WebHttpCookieSameSitePolicy](arkts-na-webview-webhttpcookiesamesitepolicy-e.md) | Indicates whether to restrict cookies so that only requests sent back to the same site that created them can carry them. |
| [WebMessageType](arkts-na-webview-webmessagetype-e.md) | Enum type supplied to [onMessageEventExt](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webmessageport-i.md#onmessageeventext) for indicating the type of web message. |
| [WebResourceType](arkts-na-webview-webresourcetype-e.md) | Defines the resource type of request. |
| [WebSoftKeyboardBehaviorMode](arkts-na-webview-websoftkeyboardbehaviormode-e.md) | Indicates the keyboard behavior mode of the web component, default value is DEFAULT. |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CreateNativeMediaPlayerCallback](arkts-na-webview-createnativemediaplayercallback-t.md) | [onCreateNativeMediaPlayer](../../../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer) 方法的参数。一个回调函数，创建一个播放器，用于接管网页中的媒体播放。 |
| [OnProxyConfigChangeCallback](arkts-na-webview-onproxyconfigchangecallback-t.md) | The callback for proxy changed. |
| [OneParamFn](arkts-na-webview-oneparamfn-t.md) | The function with one parameter. |
| [ResumePlayerFn](arkts-na-webview-resumeplayerfn-t.md) | The function of reusme media play. |
| [SuspendPlayerFn](arkts-na-webview-suspendplayerfn-t.md) | The function of suspend media play. |
| [UpdateRectFn](arkts-na-webview-updaterectfn-t.md) | The function of the rect of video tag has changed. |
| [WebMessage](arkts-na-webview-webmessage-t.md) | WebMessage type supplied to [onMessageEventExt](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webmessageport-i.md#onmessageeventext) for indicating the type of web message. |
| [ZeroParamFn](arkts-na-webview-zeroparamfn-t.md) | The function with zero parameter. |

