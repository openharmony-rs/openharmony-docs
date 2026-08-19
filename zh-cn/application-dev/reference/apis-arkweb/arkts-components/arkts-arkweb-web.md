# Web

定义 Web 组件。 <p><strong>API Note</strong>: <strong>Performance Note</strong>: <p>For details about how to optimize the compilation, resource loading, and JSBridge performance, see Optimizing Web Page Loading <p>When the white screen duration is long due to complex web page parsing, you can enable [optimizeParserBudget](arkts-arkweb-web-attribute.md#optimizeparserbudget) to reduce the first frame rendering content.</p> </p>

## Web

```TypeScript
Web(value: WebOptions)
```

Sets Value. > **说明：** > > - 在HTML5侧，调用console.log或console.info对应ConsoleMessage的信息级别都为MessageLevel.Info。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebInterface-(value: WebOptions): WebAttribute--><!--Device-WebInterface-(value: WebOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [WebOptions](arkts-arkweb-weboptions-i.md) | 是 | Web组件的初始化配置选项，用于设置加载的网页资源（src）、绑定的控制器（controller）以及渲染模式等行为参数。具体属性结构请参考WebOptions接口定义。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AcceptableFileType](arkts-arkweb-acceptablefiletype-i.md) | 提供文件选择器推荐的文件类型信息，包括MIME类型和类型数组。 |
| [AdsBlockedDetails](arkts-arkweb-adsblockeddetails-i.md) | 发生广告拦截时，广告资源信息。 |
| [AISessionEvent](arkts-arkweb-aisessionevent-i.md) | 自定义AI会话配置对象，用于定义AI会话的生命周期回调，包括创建、执行和销毁。 |
| [BlankScreenDetails](arkts-arkweb-blankscreendetails-i.md) | 提供检测到白屏时的结果细节，包括有内容节点数量。适用于需要分析白屏原因的场景，提升白屏诊断的详细性和准确性。 |
| [BlankScreenDetectionConfig](arkts-arkweb-blankscreendetectionconfig-i.md) | 提供白屏检测的策略配置选项，包括检测时机、方法和阈值。适用于需要自定义白屏检测行为的场景，提升白屏监控的灵活性和准确性。 |
| [BlankScreenDetectionEventInfo](arkts-arkweb-blankscreendetectioneventinfo-i.md) | 提供检测到白屏时的事件信息，包括URL、原因和细节。适用于需要监控页面白屏问题的场景，提升白屏诊断的准确性和用户体验。 |
| [CameraCaptureStateChangeInfo](arkts-arkweb-cameracapturestatechangeinfo-i.md) | 提供摄像头触发回调时的状态变化信息，包括改变前的状态和新状态。适用于需要监控摄像头状态变化的场景，提升摄像头管理的可见性和用户体验。 |
| [EmbedOptions](arkts-arkweb-embedoptions-i.md) | Web同层渲染的配置。用于配置Web同层渲染选项，包括支持固定大小和CSS显示属性。适用于需要优化同层元素渲染效果的场景，提升渲染的兼容性和灵活性。 |
| [ExpandedMenuItemOptions](arkts-arkweb-expandedmenuitemoptions-i.md) | 自定义菜单扩展项。 |
| [FirstMeaningfulPaint](arkts-arkweb-firstmeaningfulpaint-i.md) | 提供网页绘制页面主要内容的详细信息，包括导航时间和绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [FirstScreenPaint](arkts-arkweb-firstscreenpaint-i.md) | 提供首屏渲染事件的信息，包括URL和绘制时间。适用于需要监控页面首屏渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [FullScreenEnterEvent](arkts-arkweb-fullscreenenterevent-i.md) | 提供 Web 组件进入全屏的回调信息，包括视频尺寸和退出句柄。适用于需要处理全屏视频的场景，提升视频播放的沉浸式体验和可控性。 |
| [Header](arkts-arkweb-header-i.md) | Web组件返回的请求/响应头对象。适用于需要读取或修改HTTP头的场景，提升网络请求处理的灵活性和可控性。 |
| [IntelligentTrackingPreventionDetails](arkts-arkweb-intelligenttrackingpreventiondetails-i.md) | 提供智能防跟踪拦截的详细信息，包括网站域名和追踪者域名。适用于需要监控广告拦截行为的场景，提升隐私保护的透明度和可控性。 |
| [JavaScriptProxy](arkts-arkweb-javascriptproxy-i.md) | 定义要注入的JavaScript对象，包括对象名、方法列表和权限配置。适用于需要实现JavaScript与原生交互的场景，提升跨语言调用的灵活性和安全性。 |
| [LargestContentfulPaint](arkts-arkweb-largestcontentfulpaint-i.md) | 提供网页绘制页面最大内容的详细信息，包括导航时间和各类绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [LoadCommittedDetails](arkts-arkweb-loadcommitteddetails-i.md) | 提供已提交跳转的网页详细信息，包括是否主文档、导航类型等。适用于需要监控页面导航行为的场景，提升导航状态管理的准确性和用户体验。 |
| [MicrophoneCaptureStateChangeInfo](arkts-arkweb-microphonecapturestatechangeinfo-i.md) | 提供麦克风触发回调时的状态变化信息，包括改变前的状态和改变后的状态。适用于需要监控麦克风状态变化的场景，提升麦克风管理的可见性和用户体验。 |
| [NativeEmbedDataInfo](arkts-arkweb-nativeembeddatainfo-i.md) | 提供同层标签生命周期变化的详细信息，包括状态和标签信息。适用于需要监控同层元素生命周期的场景，提升渲染状态管理的准确性和用户体验。 |
| [NativeEmbedInfo](arkts-arkweb-nativeembedinfo-i.md) | 提供同层标签的详细信息，包括ID、类型、尺寸和位置等。适用于需要获取同层元素属性的场景，提升同层渲染的定制性和用户体验。 |
| [NativeEmbedMouseInfo](arkts-arkweb-nativeembedmouseinfo-i.md) | 提供鼠标/触摸板在同层标签上点击或长按的详细信息，包括标签ID和鼠标事件。适用于需要处理同层元素鼠标交互的场景，提升鼠标体验的定制性和灵活性。 |
| [NativeEmbedParamDataInfo](arkts-arkweb-nativeembedparamdatainfo-i.md) | 提供同层渲染object标签内嵌param元素变化时同层标签的详细信息，包括标签ID和参数项。适用于需要监控param元素变化的场景，提升同层元素管理的灵活性和准确性。 |
| [NativeEmbedParamItem](arkts-arkweb-nativeembedparamitem-i.md) | 提供同层渲染object标签内嵌param元素的详细信息，包括状态和参数。适用于需要监控param元素变化的场景，提升同层元素管理的灵活性和准确性。 |
| [NativeEmbedTouchInfo](arkts-arkweb-nativeembedtouchinfo-i.md) | 提供手指触摸同层标签的详细信息，包括标签ID和触摸事件。适用于需要处理同层元素触摸交互的场景，提升触摸体验的定制性和灵活性。 |
| [NativeEmbedVisibilityInfo](arkts-arkweb-nativeembedvisibilityinfo-i.md) | 提供同层标签的可见性信息，包括可见状态和标签ID。适用于需要监控同层元素可见性的场景，提升渲染状态管理的准确性和用户体验。 |
| [NativeMediaPlayerConfig](arkts-arkweb-nativemediaplayerconfig-i.md) | 用于配置应用接管网页媒体播放功能接口[enableNativeMediaPlayer](arkts-arkweb-web-attribute.md#enablenativemediaplayer)的功能，支持是否开启及是否覆盖网页内容。适用于需要自定义媒体 播放行为的场景，提升媒体播放的集成度和用户体验。 |
| [NestedScrollOptionsExt](arkts-arkweb-nestedscrolloptionsext-i.md) | 用于设置Web组件嵌套滚动规则，支持上下左右四个方向的滚动选项。 |
| [OnAlertEvent](arkts-arkweb-onalertevent-i.md) | 定义网页触发 `alert()` 告警时的回调函数。 |
| [OnAudioStateChangedEvent](arkts-arkweb-onaudiostatechangedevent-i.md) | 定义网页音频播放状态改变时触发的回调信息，包括播放状态。适用于需要监控音频播放行为的场景，提升音频管理的可见性和用户体验。 |
| [OnBeforeUnloadEvent](arkts-arkweb-onbeforeunloadevent-i.md) | 定义刷新或关闭场景下，在即将离开当前页面时触发此回调。适用于表单编辑等场景，允许开发者拦截离开动作并弹窗确认，从而避免用户未提交的数据意外丢失。 |
| [OnClientAuthenticationEvent](arkts-arkweb-onclientauthenticationevent-i.md) | 定义需要提供SSL客户端证书时触发的回调信息，包括主机、端口和密钥类型。适用于需要处理客户端证书认证的场景，提升认证流程的灵活性和安全性。 |
| [OnConfirmEvent](arkts-arkweb-onconfirmevent-i.md) | 定义网页触发 `confirm()` 弹窗时的回调函数。 |
| [OnConsoleEvent](arkts-arkweb-onconsoleevent-i.md) | 定义通知宿主应用JavaScript console消息。 |
| [OnContextMenuShowEvent](arkts-arkweb-oncontextmenushowevent-i.md) | 定义调用时触发的回调信息，以允许自定义显示上下文菜单。 |
| [OnDataResubmittedEvent](arkts-arkweb-ondataresubmittedevent-i.md) | 定义网页表单可以重新提交时触发的回调信息，包括提交句柄。适用于需要处理表单重试提交的场景，提升表单交互的可靠性和用户体验。 |
| [OnDownloadStartEvent](arkts-arkweb-ondownloadstartevent-i.md) | 定义通知主应用开始下载文件的回调信息，包括URL、用户代理和文件详情。适用于需要监控和管理文件下载的场景，提升下载流程的可控性和用户体验。 |
| [OnErrorReceiveEvent](arkts-arkweb-onerrorreceiveevent-i.md) | 定义网页加载遇到错误时触发的回调信息，包括请求和错误详情。适用于需要监控和处理网页加载错误的场景，提升错误处理的及时性和用户体验。 |
| [OnFaviconReceivedEvent](arkts-arkweb-onfaviconreceivedevent-i.md) | 定义应用接收到新favicon时触发的回调信息，包括图标PixelMap对象。适用于需要获取网页favicon的场景，提升图标管理的灵活性和用户体验。 |
| [OnFirstContentfulPaintEvent](arkts-arkweb-onfirstcontentfulpaintevent-i.md) | 定义网页首次内容绘制的回调信息，包括加载时间和绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [OnGeolocationShowEvent](arkts-arkweb-ongeolocationshowevent-i.md) | 定义收到地理位置获取请求时触发的回调信息，包括源信息和地理对象。适用于需要处理地理位置权限的场景。 |
| [OnHttpAuthRequestEvent](arkts-arkweb-onhttpauthrequestevent-i.md) | 定义收到HTTP认证请求时触发的回调信息，包括主机和域信息。适用于需要处理HTTP身份验证的场景，提升认证流程的灵活性和安全性。 |
| [OnHttpErrorReceiveEvent](arkts-arkweb-onhttperrorreceiveevent-i.md) | 定义网页收到资源加载HTTP错误时触发的回调信息，包括请求和响应详情。适用于需要监控和处理HTTP错误的场景，提升网络错误诊断的准确性和用户体验。 |
| [OnInterceptRequestEvent](arkts-arkweb-oninterceptrequestevent-i.md) | 定义Web组件加载URL之前触发的回调信息，包括请求详情。适用于需要拦截或修改网络请求的场景，提升请求控制的灵活性和安全性。 |
| [OnLoadFinishedEvent](arkts-arkweb-onloadfinishedevent-i.md) | 定义网页加载结束时触发的回调信息，包括页面URL。适用于需要监控页面加载完成的场景，提升页面生命周期的管理能力。 |
| [OnLoadInterceptEvent](arkts-arkweb-onloadinterceptevent-i.md) | 定义截获资源加载时触发的回调信息，包括请求详情。适用于需要拦截或处理资源加载的场景，提升资源控制的灵活性和安全性。 |
| [OnLoadStartedEvent](arkts-arkweb-onloadstartedevent-i.md) | 定义网页加载开始时触发的回调信息，包括页面URL。适用于需要监控页面加载开始的场景，提升页面生命周期的管理能力。 |
| [OnOverScrollEvent](arkts-arkweb-onoverscrollevent-i.md) | 定义网页过度滚动时触发的回调信息，包括水平和垂直偏移量。 |
| [OnPageBeginEvent](arkts-arkweb-onpagebeginevent-i.md) | 定义网页加载开始时触发的回调信息，包括页面URL。适用于需要监控页面加载开始的场景，提升页面生命周期的管理能力。 |
| [OnPageEndEvent](arkts-arkweb-onpageendevent-i.md) | 定义网页加载结束时触发的回调信息，包括页面URL。适用于需要监控页面加载完成的场景，提升页面生命周期的管理能力。 |
| [OnPageVisibleEvent](arkts-arkweb-onpagevisibleevent-i.md) | 定义旧页面不再呈现，新页面即将可见时触发的回调函数。 |
| [OnPdfLoadEvent](arkts-arkweb-onpdfloadevent-i.md) | 定义PDF加载成功或失败时触发的函数。 |
| [OnPdfScrollEvent](arkts-arkweb-onpdfscrollevent-i.md) | 定义PDF页面滚动到底时触发的回调函数。 |
| [OnPermissionRequestEvent](arkts-arkweb-onpermissionrequestevent-i.md) | 定义收到权限请求时触发的回调信息，包括请求详情。适用于需要处理权限授予的场景，提升权限管理的灵活性和安全性。 |
| [OnProgressChangeEvent](arkts-arkweb-onprogresschangeevent-i.md) | 定义网页加载进度变化时触发的回调信息，包括新的进度值。适用于需要监控页面加载进度的场景，提升加载过程的可见性和用户体验。 |
| [OnPromptEvent](arkts-arkweb-onpromptevent-i.md) | 定义网页触发 `prompt()` 弹窗时的回调函数。 |
| [OnRefreshAccessedHistoryEvent](arkts-arkweb-onrefreshaccessedhistoryevent-i.md) | 定义导航完成时触发的回调信息，包括URL和刷新状态。适用于需要监控页面导航历史的场景，提升导航行为跟踪的准确性和用户体验。 |
| [OnRenderExitedEvent](arkts-arkweb-onrenderexitedevent-i.md) | 定义渲染过程退出时触发。适用于需要监控渲染进程异常的场景，提升渲染稳定性和故障排查效率。 |
| [OnResourceLoadEvent](arkts-arkweb-onresourceloadevent-i.md) | 定义加载URL时触发的回调信息，包括资源URL。适用于需要监控资源加载行为的场景，提升资源管理的可见性和性能优化。 |
| [OnScaleChangeEvent](arkts-arkweb-onscalechangeevent-i.md) | 定义当前页面显示比例的变化时触发。 |
| [OnScreenCaptureRequestEvent](arkts-arkweb-onscreencapturerequestevent-i.md) | 定义收到屏幕捕获请求时触发的回调信息。适用于需要处理屏幕录制权限的场景，提升录屏流程的可控性和安全性。 |
| [OnScrollEvent](arkts-arkweb-onscrollevent-i.md) | 定义滚动条滑动到指定位置时触发的回调信息，包括水平和垂直偏移量。 |
| [OnSearchResultReceiveEvent](arkts-arkweb-onsearchresultreceiveevent-i.md) | 定义网页页内查找结果的回调信息，包括匹配项序号和总数。适用于需要监控页内搜索行为的场景，提升搜索交互的可见性和用户体验。 |
| [OnShowFileSelectorEvent](arkts-arkweb-onshowfileselectorevent-i.md) | 定义文件选择器结果的回调信息，包括结果和参数详情。 |
| [OnSslErrorEventReceiveEvent](arkts-arkweb-onsslerroreventreceiveevent-i.md) | 定义网页收到SSL错误时触发的回调信息，包括错误码和证书链。适用于需要处理SSL错误的场景，提升安全异常的监控和处理能力。 |
| [OnTitleReceiveEvent](arkts-arkweb-ontitlereceiveevent-i.md) | 定义网页标题更改时触发的回调信息，包括标题内容和来源。适用于需要监控页面标题变化的场景，提升页面信息的实时性和用户体验。 |
| [OnTouchIconUrlReceivedEvent](arkts-arkweb-ontouchiconurlreceivedevent-i.md) | 定义接收到apple-touch-icon URL时触发的回调信息，包括URL和预合成状态。适用于需要获取网页图标的场景，提升图标管理的灵活性和用户体验。 |
| [OnWindowNewEvent](arkts-arkweb-onwindownewevent-i.md) | 定义网页要求用户创建窗口时触发的回调。从API version 23开始，如需获取更多窗口信息，可使用[OnWindowNewExtEvent](arkts-arkweb-onwindownewextevent-i.md)。 |
| [OnWindowNewExtEvent](arkts-arkweb-onwindownewextevent-i.md) | 定义网页请求创建窗口时触发的回调信息，包括窗口特征信息和窗口打开方式。适用于需要精细控制新窗口行为的场景，提升窗口管理的定制性和用户体验。 |
| [PreviewMenuOptions](arkts-arkweb-previewmenuoptions-i.md) | 用于配置预览菜单选项，支持设置菜单弹出时的振动效果。适用于需要增强菜单交互反馈的场景，提升用户体验。 |
| [RenderProcessNotRespondingData](arkts-arkweb-renderprocessnotrespondingdata-i.md) | 提供渲染进程无响应的详细信息。适用于需要诊断渲染进程异常的场景，提升故障排查的准确性和效率。 |
| [ScreenCaptureConfig](arkts-arkweb-screencaptureconfig-i.md) | 提供 Web 屏幕捕获的配置选项，包括捕获模式。适用于需要自定义网页录屏行为的场景，提升录屏功能的灵活性和用户体验。 |
| [ScriptItem](arkts-arkweb-scriptitem-i.md) | 通过[javaScriptOnDocumentStart](arkts-arkweb-web-attribute.md#javascriptondocumentstart)属性注入到Web组件的ScriptItem对象。 |
| [SelectionMenuOptionsExt](arkts-arkweb-selectionmenuoptionsext-i.md) | 自定义菜单扩展项。 |
| [SslErrorEvent](arkts-arkweb-sslerrorevent-i.md) | 用户加载资源时发生SSL错误时触发的回调详情，包括URL、错误类型和证书链。适用于需要详细分析SSL错误的场景，提升安全问题的诊断和排查效率。 |
| [UrlRegexRule](arkts-arkweb-urlregexrule-i.md) | 定义Url正则表达式规则。 |
| [VerifyPinEvent](arkts-arkweb-verifypinevent-i.md) | 定义当需要用户进行PIN码认证时触发回调。 |
| [WebKeyboardCallbackInfo](arkts-arkweb-webkeyboardcallbackinfo-i.md) | 拦截网页可编辑元素拉起软键盘的回调入参，包括WebKeyboardController和可编辑元素的属性。适用于需要自定义键盘交互的场景，提升输入体验的定制性和灵活性。 |
| [WebKeyboardOptions](arkts-arkweb-webkeyboardoptions-i.md) | 拦截网页可编辑元素拉起软键盘的回调返回值，包括键盘类型和自定义键盘。适用于需要控制软键盘行为的场景。 |
| [WebMediaOptions](arkts-arkweb-webmediaoptions-i.md) | 用于配置 Web 组件的媒体策略，包括音频续播有效期、音频独占模式等。适用于需要优化音频播放体验和多实例音频管理的场景，提升媒体播放的稳定性和用户体验。 |
| [WebOptions](arkts-arkweb-weboptions-i.md) | 通过[接口](../../../reference/apis-arkweb/arkts-basic-components-web.md#接口)定义Web选项，包括网页资源地址、控制器、渲染方式等。 |
| [WindowFeatures](arkts-arkweb-windowfeatures-i.md) | 提供网页请求创建的新窗口特征信息，包括大小和位置。适用于需要精确控制新窗口属性的场景，提升窗口布局的准确性和用户体验。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [MouseInfoCallback](arkts-arkweb-mouseinfocallback-t.md) | 当鼠标/触摸板单击到同层标签时触发此回调。 |
| [OnAdsBlockedCallback](arkts-arkweb-onadsblockedcallback-t.md) | 当页面发生广告过滤时触发此回调。 |
| [OnAISessionCallback](arkts-arkweb-onaisessioncallback-t.md) | AI会话操作结果回调函数类型。用于报告会话创建或执行的结果。 |
| [OnCameraCaptureStateChangeCallback](arkts-arkweb-oncameracapturestatechangecallback-t.md) | 当页面摄像设备状态发生改变时触发此回调。 |
| [OnContextMenuHideCallback](arkts-arkweb-oncontextmenuhidecallback-t.md) | 上下文菜单自定义隐藏的回调。 |
| [OnCreateAISession](arkts-arkweb-oncreateaisession-t.md) | AI会话创建回调函数类型。允许自定义模型初始化和结果处理。 |
| [OnDestroyAISession](arkts-arkweb-ondestroyaisession-t.md) | AI会话销毁回调函数类型。用于清理与自定义AI模型关联的资源。 |
| [OnDetectBlankScreenCallback](arkts-arkweb-ondetectblankscreencallback-t.md) | 检测到白屏时触发此回调。 |
| [OnExecuteAIAction](arkts-arkweb-onexecuteaiaction-t.md) | AI会话执行操作回调函数类型。用于自定义实现AI模型执行。 |
| [OnFirstMeaningfulPaintCallback](arkts-arkweb-onfirstmeaningfulpaintcallback-t.md) | 网页首次绘制页面主要内容度量的回调，当网页加载完页面主要内容时会触发此回调。与OnLargestContentfulPaintCallback关注最大内容元素绘制时间、OnFirstScreenPaintCallback关注首屏可见内 容渲染完成相比，本回调更关注主要内容是否加载完成，适合评估用户可见内容的加载体验。 |
| [OnFirstScreenPaintCallback](arkts-arkweb-onfirstscreenpaintcallback-t.md) | 检测到首屏渲染结束时会触发此回调。与OnFirstMeaningfulPaintCallback关注主要内容加载完成、OnLargestContentfulPaintCallback关注最大内容元素绘制时间相比，本回调更关注首屏可见内 容的渲染完成时间，适合评估用户首次视觉体验。 |
| [OnFullScreenEnterCallback](arkts-arkweb-onfullscreenentercallback-t.md) | Web组件进入全屏时触发的回调。 |
| [OnInputmethodAttachedCallback](arkts-arkweb-oninputmethodattachedcallback-t.md) | 当检测到输入法绑定成功时，会触发此回调。 |
| [OnIntelligentTrackingPreventionCallback](arkts-arkweb-onintelligenttrackingpreventioncallback-t.md) | 当跟踪者cookie被拦截时触发的回调。 |
| [OnLargestContentfulPaintCallback](arkts-arkweb-onlargestcontentfulpaintcallback-t.md) | 当网页绘制最大内容区域时触发的回调，用于获取最大内容绘制的性能度量信息。适用于需要监控网页加载性能、优化页面渲染速度等场景。与OnFirstMeaningfulPaintCallback关注主要内容加载完成、 OnFirstScreenPaintCallback关注首屏可见内容渲染完成相比，本回调关注最大内容元素的绘制时间，适合评估页面渲染完成度和性能瓶颈。 |
| [OnMicrophoneCaptureStateChangeCallback](arkts-arkweb-onmicrophonecapturestatechangecallback-t.md) | 当页面麦克风状态发生改变时触发此回调。 |
| [OnNativeEmbedObjectParamChangeCallback](arkts-arkweb-onnativeembedobjectparamchangecallback-t.md) | 增加、修改或删除同层渲染object标签内嵌param元素时触发此回调。 |
| [OnNativeEmbedVisibilityChangeCallback](arkts-arkweb-onnativeembedvisibilitychangecallback-t.md) | 当同层标签可见性变化时触发该回调。 |
| [OnNavigationEntryCommittedCallback](arkts-arkweb-onnavigationentrycommittedcallback-t.md) | 导航条目提交时触发的回调。 |
| [OnOverrideErrorPageCallback](arkts-arkweb-onoverrideerrorpagecallback-t.md) | onOverrideErrorPage的回调函数，网页加载失败时触发。 |
| [OnOverrideUrlLoadingCallback](arkts-arkweb-onoverrideurlloadingcallback-t.md) | 用于拦截URL加载请求的回调，可阻止特定URL的加载或进行自定义处理。适用于需要拦截广告、阻止恶意网站跳转等场景。 |
| [OnRenderProcessNotRespondingCallback](arkts-arkweb-onrenderprocessnotrespondingcallback-t.md) | 渲染进程无响应时触发的回调。 |
| [OnRenderProcessRespondingCallback](arkts-arkweb-onrenderprocessrespondingcallback-t.md) | 渲染进程由无响应状态变回正常运行状态时触发该回调。 |
| [OnSafeBrowsingCheckResultCallback](arkts-arkweb-onsafebrowsingcheckresultcallback-t.md) | 网站安全风险检查触发的回调。 |
| [OnSslErrorEventCallback](arkts-arkweb-onsslerroreventcallback-t.md) | 用户加载资源时发生SSL错误时触发的回调，返回SSL错误详细信息。 |
| [OnVerifyPinCallback](arkts-arkweb-onverifypincallback-t.md) | 需要用户进行PIN码认证时触发的回调。 |
| [OnViewportFitChangedCallback](arkts-arkweb-onviewportfitchangedcallback-t.md) | 网页meta中viewport-fit配置项更改时触发的回调。 |
| [TextSelectionChangeCallback](arkts-arkweb-textselectionchangecallback-t.md) | onTextSelectionChange的回调，选区内容改变时触发。 |
| [WebKeyboardCallback](arkts-arkweb-webkeyboardcallback-t.md) | 拦截网页可编辑元素拉起软键盘的回调，一般在点击网页input标签时触发。 |
| [WebviewController](arkts-arkweb-webviewcontroller-t.md) | 提供Web控制器的方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AISessionResultType](arkts-arkweb-aisessionresulttype-e.md) | AI会话操作的结果状态。 |
| [AISessionType](arkts-arkweb-aisessiontype-e.md) | 支持的AI会话类型。 |
| [AudioSessionType](arkts-arkweb-audiosessiontype-e.md) | 应用中 Web 音频类型，用于控制 Web 音频的音频流类型和行为，帮助开发者根据应用场景优化音频体验，如支持网页游戏声音与系统音乐同时播放。 |
| [BlankScreenDetectionMethod](arkts-arkweb-blankscreendetectionmethod-e.md) | 白屏检测使用的检测策略的方法，用于定义页面内容检测的具体算法和点位，帮助开发者在检测准确性和性能开销之间取得平衡，及时发现页面渲染异常。 |
| [BlurOnKeyboardHideMode](arkts-arkweb-bluronkeyboardhidemode-e.md) | 设置手动收起软键盘时Web元素是否失焦。 |
| [CacheMode](arkts-arkweb-cachemode-e.md) | 缓存模式。 |
| [CameraCaptureState](arkts-arkweb-cameracapturestate-e.md) | 定义摄像头使用状态的值，用于标识摄像头的当前工作状态，帮助开发者实时监控摄像头资源使用情况，优化资源管理和用户隐私保护。 |
| [ConsoleMessageSource](arkts-arkweb-consolemessagesource-e.md) | ConsoleMessage的日志来源。 |
| [ContextMenuDataMediaType](arkts-arkweb-contextmenudatamediatype-e.md) | 触发上下文菜单的网页元素类型（增强获取类型能力）。 |
| [ContextMenuEditStateFlags](arkts-arkweb-contextmenueditstateflags-e.md) | 支持以按位或的方式使用此枚举。例如，如果需要同时支持CAN_CUT、CAN_COPY和CAN_SELECT_ALL，可使用CAN_CUT | CAN_COPY | CAN_SELECT_ALL或11。 |
| [ContextMenuInputFieldType](arkts-arkweb-contextmenuinputfieldtype-e.md) | 输入框类型。 |
| [ContextMenuMediaType](arkts-arkweb-contextmenumediatype-e.md) | 触发上下文菜单的网页元素类型。 |
| [ContextMenuSourceType](arkts-arkweb-contextmenusourcetype-e.md) | 触发上下文菜单的事件来源。 |
| [CredentialType](arkts-arkweb-credentialtype-e.md) | 凭证类型，用于定义身份认证中使用的凭证种类。 |
| [DetectedBlankScreenReason](arkts-arkweb-detectedblankscreenreason-e.md) | 白屏的具体原因，用于标识页面白屏现象的底层原因，帮助开发者快速定位问题来源，提升页面加载问题的排查效率和用户体验。 |
| [FileSelectorMode](arkts-arkweb-fileselectormode-e.md) | 文件选择器的模式，用于控制文件选择器的打开方式和行为，帮助开发者实现文件上传等文件操作场景。 |
| [GestureFocusMode](arkts-arkweb-gesturefocusmode-e.md) | 手势获焦的模式。 |
| [HitTestType](arkts-arkweb-hittesttype-e.md) | 点击事件检测结果类型。 |
| [MessageLevel](arkts-arkweb-messagelevel-e.md) | ConsoleMessage的信息级别。 |
| [MicrophoneCaptureState](arkts-arkweb-microphonecapturestate-e.md) | 定义麦克风使用状态的值，用于标识麦克风的当前工作状态，帮助开发者实时监控麦克风资源使用情况，优化资源管理和用户隐私保护。 |
| [MixedMode](arkts-arkweb-mixedmode-e.md) | 混合内容模式。 |
| [NativeEmbedParamStatus](arkts-arkweb-nativeembedparamstatus-e.md) | 定义同层渲染object标签内嵌param元素的状态变化类型，当添加param元素时触发ADD，修改param元素属性触发UPDATE，删除param元素触发DELETE。 |
| [NativeEmbedStatus](arkts-arkweb-nativeembedstatus-e.md) | 定义同层标签生命周期，当加载页面中有同层标签会触发CREATE，同层标签移动或者放大会触发UPDATE，退出页面会触发DESTROY。 |
| [NavigationPolicy](arkts-arkweb-navigationpolicy-e.md) | WebView中新窗口的打开方式，支持弹窗、新窗口、前台和后台标签页等多种方式。 |
| [OverScrollMode](arkts-arkweb-overscrollmode-e.md) | 设置Web的过滚动模式为关闭或开启。 |
| [PdfLoadResult](arkts-arkweb-pdfloadresult-e.md) | 定义PDF页面的加载结果，用于标识PDF文件加载过程中的各种状态和错误类型，帮助开发者在PDF显示失败时进行错误诊断和用户提示。 |
| [PinVerifyResult](arkts-arkweb-pinverifyresult-e.md) | PIN码认证结果，用于标识PIN码验证的执行状态。 |
| [ProtectedResourceType](arkts-arkweb-protectedresourcetype-e.md) | ProtectedResourceType 枚举定义了 Web 组件需要访问的受保护资源类型，用于控制MIDI、相机、麦克风、传感器等敏感资源的访问权限，帮助开发者在保护用户隐私的同时提供丰富的 Web 功能。 |
| [RenderExitReason](arkts-arkweb-renderexitreason-e.md) | onRenderExited接口返回的渲染进程退出的具体原因。 |
| [RenderMode](arkts-arkweb-rendermode-e.md) | 定义Web组件的渲染方式，默认为异步渲染模式。 建议使用异步渲染模式，异步渲染模式有更好的性能和更低的功耗。 |
| [RenderProcessNotRespondingReason](arkts-arkweb-renderprocessnotrespondingreason-e.md) | 触发渲染进程无响应回调的原因。 |
| [ScrollbarLayoutPolicy](arkts-arkweb-scrollbarlayoutpolicy-e.md) | 定义滚动条布局模式控制参数的枚举类型。 |
| [ScrollDirectionalLockType](arkts-arkweb-scrolldirectionallocktype-e.md) | 定义滑动方向锁定的场景类型。 |
| [SslError](arkts-arkweb-sslerror-e.md) | onSslErrorEventReceive接口返回的SSL错误的具体原因。 |
| [ThreatType](arkts-arkweb-threattype-e.md) | 定义网站风险类型。 |
| [ViewportFit](arkts-arkweb-viewportfit-e.md) | 网页meta中viewport-fit配置的视口类型。 |
| [WebBypassVsyncCondition](arkts-arkweb-webbypassvsynccondition-e.md) | 跳过渲染vsync条件。 |
| [WebCaptureMode](arkts-arkweb-webcapturemode-e.md) | Web屏幕捕获模式。 |
| [WebDarkMode](arkts-arkweb-webdarkmode-e.md) | Web深色模式的配置，用于控制网页内容的深色主题显示，帮助开发者根据用户偏好和系统主题提升视觉体验和可读性。 |
| [WebElementType](arkts-arkweb-webelementtype-e.md) | 网页元素信息。 |
| [WebKeyboardAppearanceMode](arkts-arkweb-webkeyboardappearancemode-e.md) | WebView中输入法沉浸模式，用于控制软键盘的显示风格，帮助开发者根据应用主题和用户偏好提供一致性的视觉体验，支持默认外观、系统跟随、浅色和深色沉浸式风格。 |
| [WebKeyboardAvoidMode](arkts-arkweb-webkeyboardavoidmode-e.md) | 软键盘避让的模式。 |
| [WebLayoutMode](arkts-arkweb-weblayoutmode-e.md) | Web布局模式的配置，用于控制Web内容的页面布局方式，帮助开发者根据屏幕尺寸和显示需求优化网页的适配性和用户体验。 |
| [WebNavigationType](arkts-arkweb-webnavigationtype-e.md) | 定义navigation类型。 |
| [WebResponseType](arkts-arkweb-webresponsetype-e.md) | 菜单的响应类型。 |
| [WebRotateEffect](arkts-arkweb-webrotateeffect-e.md) | 组件旋转时，宽高动画过程中组件内容如何填充以适应新尺寸的方式。 |

