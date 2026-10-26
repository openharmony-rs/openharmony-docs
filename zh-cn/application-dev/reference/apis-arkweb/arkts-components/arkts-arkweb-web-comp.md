# Web(Web控制器)

定义 Web 组件。

访问在线网页时需添加网络权限：ohos.permission.INTERNET，具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

<p><strong>接口说明</strong>:

<strong>性能说明</strong>: <p>有关如何优化编译、资源加载和JSBridge性能的详细信息，请参见Web加载性能优化 <p>当由于复杂的网页解析导致白屏时间较长时，可以开启[optimizeParserBudget](arkts-arkweb-web-comp-attribute.md#optimizeparserbudget)以减少首帧渲染内容。</p> </p>

## Web

```TypeScript
Web(value: WebOptions)
```

Sets Value.

> **说明：** 
> 
> - 在HTML5侧，调用console.log或console.info对应ConsoleMessage的信息级别都为MessageLevel.Info。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-WebInterface-(value: WebOptions): WebAttribute--><!--Device-WebInterface-(value: WebOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [WebOptions](arkts-arkweb-web-comp-weboptions-i.md) | 是 | Web组件的初始化配置选项，用于设置加载的网页资源（src）、绑定的控制器（controller）以及渲染模式等行为参数。具体属性结构请参考WebOptions接口定义。 |

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ClientAuthenticationHandler](arkts-arkweb-web-comp-clientauthenticationhandler-c.md) | ClientAuthenticationHandler是Web组件中处理SSL客户端证书认证请求的类。当服务器请求客户端证书进行TLS双向认证时，该处理器通过`onClientAuthenticationRequest`事件回调提供给应用，允许应用选择合适的证书凭据进行响应。示例代码参考[onClientAuthenticationRequest](arkts-arkweb-web-comp-attribute.md#onclientauthenticationrequest)事件。 |
| [ConsoleMessage](arkts-arkweb-web-comp-consolemessage-c.md) | ConsoleMessage是Web组件中封装JavaScript控制台输出信息的对象。当网页通过`console.log()`、`console.warn()`、`console.error()`等方法输出日志时，该对象通过`onConsole`事件回调提供给应用，用于监控和检查网页调试输出。示例代码参考[onConsole事件](arkts-arkweb-web-comp-attribute.md#onconsole)。 |
| [ControllerHandler](arkts-arkweb-web-comp-controllerhandler-c.md) | ControllerHandler是ArkWeb提供的处理新建Web组件控制器分配的帮助类。当Web页面通过`window.open`等方式请求创建新窗口，且Web组件已开启[multiWindowAccess](arkts-arkweb-web-comp-attribute.md#multiwindowaccess)能力时，系统通过[onWindowNew](arkts-arkweb-web-comp-attribute.md#onwindownew)事件将ControllerHandler对象提供给应用。开发者需调用其[setWebController](arkts-arkweb-web-comp-controllerhandler-c.md#setwebcontroller)方法为新窗口设置有效的[WebviewController](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md)对象，将新窗口与页面中实际创建的Web组件关联；Web内核在等待setWebController调用期间会阻塞渲染进程，若应用决定不创建新窗口，必须调用`setWebController(null)`通知Web内核，否则渲染进程会持续阻塞。典型使用场景是在自定义弹窗、新页面或分屏中打开Web新窗口，并需要应用侧显式管理新窗口的URL展示与安全隔离。 |
| [DataResubmissionHandler](arkts-arkweb-web-comp-dataresubmissionhandler-c.md) | DataResubmissionHandler是Web组件中处理网页表单数据重新提交的处理类。当网页需要重新提交之前已发送的表单数据时，Web组件会通过`onDataResubmitted`事件回调提供DataResubmissionHandler实例给应用，允许应用决定是否重新提交表单数据或取消导航。 |
| [EventResult](arkts-arkweb-web-comp-eventresult-c.md) | EventResult是ArkWeb Kit中用于通知Web组件同层事件消费结果的类。在同层嵌入场景下，应用与Web组件共同暴露在事件响应链中。EventResult允许应用向Web组件声明自身是否消费了触摸或鼠标事件，从而决定Web组件是否继续处理该事件。当应用设置消费结果为true时，表示应用已消费该事件，Web组件将不再消费；当设置为false时，表示应用不消费该事件，事件将由Web组件消费。EventResult用于设置触摸事件（[TouchType](../../apis-arkui/arkts-apis/arkts-arkui-touchtype-e.md)）和鼠标事件（[MouseAction](../../apis-arkui/arkts-apis/arkts-arkui-mouseaction-e.md)，仅限左中右按键）的消费结果，通过MouseButton定义鼠标按键的类型，适用于应用与Web组件同层交互的事件协调场景。 |
| [FileSelectorParam](arkts-arkweb-web-comp-fileselectorparam-c.md) | FileSelectorParam是ArkWeb组件中的文件选择器参数类，用于获取Web页面中`<input type="file">`触发文件选择请求时的相关参数信息，包括文件选择模式、文件过滤类型、MIME类型、建议文件名、默认起始路径等，帮助开发者高效构建符合HTML规范的自定义文件选择器。 |
| [FileSelectorResult](arkts-arkweb-web-comp-fileselectorresult-c.md) | FileSelectorResult是ArkWeb组件中用于通知Web组件文件选择结果的类，支持应用层自定义文件选择行为、统一文件选择结果回传机制，适用于应用需要接管文件选择流程的场景，例如拉起系统文件选择器、图库选择器或相机选择器后，将选中的文件结果返回给Web页面。当Web组件中的HTML页面通过`<input type="file">`等方式发起文件选择请求时，应用可通过FileSelectorResult将用户选择的文件列表回传给Web组件，完成文件选择流程。该类主要在`onShowFileSelector`事件回调中使用，使应用能够灵活控制文件选择交互，提升用户体验的一致性。示例代码参考[onShowFileSelector](arkts-arkweb-web-comp-attribute.md#onshowfileselector)。 |
| [FullScreenExitHandler](arkts-arkweb-web-comp-fullscreenexithandler-c.md) | FullScreenExitHandler 是 Web 组件提供的全屏退出处理类，用于响应网页退出全屏模式的事件。该类通过 exitFullScreen 方法通知开发者 Web 组件已退出全屏状态，帮助开发者及时处理全屏状态变化，调整应用界面布局或执行相应逻辑。示例代码参考[onFullScreenEnter](arkts-arkweb-web-comp-attribute.md#onfullscreenenter)。 |
| [HttpAuthHandler](arkts-arkweb-web-comp-httpauthhandler-c.md) | HttpAuthHandler是Web组件用于处理HTTP认证请求的处理类。当服务器返回401 Unauthorized要求身份认证时，Web组件通过onHttpAuthRequest事件回调获取HttpAuthHandler实例，由应用决定是否提供认证凭据。示例代码参考[onHttpAuthRequest](arkts-arkweb-web-comp-attribute.md#onhttpauthrequest)事件。 |
| [JsGeolocation](arkts-arkweb-web-comp-jsgeolocation-c.md) | JsGeolocation是Web组件在收到网页地理位置权限请求时，提供给应用的授权响应对象。当网页通过JavaScript调用地理位置接口（如navigator.geolocation）请求获取设备位置信息时，应用需要决定是否授权该请求。JsGeolocation通过invoke方法允许应用对指定源的网页授予或拒绝地理位置权限，同时可选择将该权限决策保存到系统中，避免后续同一源再次请求时重复弹出授权提示。 |
| [JsResult](arkts-arkweb-web-comp-jsresult-c.md) | JsResult是Web组件在处理JavaScript弹窗事件时返回的结果处理对象，适用于开发者拦截并自定义处理`window.alert`、`window.confirm`、`window.prompt`等弹窗场景。开发者可在[onAlert](arkts-arkweb-web-comp-attribute.md#onalert)、[onConfirm](arkts-arkweb-web-comp-attribute.md#onconfirm)或[onPrompt](arkts-arkweb-web-comp-attribute.md#onprompt)等事件回调中，通过该对象向Web组件反馈用户的确认、取消或输入内容等操作结果，从而控制弹窗的后续行为。 |
| [PermissionRequest](arkts-arkweb-web-comp-permissionrequest-c.md) | PermissionRequest 是 Web 组件用于授权或拒绝权限请求的对象。当网页尝试访问受保护的系统资源（如摄像头、麦克风、地理位置等）时，ArkWeb 内核会通过[onPermissionRequest](arkts-arkweb-web-comp-attribute.md#onpermissionrequest)事件回调向应用发送权限请求，应用通过 PermissionRequest 对象来决定是否授权这些请求。该对象适用于需要在应用中管理网页对敏感资源的访问权限、保护用户隐私、确保资源访问安全可控等场景，帮助开发者灵活处理网页权限请求。 |
| [ScreenCaptureHandler](arkts-arkweb-web-comp-screencapturehandler-c.md) | ScreenCaptureHandler 是 Web 组件提供的屏幕捕获权限处理类，用于响应网页发起的屏幕捕获请求。该类适用于在线教育、远程会议、屏幕录制等需要获取用户屏幕内容的应用场景。该类允许开发者通过 grant 或 deny方法控制是否授予网页屏幕捕获权限，并通过 getOrigin 方法获取请求来源信息，帮助开发者在保护用户隐私的同时，灵活处理网页的屏幕捕获访问需求，提升应用的安全性和用户体验。示例代码参考[onScreenCaptureRequest](arkts-arkweb-web-comp-attribute.md#onscreencapturerequest)事件。 |
| [SslErrorHandler](arkts-arkweb-web-comp-sslerrorhandler-c.md) | SslErrorHandler是Web组件中处理SSL证书验证错误的类。当加载安全页面时遇到SSL证书错误（如证书过期、主机名不匹配、不受信任的CA），应用可通过onSslErrorEvent回调获取SslErrorHandler实例，并决定是否继续加载或取消导航。示例代码参考[onSslErrorEvent](arkts-arkweb-web-comp-attribute.md#onsslerrorevent)事件。 |
| [VerifyPinHandler](arkts-arkweb-web-comp-verifypinhandler-c.md) | VerifyPinHandler是Web组件中处理PIN码验证请求的类，用于在Web页面中需要身份认证的场景（如安全支付、敏感操作确认等）增强应用安全性。当需要用户PIN码认证时，该处理器通过onVerifyPin事件回调提供给应用，允许应用响应PIN码验证结果，有效防止未授权访问并保护用户隐私。示例代码参考[onVerifyPin](arkts-arkweb-web-comp-attribute.md#onverifypin)。 |
| [WebContextMenuParam](arkts-arkweb-web-comp-webcontextmenuparam-c.md) | WebContextMenuParam是ArkWeb组件中用于承载长按页面元素或鼠标右键弹出的上下文菜单信息的参数类，作为`onContextMenuShow`事件回调的数据载体，封装了菜单弹出位置、链接地址、媒体类型、选中文本、编辑状态等关键信息。 |
| [WebContextMenuResult](arkts-arkweb-web-comp-webcontextmenuresult-c.md) | WebContextMenuResult是ArkWeb组件中用于处理上下文菜单（长按页面元素或鼠标右键弹出菜单）事件的类。它为开发者提供了一系列菜单操作的执行能力，包括文本编辑操作（复制、粘贴、剪切、全选、撤销、重做、粘贴并匹配样式）、图片操作（复制图片、保存图片）、菜单控制（关闭菜单）以及密码自动填充功能。 |
| [WebKeyboardController](arkts-arkweb-web-comp-webkeyboardcontroller-c.md) | WebKeyboardController是ArkWeb提供的用于控制Web组件自定义键盘行为的控制器类。当Web页面中的输入框需要弹出键盘时，开发者可通过[onInterceptKeyboardAttach](arkts-arkweb-web-comp-attribute.md#oninterceptkeyboardattach)事件拦截系统默认键盘的挂载，并使用WebKeyboardController向当前聚焦的Web输入框执行插入字符、前向/后向删除、发送Enter等功能键以及关闭自定义键盘等操作。该类适用于需要为Web场景实现自定义安全键盘、表情键盘、手写键盘或业务专属输入面板的应用，使开发者能够完全接管Web输入框的键盘输入逻辑。 |
| [WebResourceError](arkts-arkweb-web-comp-webresourceerror-c.md) | WebResourceError是Web组件中提供资源加载失败错误信息的类。该错误对象通过`onErrorReceive`和`onHttpErrorReceive`事件回调提供给应用，封装了错误详情用于调试和错误处理。通常与WebResourceRequest配合使用以确定哪个资源加载失败。示例代码参考[onErrorReceive事件](arkts-arkweb-web-comp-attribute.md#onerrorreceive)。 |
| [WebResourceRequest](arkts-arkweb-web-comp-webresourcerequest-c.md) | WebResourceRequest是Web组件中表示网络资源请求的类，提供了关于请求资源的详细元数据。该对象在`onErrorReceive`、`onHttpErrorReceive`以及请求拦截等事件回调中使用，用于帮助开发者诊断网络错误、监控请求状态和实现资源拦截控制。通过使用该类，应用可以提升错误处理能力、增强请求可控性和优化用户体验。示例代码参考[onErrorReceive事件](arkts-arkweb-web-comp-attribute.md#onerrorreceive)。 |
| [WebResourceResponse](arkts-arkweb-web-comp-webresourceresponse-c.md) | WebResourceResponse是Web组件中表示HTTP响应并允许自定义网页资源响应的类。它在onHttpErrorReceive等事件中向应用提供服务器返回响应的状态码、状态描述、响应头、响应数据、编码、MIME类型等信息；在资源请求拦截场景中允许应用自定义响应的状态码、状态描述、响应头、响应数据、编码、MIME类型及数据就绪状态，从而由应用接管特定资源的返回内容。示例代码参考[onHttpErrorReceive事件](arkts-arkweb-web-comp-attribute.md#onhttperrorreceive)。 |
| [WebController](arkts-arkweb-web-comp-webcontroller-c.md) | * WebController是ArkWeb组件的控制器类，用于控制Web组件的各种行为。一个WebController对象只能与一个Web组件绑定，绑定后开发者可通过该控制器对Web组件进行页面导航（前进/后退/加载）、焦点控制、缩放调整、页面刷新与停止、Cookie管理、JavaScript注入与执行等操作。 |
| [WebCookie](arkts-arkweb-web-comp-webcookie-c.md) | 通过WebCookie可以控制Web组件中的cookie的各种行为，其中每个应用中的所有Web组件共享一个WebCookie。通过controller方法中的getCookieManager方法可以获取WebCookie对象，进行后续的cookie管理操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AcceptableFileType](arkts-arkweb-web-comp-acceptablefiletype-i.md) | 提供文件选择器推荐的文件类型信息，包括MIME类型和类型数组。 |
| [AdsBlockedDetails](arkts-arkweb-web-comp-adsblockeddetails-i.md) | 发生广告拦截时，广告资源信息。 |
| [AISessionEvent](arkts-arkweb-web-comp-aisessionevent-i.md) | 自定义AI会话配置对象，用于定义AI会话的生命周期回调，包括创建、执行和销毁。 |
| [BlankScreenDetails](arkts-arkweb-web-comp-blankscreendetails-i.md) | 提供检测到白屏时的结果细节，包括有内容节点数量。适用于需要分析白屏原因的场景，提升白屏诊断的详细性和准确性。 |
| [BlankScreenDetectionConfig](arkts-arkweb-web-comp-blankscreendetectionconfig-i.md) | 提供白屏检测的策略配置选项，包括检测时机、方法和阈值。适用于需要自定义白屏检测行为的场景，提升白屏监控的灵活性和准确性。 |
| [BlankScreenDetectionEventInfo](arkts-arkweb-web-comp-blankscreendetectioneventinfo-i.md) | 提供检测到白屏时的事件信息，包括URL、原因和细节。适用于需要监控页面白屏问题的场景，提升白屏诊断的准确性和用户体验。 |
| [CameraCaptureStateChangeInfo](arkts-arkweb-web-comp-cameracapturestatechangeinfo-i.md) | 提供摄像头触发回调时的状态变化信息，包括改变前的状态和新状态。适用于需要监控摄像头状态变化的场景，提升摄像头管理的可见性和用户体验。 |
| [EmbedOptions](arkts-arkweb-web-comp-embedoptions-i.md) | Web同层渲染的配置。用于配置Web同层渲染选项，包括支持固定大小和CSS显示属性。适用于需要优化同层元素渲染效果的场景，提升渲染的兼容性和灵活性。 |
| [FirstMeaningfulPaint](arkts-arkweb-web-comp-firstmeaningfulpaint-i.md) | 提供网页绘制页面主要内容的详细信息，包括导航时间和绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [FirstScreenPaint](arkts-arkweb-web-comp-firstscreenpaint-i.md) | 提供首屏渲染事件的信息，包括URL和绘制时间。适用于需要监控页面首屏渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [FullScreenEnterEvent](arkts-arkweb-web-comp-fullscreenenterevent-i.md) | 提供 Web 组件进入全屏的回调信息，包括视频尺寸和退出句柄。适用于需要处理全屏视频的场景，提升视频播放的沉浸式体验和可控性。 |
| [Header](arkts-arkweb-web-comp-header-i.md) | Web组件返回的请求/响应头对象。适用于需要读取或修改HTTP头的场景，提升网络请求处理的灵活性和可控性。 |
| [IntelligentTrackingPreventionDetails](arkts-arkweb-web-comp-intelligenttrackingpreventiondetails-i.md) | 提供智能防跟踪拦截的详细信息，包括网站域名和追踪者域名。适用于需要监控广告拦截行为的场景，提升隐私保护的透明度和可控性。 |
| [JavaScriptProxy](arkts-arkweb-web-comp-javascriptproxy-i.md) | 定义要注入的JavaScript对象，包括对象名、方法列表和权限配置。适用于需要实现JavaScript与原生交互的场景，提升跨语言调用的灵活性和安全性。 |
| [LargestContentfulPaint](arkts-arkweb-web-comp-largestcontentfulpaint-i.md) | 提供网页绘制页面最大内容的详细信息，包括导航时间和各类绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [LoadCommittedDetails](arkts-arkweb-web-comp-loadcommitteddetails-i.md) | 提供已提交跳转的网页详细信息，包括是否主文档、导航类型等。适用于需要监控页面导航行为的场景，提升导航状态管理的准确性和用户体验。 |
| [MicrophoneCaptureStateChangeInfo](arkts-arkweb-web-comp-microphonecapturestatechangeinfo-i.md) | 提供麦克风触发回调时的状态变化信息，包括改变前的状态和改变后的状态。适用于需要监控麦克风状态变化的场景，提升麦克风管理的可见性和用户体验。 |
| [MonitoredBlankScreenEventInfo](arkts-arkweb-web-comp-monitoredblankscreeneventinfo-i.md) | 提供监测到白屏并完成根因归因时的事件信息，包括页面URL、归因原因和附加详情。适用于需要监控页面白屏问题并分析根因的场景，提升白屏问题的定位效率和用户体验。 |
| [NativeEmbedDataInfo](arkts-arkweb-web-comp-nativeembeddatainfo-i.md) | 提供同层标签生命周期变化的详细信息，包括状态和标签信息。适用于需要监控同层元素生命周期的场景，提升渲染状态管理的准确性和用户体验。 |
| [NativeEmbedInfo](arkts-arkweb-web-comp-nativeembedinfo-i.md) | 提供同层标签的详细信息，包括ID、类型、尺寸和位置等。适用于需要获取同层元素属性的场景，提升同层渲染的定制性和用户体验。 |
| [NativeEmbedMouseInfo](arkts-arkweb-web-comp-nativeembedmouseinfo-i.md) | 提供鼠标/触摸板在同层标签上点击或长按的详细信息，包括标签ID和鼠标事件。适用于需要处理同层元素鼠标交互的场景，提升鼠标体验的定制性和灵活性。 |
| [NativeEmbedParamDataInfo](arkts-arkweb-web-comp-nativeembedparamdatainfo-i.md) | 提供同层渲染object标签内嵌param元素变化时同层标签的详细信息，包括标签ID和参数项。适用于需要监控param元素变化的场景，提升同层元素管理的灵活性和准确性。 |
| [NativeEmbedParamItem](arkts-arkweb-web-comp-nativeembedparamitem-i.md) | 提供同层渲染object标签内嵌param元素的详细信息，包括状态和参数。适用于需要监控param元素变化的场景，提升同层元素管理的灵活性和准确性。 |
| [NativeEmbedTouchInfo](arkts-arkweb-web-comp-nativeembedtouchinfo-i.md) | 提供手指触摸同层标签的详细信息，包括标签ID和触摸事件。适用于需要处理同层元素触摸交互的场景，提升触摸体验的定制性和灵活性。 |
| [NativeEmbedVisibilityInfo](arkts-arkweb-web-comp-nativeembedvisibilityinfo-i.md) | 提供同层标签的可见性信息，包括可见状态和标签ID。适用于需要监控同层元素可见性的场景，提升渲染状态管理的准确性和用户体验。 |
| [NativeMediaPlayerConfig](arkts-arkweb-web-comp-nativemediaplayerconfig-i.md) | 用于配置应用接管网页媒体播放功能接口[enableNativeMediaPlayer](arkts-arkweb-web-comp-attribute.md#enablenativemediaplayer)的功能，支持是否开启及是否覆盖网页内容。适用于需要自定义媒体播放行为的场景，提升媒体播放的集成度和用户体验。 |
| [NestedScrollOptionsExt](arkts-arkweb-web-comp-nestedscrolloptionsext-i.md) | 用于设置Web组件嵌套滚动规则，支持上下左右四个方向的滚动选项。 |
| [OnAlertEvent](arkts-arkweb-web-comp-onalertevent-i.md) | 定义网页触发 `alert()` 告警时的回调函数。 |
| [OnAudioStateChangedEvent](arkts-arkweb-web-comp-onaudiostatechangedevent-i.md) | 定义网页音频播放状态改变时触发的回调信息，包括播放状态。适用于需要监控音频播放行为的场景，提升音频管理的可见性和用户体验。 |
| [OnBeforeUnloadEvent](arkts-arkweb-web-comp-onbeforeunloadevent-i.md) | 定义刷新或关闭场景下，在即将离开当前页面时触发此回调。适用于表单编辑等场景，允许开发者拦截离开动作并弹窗确认，从而避免用户未提交的数据意外丢失。 |
| [OnClientAuthenticationEvent](arkts-arkweb-web-comp-onclientauthenticationevent-i.md) | 定义需要提供SSL客户端证书时触发的回调信息，包括主机、端口和密钥类型。适用于需要处理客户端证书认证的场景，提升认证流程的灵活性和安全性。 |
| [OnConfirmEvent](arkts-arkweb-web-comp-onconfirmevent-i.md) | 定义网页触发 `confirm()` 弹窗时的回调函数。 |
| [OnConsoleEvent](arkts-arkweb-web-comp-onconsoleevent-i.md) | 定义通知宿主应用JavaScript console消息。 |
| [OnContextMenuShowEvent](arkts-arkweb-web-comp-oncontextmenushowevent-i.md) | 定义调用时触发的回调信息，以允许自定义显示上下文菜单。 |
| [OnDataResubmittedEvent](arkts-arkweb-web-comp-ondataresubmittedevent-i.md) | 定义网页表单可以重新提交时触发的回调信息，包括提交句柄。适用于需要处理表单重试提交的场景，提升表单交互的可靠性和用户体验。 |
| [OnDownloadStartEvent](arkts-arkweb-web-comp-ondownloadstartevent-i.md) | 定义通知主应用开始下载文件的回调信息，包括URL、用户代理和文件详情。适用于需要监控和管理文件下载的场景，提升下载流程的可控性和用户体验。 |
| [OnErrorReceiveEvent](arkts-arkweb-web-comp-onerrorreceiveevent-i.md) | 定义网页加载遇到错误时触发的回调信息，包括请求和错误详情。适用于需要监控和处理网页加载错误的场景，提升错误处理的及时性和用户体验。 |
| [OnFaviconReceivedEvent](arkts-arkweb-web-comp-onfaviconreceivedevent-i.md) | 定义应用接收到新favicon时触发的回调信息，包括图标PixelMap对象。适用于需要获取网页favicon的场景，提升图标管理的灵活性和用户体验。 |
| [OnFirstContentfulPaintEvent](arkts-arkweb-web-comp-onfirstcontentfulpaintevent-i.md) | 定义网页首次内容绘制的回调信息，包括加载时间和绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。 |
| [OnGeolocationShowEvent](arkts-arkweb-web-comp-ongeolocationshowevent-i.md) | 定义收到地理位置获取请求时触发的回调信息，包括源信息和地理对象。适用于需要处理地理位置权限的场景。 |
| [OnHttpAuthRequestEvent](arkts-arkweb-web-comp-onhttpauthrequestevent-i.md) | 定义收到HTTP认证请求时触发的回调信息，包括主机和域信息。适用于需要处理HTTP身份验证的场景，提升认证流程的灵活性和安全性。 |
| [OnHttpErrorReceiveEvent](arkts-arkweb-web-comp-onhttperrorreceiveevent-i.md) | 定义网页收到资源加载HTTP错误时触发的回调信息，包括请求和响应详情。适用于需要监控和处理HTTP错误的场景，提升网络错误诊断的准确性和用户体验。 |
| [OnInterceptRequestEvent](arkts-arkweb-web-comp-oninterceptrequestevent-i.md) | 定义Web组件加载URL之前触发的回调信息，包括请求详情。适用于需要拦截或修改网络请求的场景，提升请求控制的灵活性和安全性。 |
| [OnLoadFinishedEvent](arkts-arkweb-web-comp-onloadfinishedevent-i.md) | 定义网页加载结束时触发的回调信息，包括页面URL。适用于需要监控页面加载完成的场景，提升页面生命周期的管理能力。 |
| [OnLoadInterceptEvent](arkts-arkweb-web-comp-onloadinterceptevent-i.md) | 定义截获资源加载时触发的回调信息，包括请求详情。适用于需要拦截或处理资源加载的场景，提升资源控制的灵活性和安全性。 |
| [OnLoadStartedEvent](arkts-arkweb-web-comp-onloadstartedevent-i.md) | 定义网页加载开始时触发的回调信息，包括页面URL。适用于需要监控页面加载开始的场景，提升页面生命周期的管理能力。 |
| [OnOverScrollEvent](arkts-arkweb-web-comp-onoverscrollevent-i.md) | 定义网页过度滚动时触发的回调信息，包括水平和垂直偏移量。 |
| [OnPageBeginEvent](arkts-arkweb-web-comp-onpagebeginevent-i.md) | 定义网页加载开始时触发的回调信息，包括页面URL。适用于需要监控页面加载开始的场景，提升页面生命周期的管理能力。 |
| [OnPageEndEvent](arkts-arkweb-web-comp-onpageendevent-i.md) | 定义网页加载结束时触发的回调信息，包括页面URL。适用于需要监控页面加载完成的场景，提升页面生命周期的管理能力。 |
| [OnPageVisibleEvent](arkts-arkweb-web-comp-onpagevisibleevent-i.md) | 定义旧页面不再呈现，新页面即将可见时触发的回调函数。 |
| [OnPdfLoadEvent](arkts-arkweb-web-comp-onpdfloadevent-i.md) | 定义PDF加载成功或失败时触发的函数。 |
| [OnPdfScrollEvent](arkts-arkweb-web-comp-onpdfscrollevent-i.md) | 定义PDF页面滚动到底时触发的回调函数。 |
| [OnPermissionRequestEvent](arkts-arkweb-web-comp-onpermissionrequestevent-i.md) | 定义收到权限请求时触发的回调信息，包括请求详情。适用于需要处理权限授予的场景，提升权限管理的灵活性和安全性。 |
| [OnProgressChangeEvent](arkts-arkweb-web-comp-onprogresschangeevent-i.md) | 定义网页加载进度变化时触发的回调信息，包括新的进度值。适用于需要监控页面加载进度的场景，提升加载过程的可见性和用户体验。 |
| [OnPromptEvent](arkts-arkweb-web-comp-onpromptevent-i.md) | 定义网页触发 `prompt()` 弹窗时的回调函数。 |
| [OnRefreshAccessedHistoryEvent](arkts-arkweb-web-comp-onrefreshaccessedhistoryevent-i.md) | 定义导航完成时触发的回调信息，包括URL和刷新状态。适用于需要监控页面导航历史的场景，提升导航行为跟踪的准确性和用户体验。 |
| [OnRenderExitedEvent](arkts-arkweb-web-comp-onrenderexitedevent-i.md) | 定义渲染过程退出时触发。适用于需要监控渲染进程异常的场景，提升渲染稳定性和故障排查效率。 |
| [OnResourceLoadEvent](arkts-arkweb-web-comp-onresourceloadevent-i.md) | 定义加载URL时触发的回调信息，包括资源URL。适用于需要监控资源加载行为的场景，提升资源管理的可见性和性能优化。 |
| [OnScaleChangeEvent](arkts-arkweb-web-comp-onscalechangeevent-i.md) | 定义当前页面显示比例的变化时触发。 |
| [OnScreenCaptureRequestEvent](arkts-arkweb-web-comp-onscreencapturerequestevent-i.md) | 定义收到屏幕捕获请求时触发的回调信息。适用于需要处理屏幕录制权限的场景，提升录屏流程的可控性和安全性。 |
| [OnScrollEvent](arkts-arkweb-web-comp-onscrollevent-i.md) | 定义滚动条滑动到指定位置时触发的回调信息，包括水平和垂直偏移量。 |
| [OnSearchResultReceiveEvent](arkts-arkweb-web-comp-onsearchresultreceiveevent-i.md) | 定义网页页内查找结果的回调信息，包括匹配项序号和总数。适用于需要监控页内搜索行为的场景，提升搜索交互的可见性和用户体验。 |
| [OnShowFileSelectorEvent](arkts-arkweb-web-comp-onshowfileselectorevent-i.md) | 定义文件选择器结果的回调信息，包括结果和参数详情。 |
| [OnSslErrorEventReceiveEvent](arkts-arkweb-web-comp-onsslerroreventreceiveevent-i.md) | 定义网页收到SSL错误时触发的回调信息，包括错误码和证书链。适用于需要处理SSL错误的场景，提升安全异常的监控和处理能力。 |
| [OnTitleReceiveEvent](arkts-arkweb-web-comp-ontitlereceiveevent-i.md) | 定义网页标题更改时触发的回调信息，包括标题内容和来源。适用于需要监控页面标题变化的场景，提升页面信息的实时性和用户体验。 |
| [OnTouchIconUrlReceivedEvent](arkts-arkweb-web-comp-ontouchiconurlreceivedevent-i.md) | 定义接收到apple-touch-icon URL时触发的回调信息，包括URL和预合成状态。适用于需要获取网页图标的场景，提升图标管理的灵活性和用户体验。 |
| [OnWindowNewEvent](arkts-arkweb-web-comp-onwindownewevent-i.md) | 定义网页要求用户创建窗口时触发的回调。从API version 23开始，如需获取更多窗口信息，可使用[OnWindowNewExtEvent](arkts-arkweb-web-comp-onwindownewextevent-i.md)。 |
| [OnWindowNewExtEvent](arkts-arkweb-web-comp-onwindownewextevent-i.md) | 定义网页请求创建窗口时触发的回调信息，包括窗口特征信息和窗口打开方式。适用于需要精细控制新窗口行为的场景，提升窗口管理的定制性和用户体验。 |
| [OnZoomChangeEvent](arkts-arkweb-web-comp-onzoomchangeevent-i.md) | 描述网页浏览器级缩放倍率变化的信息。 |
| [PreviewMenuOptions](arkts-arkweb-web-comp-previewmenuoptions-i.md) | 用于配置预览菜单选项，支持设置菜单弹出时的振动效果。适用于需要增强菜单交互反馈的场景，提升用户体验。 |
| [RenderProcessNotRespondingData](arkts-arkweb-web-comp-renderprocessnotrespondingdata-i.md) | 提供渲染进程无响应的详细信息。适用于需要诊断渲染进程异常的场景，提升故障排查的准确性和效率。 |
| [ScreenCaptureConfig](arkts-arkweb-web-comp-screencaptureconfig-i.md) | 提供 Web 屏幕捕获的配置选项，包括捕获模式。适用于需要自定义网页录屏行为的场景，提升录屏功能的灵活性和用户体验。 |
| [ScriptItem](arkts-arkweb-web-comp-scriptitem-i.md) | 通过[javaScriptOnDocumentStart](arkts-arkweb-web-comp-attribute.md#javascriptondocumentstart)属性注入到Web组件的ScriptItem对象。 |
| [SelectionMenuOptionsExt](arkts-arkweb-web-comp-selectionmenuoptionsext-i.md) | 自定义菜单扩展项。 |
| [SslErrorEvent](arkts-arkweb-web-comp-sslerrorevent-i.md) | 用户加载资源时发生SSL错误时触发的回调详情，包括URL、错误类型和证书链。适用于需要详细分析SSL错误的场景，提升安全问题的诊断和排查效率。 |
| [UrlRegexRule](arkts-arkweb-web-comp-urlregexrule-i.md) | 定义Url正则表达式规则。 |
| [VerifyPinEvent](arkts-arkweb-web-comp-verifypinevent-i.md) | 定义当需要用户进行PIN码认证时触发回调。 |
| [WebContextMenuOptions](arkts-arkweb-web-comp-webcontextmenuoptions-i.md) | 定义上下文菜单项的选项。 |
| [WebKeyboardCallbackInfo](arkts-arkweb-web-comp-webkeyboardcallbackinfo-i.md) | 拦截网页可编辑元素拉起软键盘的回调入参，包括[WebKeyboardController](arkts-arkweb-web-comp.md)和可编辑元素的属性。适用于需要自定义键盘交互的场景，提升输入体验的定制性和灵活性。 |
| [WebKeyboardOptions](arkts-arkweb-web-comp-webkeyboardoptions-i.md) | 拦截网页可编辑元素拉起软键盘的回调返回值，包括键盘类型和自定义键盘。适用于需要控制软键盘行为的场景。 |
| [WebMediaOptions](arkts-arkweb-web-comp-webmediaoptions-i.md) | 用于配置 Web 组件的媒体策略，包括音频续播有效期、音频独占模式等。适用于需要优化音频播放体验和多实例音频管理的场景，提升媒体播放的稳定性和用户体验。 |
| [WebOptions](arkts-arkweb-web-comp-weboptions-i.md) | 通过[接口](../../../reference/apis-arkweb/arkts-basic-components-web.md#接口)定义Web选项，包括网页资源地址、控制器、渲染方式等。 |
| [WindowFeatures](arkts-arkweb-web-comp-windowfeatures-i.md) | 提供网页请求创建的新窗口特征信息，包括大小和位置。适用于需要精确控制新窗口属性的场景，提升窗口布局的准确性和用户体验。 |
| [ExpandedMenuItemOptions](arkts-arkweb-web-comp-expandedmenuitemoptions-i.md) | 自定义菜单扩展项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [MouseInfoCallback](arkts-arkweb-web-comp-mouseinfocallback-t.md) | 当鼠标/触摸板单击到同层标签时触发此回调。 |
| [OnAdsBlockedCallback](arkts-arkweb-web-comp-onadsblockedcallback-t.md) | 当页面发生广告过滤时触发此回调。 |
| [OnAISessionCallback](arkts-arkweb-web-comp-onaisessioncallback-t.md) | AI会话操作结果回调函数类型。用于报告会话创建或执行的结果。 |
| [OnCameraCaptureStateChangeCallback](arkts-arkweb-web-comp-oncameracapturestatechangecallback-t.md) | 当页面摄像设备状态发生改变时触发此回调。 |
| [OnContextMenuHideCallback](arkts-arkweb-web-comp-oncontextmenuhidecallback-t.md) | 上下文菜单自定义隐藏的回调。 |
| [OnContextMenuUpdateCallback](arkts-arkweb-web-comp-oncontextmenuupdatecallback-t.md) | 上下文菜单项状态更新的回调类型。 |
| [OnCreateAISession](arkts-arkweb-web-comp-oncreateaisession-t.md) | AI会话创建回调函数类型。允许自定义模型初始化和结果处理。 |
| [OnDestroyAISession](arkts-arkweb-web-comp-ondestroyaisession-t.md) | AI会话销毁回调函数类型。用于清理与自定义AI模型关联的资源。 |
| [OnDetectBlankScreenCallback](arkts-arkweb-web-comp-ondetectblankscreencallback-t.md) | 检测到白屏时触发此回调。 |
| [OnExecuteAIAction](arkts-arkweb-web-comp-onexecuteaiaction-t.md) | AI会话执行操作回调函数类型。用于自定义实现AI模型执行。 |
| [OnFirstMeaningfulPaintCallback](arkts-arkweb-web-comp-onfirstmeaningfulpaintcallback-t.md) | 网页首次绘制页面主要内容度量的回调，当网页加载完页面主要内容时会触发此回调。与OnLargestContentfulPaintCallback关注最大内容元素绘制时间、OnFirstScreenPaintCallback关注首屏可见内容渲染完成相比，本回调更关注主要内容是否加载完成，适合评估用户可见内容的加载体验。 |
| [OnFirstScreenPaintCallback](arkts-arkweb-web-comp-onfirstscreenpaintcallback-t.md) | 检测到首屏渲染结束时会触发此回调。与OnFirstMeaningfulPaintCallback关注主要内容加载完成、OnLargestContentfulPaintCallback关注最大内容元素绘制时间相比，本回调更关注首屏可见内容的渲染完成时间，适合评估用户首次视觉体验。 |
| [OnFullScreenEnterCallback](arkts-arkweb-web-comp-onfullscreenentercallback-t.md) | Web组件进入全屏时触发的回调。 |
| [OnInputmethodAttachedCallback](arkts-arkweb-web-comp-oninputmethodattachedcallback-t.md) | 当检测到输入法绑定成功时，会触发此回调。 |
| [OnIntelligentTrackingPreventionCallback](arkts-arkweb-web-comp-onintelligenttrackingpreventioncallback-t.md) | 当跟踪者cookie被拦截时触发的回调。 |
| [OnLargestContentfulPaintCallback](arkts-arkweb-web-comp-onlargestcontentfulpaintcallback-t.md) | 当网页绘制最大内容区域时触发的回调，用于获取最大内容绘制的性能度量信息。适用于需要监控网页加载性能、优化页面渲染速度等场景。与OnFirstMeaningfulPaintCallback关注主要内容加载完成、OnFirstScreenPaintCallback关注首屏可见内容渲染完成相比，本回调关注最大内容元素的绘制时间，适合评估页面渲染完成度和性能瓶颈。 |
| [OnMicrophoneCaptureStateChangeCallback](arkts-arkweb-web-comp-onmicrophonecapturestatechangecallback-t.md) | 当页面麦克风状态发生改变时触发此回调。 |
| [OnMonitorBlankScreenCallback](arkts-arkweb-web-comp-onmonitorblankscreencallback-t.md) | 监测到白屏并完成根因归因时触发此回调。 |
| [OnNativeEmbedObjectParamChangeCallback](arkts-arkweb-web-comp-onnativeembedobjectparamchangecallback-t.md) | 增加、修改或删除同层渲染object标签内嵌param元素时触发此回调。 |
| [OnNativeEmbedVisibilityChangeCallback](arkts-arkweb-web-comp-onnativeembedvisibilitychangecallback-t.md) | 当同层标签可见性变化时触发该回调。 |
| [OnNavigationEntryCommittedCallback](arkts-arkweb-web-comp-onnavigationentrycommittedcallback-t.md) | 导航条目提交时触发的回调。 |
| [OnOverrideErrorPageCallback](arkts-arkweb-web-comp-onoverrideerrorpagecallback-t.md) | onOverrideErrorPage的回调函数，网页加载失败时触发。 |
| [OnOverrideUrlLoadingCallback](arkts-arkweb-web-comp-onoverrideurlloadingcallback-t.md) | 用于拦截URL加载请求的回调，可阻止特定URL的加载或进行自定义处理。适用于需要拦截广告、阻止恶意网站跳转等场景。 |
| [OnRenderProcessNotRespondingCallback](arkts-arkweb-web-comp-onrenderprocessnotrespondingcallback-t.md) | 渲染进程无响应时触发的回调。 |
| [OnRenderProcessRespondingCallback](arkts-arkweb-web-comp-onrenderprocessrespondingcallback-t.md) | 渲染进程由无响应状态变回正常运行状态时触发该回调。 |
| [OnSafeBrowsingCheckResultCallback](arkts-arkweb-web-comp-onsafebrowsingcheckresultcallback-t.md) | 网站安全风险检查触发的回调。 |
| [OnSslErrorEventCallback](arkts-arkweb-web-comp-onsslerroreventcallback-t.md) | 用户加载资源时发生SSL错误时触发的回调，返回SSL错误详细信息。 |
| [OnVerifyPinCallback](arkts-arkweb-web-comp-onverifypincallback-t.md) | 需要用户进行PIN码认证时触发的回调。 |
| [OnViewportFitChangedCallback](arkts-arkweb-web-comp-onviewportfitchangedcallback-t.md) | 网页meta中viewport-fit配置项更改时触发的回调。 |
| [OnZoomChangeCallback](arkts-arkweb-web-comp-onzoomchangecallback-t.md) | 浏览器级缩放倍率变化时触发的回调类型。 |
| [TextSelectionChangeCallback](arkts-arkweb-web-comp-textselectionchangecallback-t.md) | onTextSelectionChange的回调，选区内容改变时触发。 |
| [WebKeyboardCallback](arkts-arkweb-web-comp-webkeyboardcallback-t.md) | 拦截网页可编辑元素拉起软键盘的回调，一般在点击网页input标签时触发。 |
| [WebviewController](arkts-arkweb-web-comp-webviewcontroller-t.md) | 提供Web控制器的方法。通过WebviewController可以控制Web组件各种行为。一个WebviewController对象只能控制一个Web组件，且必须在Web组件和WebviewController绑定后，才能调用WebviewController上的方法（静态方法除外）。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AISessionResultType](arkts-arkweb-web-comp-aisessionresulttype-e.md) | AI会话操作的结果状态。 |
| [AISessionType](arkts-arkweb-web-comp-aisessiontype-e.md) | 支持的AI会话类型。 |
| [AudioSessionType](arkts-arkweb-web-comp-audiosessiontype-e.md) | 应用中 Web 音频类型，用于控制 Web 音频的音频流类型和行为，帮助开发者根据应用场景优化音频体验，如支持网页游戏声音与系统音乐同时播放。 |
| [BlankScreenDetectionMethod](arkts-arkweb-web-comp-blankscreendetectionmethod-e.md) | 白屏检测使用的检测策略的方法，用于定义页面内容检测的具体算法和点位，帮助开发者在检测准确性和性能开销之间取得平衡，及时发现页面渲染异常。 |
| [BlankScreenReason](arkts-arkweb-web-comp-blankscreenreason-e.md) | 白屏归因的具体原因，从网络层、资源层、渲染与JS层、内核与进程层、容器层标识白屏问题的根因，帮助开发者快速定位白屏问题来源，提升页面加载问题的排查效率和用户体验。 |
| [BlurOnKeyboardHideMode](arkts-arkweb-web-comp-bluronkeyboardhidemode-e.md) | 设置手动收起软键盘时Web元素是否失焦。 |
| [CacheMode](arkts-arkweb-web-comp-cachemode-e.md) | 缓存模式。 |
| [CameraCaptureState](arkts-arkweb-web-comp-cameracapturestate-e.md) | 定义摄像头使用状态的值，用于标识摄像头的当前工作状态，帮助开发者实时监控摄像头资源使用情况，优化资源管理和用户隐私保护。 |
| [ConsoleMessageSource](arkts-arkweb-web-comp-consolemessagesource-e.md) | ConsoleMessage的日志来源。 |
| [ContextMenuDataMediaType](arkts-arkweb-web-comp-contextmenudatamediatype-e.md) | 触发上下文菜单的网页元素类型（增强获取类型能力）。 |
| [ContextMenuEditStateFlags](arkts-arkweb-web-comp-contextmenueditstateflags-e.md) | 支持以按位或的方式使用此枚举。例如，如果需要同时支持CAN_CUT、CAN_COPY和CAN_SELECT_ALL，可使用CAN_CUT | CAN_COPY | CAN_SELECT_ALL或11。 |
| [ContextMenuInputFieldType](arkts-arkweb-web-comp-contextmenuinputfieldtype-e.md) | 输入框类型。 |
| [ContextMenuMediaType](arkts-arkweb-web-comp-contextmenumediatype-e.md) | 触发上下文菜单的网页元素类型。 |
| [ContextMenuSourceType](arkts-arkweb-web-comp-contextmenusourcetype-e.md) | 触发上下文菜单的事件来源。 |
| [CredentialType](arkts-arkweb-web-comp-credentialtype-e.md) | 凭证类型，用于定义身份认证中使用的凭证种类。 |
| [DetectedBlankScreenReason](arkts-arkweb-web-comp-detectedblankscreenreason-e.md) | 白屏的具体原因，用于标识页面白屏现象的底层原因，帮助开发者快速定位问题来源，提升页面加载问题的排查效率和用户体验。 |
| [FileSelectorMode](arkts-arkweb-web-comp-fileselectormode-e.md) | 文件选择器的模式，用于控制文件选择器的打开方式和行为，帮助开发者实现文件上传等文件操作场景。 |
| [GestureFocusMode](arkts-arkweb-web-comp-gesturefocusmode-e.md) | 手势获焦的模式。 |
| [MessageLevel](arkts-arkweb-web-comp-messagelevel-e.md) | ConsoleMessage的信息级别。 |
| [MicrophoneCaptureState](arkts-arkweb-web-comp-microphonecapturestate-e.md) | 定义麦克风使用状态的值，用于标识麦克风的当前工作状态，帮助开发者实时监控麦克风资源使用情况，优化资源管理和用户隐私保护。 |
| [MixedMode](arkts-arkweb-web-comp-mixedmode-e.md) | 混合内容模式。 |
| [NativeEmbedParamStatus](arkts-arkweb-web-comp-nativeembedparamstatus-e.md) | 定义同层渲染object标签内嵌param元素的状态变化类型，当添加param元素时触发ADD，修改param元素属性触发UPDATE，删除param元素触发DELETE。 |
| [NativeEmbedStatus](arkts-arkweb-web-comp-nativeembedstatus-e.md) | 定义同层标签生命周期，当加载页面中有同层标签会触发CREATE，同层标签移动或者放大会触发UPDATE，退出页面会触发DESTROY。 |
| [NavigationPolicy](arkts-arkweb-web-comp-navigationpolicy-e.md) | WebView中新窗口的打开方式，支持弹窗、新窗口、前台和后台标签页等多种方式。 |
| [OverScrollMode](arkts-arkweb-web-comp-overscrollmode-e.md) | 设置Web的过滚动模式为关闭或开启。 |
| [PdfLoadResult](arkts-arkweb-web-comp-pdfloadresult-e.md) | 定义PDF页面的加载结果，用于标识PDF文件加载过程中的各种状态和错误类型，帮助开发者在PDF显示失败时进行错误诊断和用户提示。 |
| [PinVerifyResult](arkts-arkweb-web-comp-pinverifyresult-e.md) | PIN码认证结果，用于标识PIN码验证的执行状态。 |
| [ProtectedResourceType](arkts-arkweb-web-comp-protectedresourcetype-e.md) | ProtectedResourceType 枚举定义了 Web 组件需要访问的受保护资源类型，用于控制MIDI、相机、麦克风、传感器等敏感资源的访问权限，帮助开发者在保护用户隐私的同时提供丰富的 Web 功能。 |
| [RenderExitReason](arkts-arkweb-web-comp-renderexitreason-e.md) | onRenderExited接口返回的渲染进程退出的具体原因。 |
| [RenderMode](arkts-arkweb-web-comp-rendermode-e.md) | 定义Web组件的渲染方式，默认为异步渲染模式。 |
| [RenderProcessNotRespondingReason](arkts-arkweb-web-comp-renderprocessnotrespondingreason-e.md) | 触发渲染进程无响应回调的原因。 |
| [ScrollbarLayoutPolicy](arkts-arkweb-web-comp-scrollbarlayoutpolicy-e.md) | 定义滚动条布局模式控制参数的枚举类型。 |
| [ScrollDirectionalLockType](arkts-arkweb-web-comp-scrolldirectionallocktype-e.md) | 定义滑动方向锁定的场景类型。 |
| [SslError](arkts-arkweb-web-comp-sslerror-e.md) | onSslErrorEventReceive接口返回的SSL错误的具体原因。 |
| [ThreatType](arkts-arkweb-web-comp-threattype-e.md) | 定义网站风险类型。 |
| [ViewportFit](arkts-arkweb-web-comp-viewportfit-e.md) | 网页meta中viewport-fit配置的视口类型。 |
| [WebBypassVsyncCondition](arkts-arkweb-web-comp-webbypassvsynccondition-e.md) | 跳过渲染vsync条件。 |
| [WebCaptureMode](arkts-arkweb-web-comp-webcapturemode-e.md) | Web屏幕捕获模式。 |
| [WebContextMenuItemId](arkts-arkweb-web-comp-webcontextmenuitemid-e.md) | 枚举上下文菜单项的ID。 |
| [WebDarkMode](arkts-arkweb-web-comp-webdarkmode-e.md) | Web深色模式的配置，用于控制网页内容的深色主题显示，帮助开发者根据用户偏好和系统主题提升视觉体验和可读性。 |
| [WebElementType](arkts-arkweb-web-comp-webelementtype-e.md) | 网页元素信息。 |
| [WebKeyboardAppearanceMode](arkts-arkweb-web-comp-webkeyboardappearancemode-e.md) | WebView中输入法沉浸模式，用于控制软键盘的显示风格，帮助开发者根据应用主题和用户偏好提供一致性的视觉体验，支持默认外观、系统跟随、浅色和深色沉浸式风格。 |
| [WebKeyboardAvoidMode](arkts-arkweb-web-comp-webkeyboardavoidmode-e.md) | 软键盘避让的模式。 |
| [WebLayoutMode](arkts-arkweb-web-comp-weblayoutmode-e.md) | Web布局模式的配置，用于控制Web内容的页面布局方式，帮助开发者根据屏幕尺寸和显示需求优化网页的适配性和用户体验。 |
| [WebNavigationType](arkts-arkweb-web-comp-webnavigationtype-e.md) | 定义navigation类型。 |
| [WebResponseType](arkts-arkweb-web-comp-webresponsetype-e.md) | 菜单的响应类型。 |
| [WebRotateEffect](arkts-arkweb-web-comp-webrotateeffect-e.md) | 组件旋转时，宽高动画过程中组件内容如何填充以适应新尺寸的方式。 |
| [HitTestType](arkts-arkweb-web-comp-hittesttype-e.md) | 点击事件检测结果类型。 |
