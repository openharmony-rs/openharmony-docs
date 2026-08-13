# web

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [Web](arkts-na-web-web-f.md#Web) | Defines Web Component. |

### 类

| 名称 | 说明 |
| --- | --- |
| [ClientAuthenticationHandler](arkts-na-web-clientauthenticationhandler-c.md) | Defines the client certificate request result, related to onClientAuthenticationRequest method. |
| [ConsoleMessage](arkts-na-web-consolemessage-c.md) | Encompassed message information as parameters to onConsole method. |
| [ControllerHandler](arkts-na-web-controllerhandler-c.md) | Defines the onWindowNew callback, related to onWindowNew method. |
| [DataResubmissionHandler](arkts-na-web-dataresubmissionhandler-c.md) | Defines the onDataResubmission callback, related to onDataResubmission method. |
| [EventResult](arkts-na-web-eventresult-c.md) | Represents the event consumption result sent to the Web component. For details about the supported events, see TouchEvent/MouseEvent. If the application does not consume the event, set this parameter to false, and the event will be consumed by the Web component. If the application has consumed the event, set this parameter to true, and the event will not be consumed by the Web component. |
| [FileSelectorParam](arkts-na-web-fileselectorparam-c.md) | Encompassed message information as parameters to onFileSelectorShow method. |
| [FileSelectorResult](arkts-na-web-fileselectorresult-c.md) | Defines the file selector result, related to onFileSelectorShow method. |
| [FullScreenExitHandler](arkts-na-web-fullscreenexithandler-c.md) | Define the handler to exit the full screen mode, related to the onFullScreenEnter event. |
| [HttpAuthHandler](arkts-na-web-httpauthhandler-c.md) | Defines the http auth request result, related to onHttpAuthRequest method. |
| [JsGeolocation](arkts-na-web-jsgeolocation-c.md) | Defines the js geolocation request. |
| [JsResult](arkts-na-web-jsresult-c.md) | Defines the js result. |
| [PermissionRequest](arkts-na-web-permissionrequest-c.md) | 权限请求。 |
| [ScreenCaptureHandler](arkts-na-web-screencapturehandler-c.md) | Defines the onScreenCapture callback, related to onScreenCapture method. |
| [SslErrorHandler](arkts-na-web-sslerrorhandler-c.md) | Defines the ssl error request result, related to onSslErrorEventReceive method. |
| [VerifyPinHandler](arkts-na-web-verifypinhandler-c.md) | Handle the result of PIN verification. |
| [WebContextMenuParam](arkts-na-web-webcontextmenuparam-c.md) | Defines the context menu param, related to [WebContextMenuParam](arkts-na-web-webcontextmenuparam-c.md#WebContextMenuParam) method. |
| [WebContextMenuResult](arkts-na-web-webcontextmenuresult-c.md) | Defines the context menu result, related to [WebContextMenuResult](arkts-na-web-webcontextmenuresult-c.md#WebContextMenuResult) method. |
| [WebKeyboardController](arkts-na-web-webkeyboardcontroller-c.md) | Define the controller to interact with a custom keyboard, related to the onInterceptKeyboardAttach event. |
| [WebResourceError](arkts-na-web-webresourceerror-c.md) | Defines the Web resource error. |
| [WebResourceRequest](arkts-na-web-webresourcerequest-c.md) | Defines the Web resource request. |
| [WebResourceResponse](arkts-na-web-webresourceresponse-c.md) | Defines the Web resource response. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AISessionEvent](arkts-na-web-aisessionevent-i.md) | Custom AI session model integration for Web components. Users can define custom AI session behaviors via this interface. |
| [AcceptableFileType](arkts-na-web-acceptablefiletype-i.md) | Define file selection type. |
| [AdsBlockedDetails](arkts-na-web-adsblockeddetails-i.md) | Defines the ads block details. |
| [BlankScreenDetails](arkts-na-web-blankscreendetails-i.md) | The details of this blank screen detection result. |
| [BlankScreenDetectionConfig](arkts-na-web-blankscreendetectionconfig-i.md) | The strategy of blank screen detection. |
| [BlankScreenDetectionEventInfo](arkts-na-web-blankscreendetectioneventinfo-i.md) | Defines the blank screen detection event info. |
| [CameraCaptureStateChangeInfo](arkts-na-web-cameracapturestatechangeinfo-i.md) | Defines the camera capture state change info. |
| [EmbedOptions](arkts-na-web-embedoptions-i.md) | Defines the Embed Options. |
| [FirstMeaningfulPaint](arkts-na-web-firstmeaningfulpaint-i.md) | Provides detailed information about the first meaningful paint. |
| [FirstScreenPaint](arkts-na-web-firstscreenpaint-i.md) | Defines the first screen paint info. |
| [FullScreenEnterEvent](arkts-na-web-fullscreenenterevent-i.md) | Web组件进入全屏回调事件的详情。 |
| [Header](arkts-na-web-header-i.md) | Defines the Web's request/response header. |
| [IntelligentTrackingPreventionDetails](arkts-na-web-intelligenttrackingpreventiondetails-i.md) | Defines the Intelligent Tracking Prevention details. |
| [JavaScriptProxy](arkts-na-web-javascriptproxy-i.md) | Defines the JavaScript object to be injected. |
| [LargestContentfulPaint](arkts-na-web-largestcontentfulpaint-i.md) | Defines the largest content paint rendering of web page. |
| [LoadCommittedDetails](arkts-na-web-loadcommitteddetails-i.md) | Defines the load committed details. |
| [MicrophoneCaptureStateChangeInfo](arkts-na-web-microphonecapturestatechangeinfo-i.md) | Defines the microphone capture state change info. |
| [NativeEmbedDataInfo](arkts-na-web-nativeembeddatainfo-i.md) | Provides detailed information about the changes of the same-layer tag lifecycle. |
| [NativeEmbedInfo](arkts-na-web-nativeembedinfo-i.md) | Defines the embed info. |
| [NativeEmbedMouseInfo](arkts-na-web-nativeembedmouseinfo-i.md) | Defines the user mouse info on embed layer. |
| [NativeEmbedParamDataInfo](arkts-na-web-nativeembedparamdatainfo-i.md) | Defines the param data info. |
| [NativeEmbedParamItem](arkts-na-web-nativeembedparamitem-i.md) | Defines the information of param element. |
| [NativeEmbedTouchInfo](arkts-na-web-nativeembedtouchinfo-i.md) | Defines the user touch info. |
| [NativeEmbedVisibilityInfo](arkts-na-web-nativeembedvisibilityinfo-i.md) | Provides visibility information about the same-layer tag. |
| [NativeMediaPlayerConfig](arkts-na-web-nativemediaplayerconfig-i.md) | 用于 [开启应用接管网页媒体播放功能](../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#enablenativemediaplayer12)的 配置信息。 |
| [NestedScrollOptionsExt](arkts-na-web-nestedscrolloptionsext-i.md) | Define nested scroll options |
| [OnAlertEvent](arkts-na-web-onalertevent-i.md) | Defines the triggered function when the web page wants to display a JavaScript alert() dialog. |
| [OnAudioStateChangedEvent](arkts-na-web-onaudiostatechangedevent-i.md) | 定义网页上的音频播放状态发生改变时的回调函数。 |
| [OnBeforeUnloadEvent](arkts-na-web-onbeforeunloadevent-i.md) | Defines the triggered function when the web page wants to confirm navigation from JavaScript onbeforeunload. |
| [OnClientAuthenticationEvent](arkts-na-web-onclientauthenticationevent-i.md) | Defines the triggered callback when needs ssl client certificate from the user. |
| [OnConfirmEvent](arkts-na-web-onconfirmevent-i.md) | Defines the triggered function when the web page wants to display a JavaScript confirm() dialog. |
| [OnConsoleEvent](arkts-na-web-onconsoleevent-i.md) | Defines the triggered function when the web page receives a JavaScript console message. |
| [OnContextMenuShowEvent](arkts-na-web-oncontextmenushowevent-i.md) | Defines the triggered callback when called to allow custom display of the context menu. |
| [OnDataResubmittedEvent](arkts-na-web-ondataresubmittedevent-i.md) | Defines the triggered callback to decision whether resend form data or not. |
| [OnDownloadStartEvent](arkts-na-web-ondownloadstartevent-i.md) | Defines the triggered function when starting to download. |
| [OnErrorReceiveEvent](arkts-na-web-onerrorreceiveevent-i.md) | Defines the triggered function when the web page receives a web resource loading error. |
| [OnFaviconReceivedEvent](arkts-na-web-onfaviconreceivedevent-i.md) | Defines the triggered callback when the application receive a new favicon for the current web page. |
| [OnFirstContentfulPaintEvent](arkts-na-web-onfirstcontentfulpaintevent-i.md) | Defines triggered when the first content rendering of web page. |
| [OnGeolocationShowEvent](arkts-na-web-ongeolocationshowevent-i.md) | Defines the triggered function when requesting to show the geolocation permission. |
| [OnHttpAuthRequestEvent](arkts-na-web-onhttpauthrequestevent-i.md) | Defines the triggered when the browser needs credentials from the user. |
| [OnHttpErrorReceiveEvent](arkts-na-web-onhttperrorreceiveevent-i.md) | Defines the triggered function when the web page receives a web resource loading HTTP error. |
| [OnInterceptRequestEvent](arkts-na-web-oninterceptrequestevent-i.md) | Defines the triggered callback when the resources loading is intercepted. |
| [OnLoadFinishedEvent](arkts-na-web-onloadfinishedevent-i.md) | Defines the triggered function at the end of web page loading. |
| [OnLoadInterceptEvent](arkts-na-web-onloadinterceptevent-i.md) | Defines the triggered callback when the resources loading is intercepted. |
| [OnLoadStartedEvent](arkts-na-web-onloadstartedevent-i.md) | Defines the triggered function at the begin of web page loading. |
| [OnOverScrollEvent](arkts-na-web-onoverscrollevent-i.md) | Defines the function Triggered when the over scrolling. |
| [OnPageBeginEvent](arkts-na-web-onpagebeginevent-i.md) | Defines the triggered function at the begin of web page loading. |
| [OnPageEndEvent](arkts-na-web-onpageendevent-i.md) | Defines the triggered function at the end of web page loading. |
| [OnPageVisibleEvent](arkts-na-web-onpagevisibleevent-i.md) | Defines the triggered callback when previous page will no longer be drawn and next page begin to draw. |
| [OnPdfLoadEvent](arkts-na-web-onpdfloadevent-i.md) | 定义PDF加载成功或失败时触发的函数。 |
| [OnPdfScrollEvent](arkts-na-web-onpdfscrollevent-i.md) | 定义PDF页面滚动到底时触发的回调函数。 |
| [OnPermissionRequestEvent](arkts-na-web-onpermissionrequestevent-i.md) | 定义通知收到获取权限请求。 |
| [OnProgressChangeEvent](arkts-na-web-onprogresschangeevent-i.md) | Defines the triggered function when the page loading progress changes. |
| [OnPromptEvent](arkts-na-web-onpromptevent-i.md) | Defines the triggered function when the web page wants to display a JavaScript prompt() dialog. |
| [OnRefreshAccessedHistoryEvent](arkts-na-web-onrefreshaccessedhistoryevent-i.md) | Defines the triggered callback when the Web page refreshes accessed history. |
| [OnRenderExitedEvent](arkts-na-web-onrenderexitedevent-i.md) | Defines the triggered when the render process exits. |
| [OnResourceLoadEvent](arkts-na-web-onresourceloadevent-i.md) | Defines the triggered when the url loading. |
| [OnScaleChangeEvent](arkts-na-web-onscalechangeevent-i.md) | Defines the triggered when the scale of WebView changed. |
| [OnScreenCaptureRequestEvent](arkts-na-web-onscreencapturerequestevent-i.md) | 定义通知收到屏幕捕获请求。 |
| [OnScrollEvent](arkts-na-web-onscrollevent-i.md) | Defines function Triggered when the scroll bar slides to the specified position. |
| [OnSearchResultReceiveEvent](arkts-na-web-onsearchresultreceiveevent-i.md) | Defines function Triggered when the host application call searchAllAsync. |
| [OnShowFileSelectorEvent](arkts-na-web-onshowfileselectorevent-i.md) | Defines the triggered when the file selector shows. |
| [OnSslErrorEventReceiveEvent](arkts-na-web-onsslerroreventreceiveevent-i.md) | Defines the triggered callback when the Web page receives an ssl Error. |
| [OnTitleReceiveEvent](arkts-na-web-ontitlereceiveevent-i.md) | Defines the triggered function when the title of the main application document changes. |
| [OnTouchIconUrlReceivedEvent](arkts-na-web-ontouchiconurlreceivedevent-i.md) | Defines the triggered callback when the application receive an new url of an apple-touch-icon. |
| [OnWindowNewEvent](arkts-na-web-onwindownewevent-i.md) | Defines the triggered callback when web page requires the user to create a window. |
| [OnWindowNewExtEvent](arkts-na-web-onwindownewextevent-i.md) | Defines the triggered callback when web page requires the user to create a window. |
| [RenderProcessNotRespondingData](arkts-na-web-renderprocessnotrespondingdata-i.md) | Defines the render process not responding info. |
| [ScreenCaptureConfig](arkts-na-web-screencaptureconfig-i.md) | Defines the screen capture configuration. |
| [ScriptItem](arkts-na-web-scriptitem-i.md) | Defines the contents of the JavaScript to be injected. |
| [SelectionMenuOptionsExt](arkts-na-web-selectionmenuoptionsext-i.md) | Defines the selection menu options. |
| [SslErrorEvent](arkts-na-web-sslerrorevent-i.md) | Defines the ssl error event. |
| [UrlRegexRule](arkts-na-web-urlregexrule-i.md) | Defines the regular expression rule. |
| [VerifyPinEvent](arkts-na-web-verifypinevent-i.md) | Defines the event for PIN verification. |
| [WebKeyboardCallbackInfo](arkts-na-web-webkeyboardcallbackinfo-i.md) | Defines the web keyboard callback info related to the onInterceptKeyboardAttach event. |
| [WebKeyboardOptions](arkts-na-web-webkeyboardoptions-i.md) | Defines the web keyboard options when onInterceptKeyboardAttach event return. |
| [WebMediaOptions](arkts-na-web-webmediaoptions-i.md) | Web媒体策略的配置。 |
| [WebOptions](arkts-na-web-weboptions-i.md) | Defines the Web options. |
| [WindowFeatures](arkts-na-web-windowfeatures-i.md) | Defines the window features info for window.open. |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AISessionResultType](arkts-na-web-aisessionresulttype-e.md) | Enum representing the result states for AI session operations. |
| [AISessionType](arkts-na-web-aisessiontype-e.md) | Enum representing the supported types of AI sessions. |
| [AudioSessionType](arkts-na-web-audiosessiontype-e.md) | 应用中Web音频类型。 |
| [BlankScreenDetectionMethod](arkts-na-web-blankscreendetectionmethod-e.md) | The methods can be chosen to detect if current page is blank or nearly blank. |
| [BlurOnKeyboardHideMode](arkts-na-web-bluronkeyboardhidemode-e.md) | Enum type supplied to blurOnKeyboardHideMode for setting the web blurOnKeyboardHide mode. |
| [CacheMode](arkts-na-web-cachemode-e.md) | Enum type supplied to cacheMode for setting the Web cache mode. |
| [CameraCaptureState](arkts-na-web-cameracapturestate-e.md) | Indicates current camera capture state of current web page. |
| [ConsoleMessageSource](arkts-na-web-consolemessagesource-e.md) | The source of console message. |
| [ContextMenuDataMediaType](arkts-na-web-contextmenudatamediatype-e.md) | Defines the context menu media type, related to onContextMenuShow method. |
| [ContextMenuEditStateFlags](arkts-na-web-contextmenueditstateflags-e.md) | Defines the context menu supported event bit flags, related to onContextMenuShow method. |
| [ContextMenuInputFieldType](arkts-na-web-contextmenuinputfieldtype-e.md) | Defines the context menu input field type, related to onContextMenuShow method. |
| [ContextMenuMediaType](arkts-na-web-contextmenumediatype-e.md) | Defines the context menu media type, related to onContextMenuShow method. |
| [ContextMenuSourceType](arkts-na-web-contextmenusourcetype-e.md) | Defines the context menu source type, related to onContextMenuShow method. |
| [CredentialType](arkts-na-web-credentialtype-e.md) | Enum type supplied to [CredentialType](arkts-na-web-credentialtype-e.md#CredentialType) when ClientAuthenticationHandler#confirm being called. |
| [DetectedBlankScreenReason](arkts-na-web-detectedblankscreenreason-e.md) | Enum type supplied to [BlankScreenDetectionEventInfo](arkts-na-web-blankscreendetectioneventinfo-i.md#BlankScreenDetectionEventInfo) when onDetectedBlankScreen being called. |
| [FileSelectorMode](arkts-na-web-fileselectormode-e.md) | Enum type supplied to [FileSelectorParam](arkts-na-web-fileselectorparam-c.md#FileSelectorParam) when onFileSelectorShow being called. |
| [GestureFocusMode](arkts-na-web-gesturefocusmode-e.md) | Enum type supplied to gestureFocusMode for setting the web gesture focus mode. |
| [MessageLevel](arkts-na-web-messagelevel-e.md) | Enum type supplied to [getMessageLevel](arkts-na-web-consolemessage-c.md#getMessageLevel) for receiving the console log level of JavaScript. |
| [MicrophoneCaptureState](arkts-na-web-microphonecapturestate-e.md) | Indicates current microphone capture state of current web page. |
| [MixedMode](arkts-na-web-mixedmode-e.md) | The Web's behavior to load from HTTP or HTTPS. Defaults to MixedMode.None. |
| [NativeEmbedParamStatus](arkts-na-web-nativeembedparamstatus-e.md) | Enum type supplied to [NativeEmbedParamItem](arkts-na-web-nativeembedparamitem-i.md#NativeEmbedParamItem) when onNativeEmbedObjectParamChange being called. |
| [NativeEmbedStatus](arkts-na-web-nativeembedstatus-e.md) | Defines the lifecycle of the same-layer tag. When the same-layer tag exists on the loaded page, CREATE is triggered. When the same-layer tag is moved or is enlarged, **UPDATE **is triggered. When the page exits, DESTROY is triggered. |
| [NavigationPolicy](arkts-na-web-navigationpolicy-e.md) | Enum type for navigationPolicy in OnWindowNewExtEvent. |
| [OverScrollMode](arkts-na-web-overscrollmode-e.md) | Enum type supplied to overScrollMode for setting the web overScroll mode. |
| [PdfLoadResult](arkts-na-web-pdfloadresult-e.md) | 定义PDF页面的加载结果。 |
| [PinVerifyResult](arkts-na-web-pinverifyresult-e.md) | Enum type supplied to [PinVerifyResult](arkts-na-web-pinverifyresult-e.md#PinVerifyResult) when VerifyPinHandler#confirm being called. |
| [ProtectedResourceType](arkts-na-web-protectedresourcetype-e.md) | Defines the accessible resource type, related to onPermissionRequest method. |
| [RenderExitReason](arkts-na-web-renderexitreason-e.md) | Enum type supplied to [renderExitReason](arkts-na-web-onrenderexitedevent-i.md#renderExitReason) when onRenderExited being called. |
| [RenderMode](arkts-na-web-rendermode-e.md) | Enumerates the rendering mode of Web components. By default, the asynchronous rendering mode is used. The asynchronous rendering mode is recommended because it has better performance and lower power consumption. |
| [RenderProcessNotRespondingReason](arkts-na-web-renderprocessnotrespondingreason-e.md) | Enum type supplied to [RenderProcessNotRespondingData](arkts-na-web-renderprocessnotrespondingdata-i.md#RenderProcessNotRespondingData) when onRenderProcessNotResponding is called. |
| [ScrollDirectionalLockType](arkts-na-web-scrolldirectionallocktype-e.md) | Enum defining the scope of directional lock behavior in the WebView, used with enableScrollDirectionalLock. |
| [ScrollbarLayoutPolicy](arkts-na-web-scrollbarlayoutpolicy-e.md) | Defines the layout policy for scrollbars, used with scrollbarLayoutPolicy. |
| [SslError](arkts-na-web-sslerror-e.md) | Enum type supplied to error when onSslErrorEventReceive being called. |
| [ThreatType](arkts-na-web-threattype-e.md) | Enum type supplied to threatType for the website's threat type. |
| [ViewportFit](arkts-na-web-viewportfit-e.md) | Defines the viewport-fit type, related to [ViewportFit](arkts-na-web-viewportfit-e.md#ViewportFit). |
| [WebBypassVsyncCondition](arkts-na-web-webbypassvsynccondition-e.md) | Enum type supplied to bypassVsyncCondition for setting the bypass vsync condition. |
| [WebCaptureMode](arkts-na-web-webcapturemode-e.md) | Web屏幕捕获模式。 |
| [WebDarkMode](arkts-na-web-webdarkmode-e.md) | Enum type supplied to darkMode for setting the web dark mode. |
| [WebElementType](arkts-na-web-webelementtype-e.md) | Defines Web Elements type. |
| [WebKeyboardAppearanceMode](arkts-na-web-webkeyboardappearancemode-e.md) | Enum type supplied to keyboardAppearance for setting the web keyboard appearance mode. |
| [WebKeyboardAvoidMode](arkts-na-web-webkeyboardavoidmode-e.md) | Enum type supplied to keyboardAvoidMode for setting the web keyboard avoid mode. |
| [WebLayoutMode](arkts-na-web-weblayoutmode-e.md) | Enum type supplied to layoutMode for setting the web layout mode. |
| [WebNavigationType](arkts-na-web-webnavigationtype-e.md) | Enum type supplied to [navigationType](arkts-na-web-loadcommitteddetails-i.md#navigationType) for the navigation's type. |
| [WebResponseType](arkts-na-web-webresponsetype-e.md) | ResponseType for contextMenu |
| [WebRotateEffect](arkts-na-web-webrotateeffect-e.md) | Enum type supplied to rotateRenderEffect for setting the effect of rotation. |

### 类型

| 名称 | 说明 |
| --- | --- |
| [MouseInfoCallback](arkts-na-mouseinfocallback-t.md) | The callback when mouse event is triggered in native embed area |
| [OnAISessionCallback](arkts-na-onaisessioncallback-t.md) | Callback type for AI session operations. Used to report the result of session creation or execution. |
| [OnAdsBlockedCallback](arkts-na-onadsblockedcallback-t.md) | The callback of ads block |
| [OnCameraCaptureStateChangeCallback](arkts-na-oncameracapturestatechangecallback-t.md) | The callback when camera capturing state of current page has been changed. |
| [OnContextMenuHideCallback](arkts-na-oncontextmenuhidecallback-t.md) | The callback of custom hide of the context menu. |
| [OnCreateAISession](arkts-na-oncreateaisession-t.md) | Triggered when an AI session is created. Allows custom model initialization and result handling. Return `true` to bypass the default system behavior; return `false` to proceed with the default logic. |
| [OnDestroyAISession](arkts-na-ondestroyaisession-t.md) | Triggered when an AI session is destroyed. Used for cleaning up resources associated with custom AI models. |
| [OnDetectBlankScreenCallback](arkts-na-ondetectblankscreencallback-t.md) | The callback when web engine detects current page is blank or nearly blank. |
| [OnExecuteAIAction](arkts-na-onexecuteaiaction-t.md) | Triggered when executing an AI session action. Enables custom implementation of AI model execution. |
| [OnFirstMeaningfulPaintCallback](arkts-na-onfirstmeaningfulpaintcallback-t.md) | The callback of firstMeaningfulPaint. |
| [OnFirstScreenPaintCallback](arkts-na-onfirstscreenpaintcallback-t.md) | The callback reports the time required for the first screen painting of the current web page. |
| [OnFullScreenEnterCallback](arkts-na-onfullscreenentercallback-t.md) | Web组件进入全屏时触发的回调。 |
| [OnInputmethodAttachedCallback](arkts-na-oninputmethodattachedcallback-t.md) | The callback will be triggered when inputmethod is attached. |
| [OnIntelligentTrackingPreventionCallback](arkts-na-onintelligenttrackingpreventioncallback-t.md) | The callback of Intelligent Tracking Prevention. |
| [OnLargestContentfulPaintCallback](arkts-na-onlargestcontentfulpaintcallback-t.md) | The callback of largestContentfulPaint. |
| [OnMicrophoneCaptureStateChangeCallback](arkts-na-onmicrophonecapturestatechangecallback-t.md) | The callback when microphone capturing state of current page has been changed. |
| [OnNativeEmbedObjectParamChangeCallback](arkts-na-onnativeembedobjectparamchangecallback-t.md) | The callback when the param element which is a child item of the object element has changed. |
| [OnNativeEmbedVisibilityChangeCallback](arkts-na-onnativeembedvisibilitychangecallback-t.md) | The callback of onNativeEmbedVisibilityChange. |
| [OnNavigationEntryCommittedCallback](arkts-na-onnavigationentrycommittedcallback-t.md) | The callback of load committed. |
| [OnOverrideErrorPageCallback](arkts-na-onoverrideerrorpagecallback-t.md) | The callback of onOverrideErrorPage. |
| [OnOverrideUrlLoadingCallback](arkts-na-onoverrideurlloadingcallback-t.md) | The callback of onOverrideUrlLoading. Should not call WebviewController.loadUrl with the request's URL and then return true. |
| [OnRenderProcessNotRespondingCallback](arkts-na-onrenderprocessnotrespondingcallback-t.md) | The callback of render process not responding. |
| [OnRenderProcessRespondingCallback](arkts-na-onrenderprocessrespondingcallback-t.md) | The callback of render process responding. |
| [OnSafeBrowsingCheckResultCallback](arkts-na-onsafebrowsingcheckresultcallback-t.md) | The callback of safe browsing check. |
| [OnSslErrorEventCallback](arkts-na-onsslerroreventcallback-t.md) | The callback of ssl error event. |
| [OnVerifyPinCallback](arkts-na-onverifypincallback-t.md) | The callback of verify pin. |
| [OnViewportFitChangedCallback](arkts-na-onviewportfitchangedcallback-t.md) | The callback of ViewportFit Changed. |
| [TextSelectionChangeCallback](arkts-na-textselectionchangecallback-t.md) | Callback with the selected text after the text selection content changes. |
| [WebKeyboardCallback](arkts-na-webkeyboardcallback-t.md) | The callback of onInterceptKeyboardAttach event. |
| [WebviewController](arkts-na-webviewcontroller-t.md) | Provides methods for controlling the web controller. |

