# Web

Defines Web Component.

<p><strong>API Note</strong>:

<strong>Performance Note</strong>: <p>For details about how to optimize the compilation, resource loading, and JSBridge performance, see Optimizing Web Page Loading <p>When the white screen duration is long due to complex web page parsing, you can enable [optimizeParserBudget](arkts-arkweb-web-comp-attribute.md#optimizeparserbudget) to reduce the first frame rendering content.</p> </p>

## Web

```TypeScript
Web(value: WebOptions)
```

Sets Value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [WebOptions](arkts-arkweb-weboptions-i.md) | Yes | Define web options. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AcceptableFileType](arkts-arkweb-acceptablefiletype-i.md) | Provides the file type information recommended by the file selector, including the MIME type and type array. |
| [AdsBlockedDetails](arkts-arkweb-adsblockeddetails-i.md) | Provides detailed information about the blocked ads when ads are blocked. |
| [AISessionEvent](arkts-arkweb-aisessionevent-i.md) | Custom AI session configuration object, used to define the lifecycle callbacks of an AI session, including creation, execution, and destruction. |
| [BlankScreenDetails](arkts-arkweb-blankscreendetails-i.md) | Provides the result details when a blank screen is detected, including the number of nodes with content. It is suitable for scenarios where analyzing blank screen causes is required, improving blank screen diagnosis detail and accuracy. |
| [BlankScreenDetectionConfig](arkts-arkweb-blankscreendetectionconfig-i.md) | Provides the policy configuration options for blank screen detection, including the detection timing, method, and threshold. It is suitable for scenarios where custom blank screen detection behavior is required, improving blank screen monitoring flexibility and accuracy. |
| [BlankScreenDetectionEventInfo](arkts-arkweb-blankscreendetectioneventinfo-i.md) | Provides the event information when a blank screen is detected, including the URL, reason, and details. It is suitable for scenarios where monitoring page blank screen issues is required, improving blank screen diagnosis accuracy and user experience. |
| [CameraCaptureStateChangeInfo](arkts-arkweb-cameracapturestatechangeinfo-i.md) | Provides the state change information of the camera when the callback is triggered, including the state before the change and the new state. It is suitable for scenarios where monitoring camera state changes is required, improving camera management visibility and user experience. |
| [EmbedOptions](arkts-arkweb-embedoptions-i.md) | Configuration for Web same-layer rendering. Configures Web same-layer rendering options, including support for fixed size and CSS display properties. It is suitable for scenarios where same-layer element rendering optimization is required, improving rendering compatibility and flexibility. |
| [ExpandedMenuItemOptions](arkts-arkweb-expandedmenuitemoptions-i.md) | Custom menu extension item. |
| [FirstMeaningfulPaint](arkts-arkweb-firstmeaningfulpaint-i.md) | Provides detailed information about the first meaningful paint on the web page, including the navigation time and paint time. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience. |
| [FirstScreenPaint](arkts-arkweb-firstscreenpaint-i.md) | Provides the event information when the first screen paint is detected, including the URL and paint time. It is suitable for scenarios where monitoring page first screen rendering performance is required, improving performance optimization accuracy and user experience. |
| [FullScreenEnterEvent](arkts-arkweb-fullscreenenterevent-i.md) | Provides the callback information for the **Web** component to enter the full-screen mode, including the video size and exit handler. It is suitable for scenarios where handling full-screen video is required, improving video playback immersive experience and controllability. |
| [Header](arkts-arkweb-header-i.md) | Request/response header object returned by the **Web** component. It is suitable for scenarios where reading or modifying HTTP headers is required, improving network request handling flexibility and controllability. |
| [IntelligentTrackingPreventionDetails](arkts-arkweb-intelligenttrackingpreventiondetails-i.md) | Provides detailed information about intelligent tracking prevention, including the website domain and tracker domain. It is suitable for scenarios where monitoring ad blocking behavior is required, improving privacy protection transparency and controllability. |
| [JavaScriptProxy](arkts-arkweb-javascriptproxy-i.md) | Defines the JavaScript object to be injected, including the object name, method list, and permission configuration. It is suitable for scenarios where JavaScript-to-native interaction is required, improving cross-language call flexibility and security. |
| [LargestContentfulPaint](arkts-arkweb-largestcontentfulpaint-i.md) | Provides detailed information about the largest contentful paint on the web page, including the navigation time and various paint times. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience. |
| [LoadCommittedDetails](arkts-arkweb-loadcommitteddetails-i.md) | Provides detailed information about the web page that has been submitted for redirection, including whether it is the main document, the navigation type, and more. It is suitable for scenarios where monitoring page navigation behavior is required, improving navigation state management accuracy and user experience. |
| [MicrophoneCaptureStateChangeInfo](arkts-arkweb-microphonecapturestatechangeinfo-i.md) | Provides the state change information of the microphone when the callback is triggered, including the state before the change and the state after the change. It is suitable for scenarios where monitoring microphone state changes is required, improving microphone management visibility and user experience. |
| [NativeEmbedDataInfo](arkts-arkweb-nativeembeddatainfo-i.md) | Provides detailed information about the changes of the same-layer tag lifecycle, including the status and tag information. It is suitable for scenarios where monitoring same-layer element lifecycle is required, improving rendering state management accuracy and user experience. |
| [NativeEmbedInfo](arkts-arkweb-nativeembedinfo-i.md) | Provides detailed information about the same-layer tag, including the ID, type, size, and location. It is suitable for scenarios where obtaining same-layer element attributes is required, improving same-layer rendering customization and user experience. |
| [NativeEmbedMouseInfo](arkts-arkweb-nativeembedmouseinfo-i.md) | Provides detailed information about clicking or touching and holding a same-layer tag using the mouse or touchpad, including the tag ID and mouse event. It is suitable for scenarios where handling same-layer element mouse interaction is required, improving mouse experience customization and flexibility. |
| [NativeEmbedParamDataInfo](arkts-arkweb-nativeembedparamdatainfo-i.md) | Provides detailed information about the same-layer tag when the **param** element embedded in the **object** tag changes, including the tag ID and parameter items. It is suitable for scenarios where monitoring param element changes is required, improving same-layer element management flexibility and accuracy. |
| [NativeEmbedParamItem](arkts-arkweb-nativeembedparamitem-i.md) | Provides detailed information about the **param** element embedded in the same-layer rendering tag **object**, including the status and parameters. It is suitable for scenarios where monitoring param element changes is required, improving same-layer element management flexibility and accuracy. |
| [NativeEmbedTouchInfo](arkts-arkweb-nativeembedtouchinfo-i.md) | Provides detailed information about finger touch on a same-layer tag, including the tag ID and touch event. It is suitable for scenarios where handling same-layer element touch interaction is required, improving touch experience customization and flexibility. |
| [NativeEmbedVisibilityInfo](arkts-arkweb-nativeembedvisibilityinfo-i.md) | Provides visibility information about the same-layer tag, including the visibility status and tag ID. It is suitable for scenarios where monitoring same-layer element visibility is required, improving rendering state management accuracy and user experience. |
| [NativeMediaPlayerConfig](arkts-arkweb-nativemediaplayerconfig-i.md) | Configures the [enableNativeMediaPlayer](arkts-arkweb-web-comp-attribute.md#enablenativemediaplayer) API for the app to take over web page media playback, supporting whether to enable it and whether to override web page content. It is suitable for scenarios where custom media playback behavior is required, improving media playback integration and user experience. |
| [NestedScrollOptionsExt](arkts-arkweb-nestedscrolloptionsext-i.md) | Sets the nested scrolling rules of the **Web** component, supporting scrolling options in four directions: up, down, left, and right. |
| [OnAlertEvent](arkts-arkweb-onalertevent-i.md) | Defines the callback used when a web page triggers **alert()**. |
| [OnAudioStateChangedEvent](arkts-arkweb-onaudiostatechangedevent-i.md) | Defines the callback information triggered when the audio playback status on the web page changes, including the playback status. It is suitable for scenarios where monitoring audio playback behavior is required, improving audio management visibility and user experience. |
| [OnBeforeUnloadEvent](arkts-arkweb-onbeforeunloadevent-i.md) | Defines the callback triggered when the user is about to leave the current page in refresh or close scenarios. It is suitable for scenarios such as form editing, allowing developers to intercept the leave action and display a confirmation dialog, thereby preventing accidental loss of unsubmitted user data. |
| [OnClientAuthenticationEvent](arkts-arkweb-onclientauthenticationevent-i.md) | Defines the callback information triggered when an SSL client certificate is required, including the host, port, and key type. It is suitable for scenarios where handling client certificate authentication is required, improving authentication process flexibility and security. |
| [OnConfirmEvent](arkts-arkweb-onconfirmevent-i.md) | Defines the callback used when a web page triggers **confirm()**. |
| [OnConsoleEvent](arkts-arkweb-onconsoleevent-i.md) | Represents the callback invoked to notify the host application of a JavaScript console message. |
| [OnContextMenuShowEvent](arkts-arkweb-oncontextmenushowevent-i.md) | Defines the callback information triggered during a call to allow for the display of a custom context menu. |
| [OnDataResubmittedEvent](arkts-arkweb-ondataresubmittedevent-i.md) | Defines the callback information triggered when the web form data can be resubmitted, including the submission handler. It is suitable for scenarios where handling form retry submission is required, improving form interaction reliability and user experience. |
| [OnDownloadStartEvent](arkts-arkweb-ondownloadstartevent-i.md) | Defines the callback information for notifying the host app that a file download has started, including the URL, user agent, and file details. It is suitable for scenarios where monitoring and managing file downloads are required, improving download process controllability and user experience. |
| [OnErrorReceiveEvent](arkts-arkweb-onerrorreceiveevent-i.md) | Defines the callback information triggered when an error occurs during web page loading, including the request and error details. It is suitable for scenarios where monitoring and handling web page loading errors are required, improving error handling timeliness and user experience. |
| [OnFaviconReceivedEvent](arkts-arkweb-onfaviconreceivedevent-i.md) | Defines the callback information triggered when the app receives a new favicon, including the icon PixelMap object. It is suitable for scenarios where obtaining web page favicons is required, improving icon management flexibility and user experience. |
| [OnFirstContentfulPaintEvent](arkts-arkweb-onfirstcontentfulpaintevent-i.md) | Defines the callback information for the first content paint on the web page, including the load time and paint time. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience. |
| [OnGeolocationShowEvent](arkts-arkweb-ongeolocationshowevent-i.md) | Defines the callback information triggered when a request to obtain the geolocation information is received, including the origin information and geolocation object. It is suitable for scenarios where handling geolocation permissions is required. |
| [OnHttpAuthRequestEvent](arkts-arkweb-onhttpauthrequestevent-i.md) | Defines the callback information triggered when an HTTP authentication request is received, including the host and realm information. It is suitable for scenarios where handling HTTP authentication is required, improving authentication process flexibility and security. |
| [OnHttpErrorReceiveEvent](arkts-arkweb-onhttperrorreceiveevent-i.md) | Defines the callback information triggered when the web page receives an HTTP error during resource loading, including the request and response details. It is suitable for scenarios where monitoring and handling HTTP errors are required, improving network error diagnosis accuracy and user experience. |
| [OnInterceptRequestEvent](arkts-arkweb-oninterceptrequestevent-i.md) | Defines the callback information triggered before the **Web** component loads a URL, including the request details. It is suitable for scenarios where intercepting or modifying network requests is required, improving request control flexibility and security. |
| [OnLoadFinishedEvent](arkts-arkweb-onloadfinishedevent-i.md) | Defines the callback information triggered when the web page loading ends, including the page URL. It is suitable for scenarios where monitoring page loading completion is required, improving page lifecycle management capabilities. |
| [OnLoadInterceptEvent](arkts-arkweb-onloadinterceptevent-i.md) | Defines the callback information triggered when resource loading is intercepted, including the request details. It is suitable for scenarios where intercepting or handling resource loading is required, improving resource control flexibility and security. |
| [OnLoadStartedEvent](arkts-arkweb-onloadstartedevent-i.md) | Defines the callback information triggered when the web page loading begins, including the page URL. It is suitable for scenarios where monitoring page loading start is required, improving page lifecycle management capabilities. |
| [OnOverScrollEvent](arkts-arkweb-onoverscrollevent-i.md) | Defines the callback information triggered when the web page is overscrolled, including the horizontal and vertical offsets. |
| [OnPageBeginEvent](arkts-arkweb-onpagebeginevent-i.md) | Defines the callback information triggered when the web page loading begins, including the page URL. It is suitable for scenarios where monitoring page loading start is required, improving page lifecycle management capabilities. |
| [OnPageEndEvent](arkts-arkweb-onpageendevent-i.md) | Defines the callback information triggered when the web page loading ends, including the page URL. It is suitable for scenarios where monitoring page loading completion is required, improving page lifecycle management capabilities. |
| [OnPageVisibleEvent](arkts-arkweb-onpagevisibleevent-i.md) | Represents the callback invoked when the old page is not displayed and the new page is about to be visible. |
| [OnPdfLoadEvent](arkts-arkweb-onpdfloadevent-i.md) | Defines the function triggered when the PDF loading is successful or fails. |
| [OnPdfScrollEvent](arkts-arkweb-onpdfscrollevent-i.md) | Defines the callback function triggered when the PDF page is scrolled to the bottom. |
| [OnPermissionRequestEvent](arkts-arkweb-onpermissionrequestevent-i.md) | Defines the callback information triggered when a permission request is received, including the request details. It is suitable for scenarios where handling permission grants is required, improving permission management flexibility and security. |
| [OnProgressChangeEvent](arkts-arkweb-onprogresschangeevent-i.md) | Defines the callback information triggered when the web page loading progress changes, including the new progress value. It is suitable for scenarios where monitoring page loading progress is required, improving loading process visibility and user experience. |
| [OnPromptEvent](arkts-arkweb-onpromptevent-i.md) | Defines the callback used when a web page triggers **prompt()**. |
| [OnRefreshAccessedHistoryEvent](arkts-arkweb-onrefreshaccessedhistoryevent-i.md) | Defines the callback information triggered when navigation is complete, including the URL and refresh status. It is suitable for scenarios where monitoring page navigation history is required, improving navigation behavior tracking accuracy and user experience. |
| [OnRenderExitedEvent](arkts-arkweb-onrenderexitedevent-i.md) | Defines the callback triggered when the rendering process exits. It is suitable for scenarios where monitoring rendering process exceptions is required, improving rendering stability and troubleshooting efficiency. |
| [OnResourceLoadEvent](arkts-arkweb-onresourceloadevent-i.md) | Defines the callback information triggered when a URL is loaded, including the resource URL. It is suitable for scenarios where monitoring resource loading behavior is required, improving resource management visibility and performance optimization. |
| [OnScaleChangeEvent](arkts-arkweb-onscalechangeevent-i.md) | Represents the callback invoked when the display scale of this page changes. |
| [OnScreenCaptureRequestEvent](arkts-arkweb-onscreencapturerequestevent-i.md) | Defines the callback information triggered when a screen capture request is received. It is suitable for scenarios where handling screen recording permissions is required, improving screen recording process controllability and security. |
| [OnScrollEvent](arkts-arkweb-onscrollevent-i.md) | Defines the callback information triggered when the scrollbar scrolls to a specified position, including the horizontal and vertical offsets. |
| [OnSearchResultReceiveEvent](arkts-arkweb-onsearchresultreceiveevent-i.md) | Defines the callback information for the search result on the web page, including the match ordinal and total count. It is suitable for scenarios where monitoring in-page search behavior is required, improving search interaction visibility and user experience. |
| [OnShowFileSelectorEvent](arkts-arkweb-onshowfileselectorevent-i.md) | Defines the callback information for the file selector result, including the result and parameter details. |
| [OnSslErrorEventReceiveEvent](arkts-arkweb-onsslerroreventreceiveevent-i.md) | Defines the callback information triggered when the web page receives an SSL error, including the error code and certificate chain. It is suitable for scenarios where handling SSL errors is required, improving security exception monitoring and handling capabilities. |
| [OnTitleReceiveEvent](arkts-arkweb-ontitlereceiveevent-i.md) | Defines the callback information triggered when the document title of the web page is changed, including the title content and source. It is suitable for scenarios where monitoring page title changes is required, improving page information real-time performance and user experience. |
| [OnTouchIconUrlReceivedEvent](arkts-arkweb-ontouchiconurlreceivedevent-i.md) | Defines the callback information triggered when an apple-touch-icon URL is received, including the URL and precomposed status. It is suitable for scenarios where obtaining web page icons is required, improving icon management flexibility and user experience. |
| [OnWindowNewEvent](arkts-arkweb-onwindownewevent-i.md) | Defines the callback triggered when the web page requests the user to create a window. Starting from API version 23, you can use [OnWindowNewExtEvent](arkts-arkweb-onwindownewextevent-i.md) to obtain more window information. |
| [OnWindowNewExtEvent](arkts-arkweb-onwindownewextevent-i.md) | Defines the callback information triggered when the web page requests to create a window, including the window feature information and window opening method. It is suitable for scenarios where fine-grained control of new window behavior is required, improving window management customization and user experience. |
| [PreviewMenuOptions](arkts-arkweb-previewmenuoptions-i.md) | Configures preview menu options, supporting the vibration effect when the menu pops up. It is suitable for scenarios where enhanced menu interaction feedback is required, improving user experience. |
| [RenderProcessNotRespondingData](arkts-arkweb-renderprocessnotrespondingdata-i.md) | Provides detailed information about the unresponsive rendering process. It is suitable for scenarios where diagnosing rendering process exceptions is required, improving troubleshooting accuracy and efficiency. |
| [ScreenCaptureConfig](arkts-arkweb-screencaptureconfig-i.md) | Provides the web screen capture configuration options, including the capture mode. It is suitable for scenarios where custom web page screen recording behavior is required, improving screen recording flexibility and user experience. |
| [ScriptItem](arkts-arkweb-scriptitem-i.md) | Describes the **ScriptItem** object registered with the **Web** component through the [javaScriptOnDocumentStart](arkts-arkweb-web-comp-attribute.md#javascriptondocumentstart) attribute. |
| [SelectionMenuOptionsExt](arkts-arkweb-selectionmenuoptionsext-i.md) | Represents the selection menu option extension. |
| [SslErrorEvent](arkts-arkweb-sslerrorevent-i.md) | Callback details triggered when an SSL error occurs during resource loading by the user, including the URL, error type, and certificate chain. It is suitable for scenarios where detailed analysis of SSL errors is required, improving security issue diagnosis and troubleshooting efficiency. |
| [UrlRegexRule](arkts-arkweb-urlregexrule-i.md) | Defines the URL regular expression rule. |
| [VerifyPinEvent](arkts-arkweb-verifypinevent-i.md) | Defines the callback triggered to notify the user of PIN verification. |
| [WebKeyboardCallbackInfo](arkts-arkweb-webkeyboardcallbackinfo-i.md) | Input parameters of the callback used to intercept the soft keyboard started from editable elements on a web page, including WebKeyboardController and the attributes of the editable element. It is suitable for scenarios where custom keyboard interaction is required, improving input experience customization and flexibility. |
| [WebKeyboardOptions](arkts-arkweb-webkeyboardoptions-i.md) | Return value of the callback that intercepts the soft keyboard started from editable elements on the web page, including the keyboard type and custom keyboard. It is suitable for scenarios where controlling soft keyboard behavior is required. |
| [WebMediaOptions](arkts-arkweb-webmediaoptions-i.md) | Configures the media policy of the **Web** component, including the audio playback continuation validity period, audio exclusive mode, and more. It is suitable for scenarios where audio playback experience optimization and multi- instance audio management are required, improving media playback stability and user experience. |
| [WebOptions](arkts-arkweb-weboptions-i.md) | Defines Web options through the [API](../../../reference/apis-arkweb/arkts-basic-components-web.md#api), including the web page resource URL, controller, rendering mode, and more. |
| [WindowFeatures](arkts-arkweb-windowfeatures-i.md) | Provides the feature information of the new window requested to be created by the web page, including the size and location. It is suitable for scenarios where precise control of new window attributes is required, improving window layout accuracy and user experience. |

### Types

| Name | Description |
| --- | --- |
| [MouseInfoCallback](arkts-arkweb-mouseinfocallback-t.md) | This callback is triggered when a same-layer tag is clicked using the mouse or touchpad. |
| [OnAdsBlockedCallback](arkts-arkweb-onadsblockedcallback-t.md) | Defines a callback invoked when ads are blocked on the web page. |
| [OnAISessionCallback](arkts-arkweb-onaisessioncallback-t.md) | AI session operation result callback function type. Used to report the result of session creation or execution. |
| [OnCameraCaptureStateChangeCallback](arkts-arkweb-oncameracapturestatechangecallback-t.md) | This callback is triggered when the camera device state of the page changes. |
| [OnContextMenuHideCallback](arkts-arkweb-oncontextmenuhidecallback-t.md) | Defines a callback invoked when the context menu is hidden. |
| [OnCreateAISession](arkts-arkweb-oncreateaisession-t.md) | AI session creation callback function type. Allows custom model initialization and result processing. |
| [OnDestroyAISession](arkts-arkweb-ondestroyaisession-t.md) | AI session destruction callback function type. Used to clean up resources associated with the custom AI model. |
| [OnDetectBlankScreenCallback](arkts-arkweb-ondetectblankscreencallback-t.md) | Defines a callback triggered when a blank screen is detected. |
| [OnExecuteAIAction](arkts-arkweb-onexecuteaiaction-t.md) | AI session execution operation callback function type. Used to implement custom AI model execution. |
| [OnFirstMeaningfulPaintCallback](arkts-arkweb-onfirstmeaningfulpaintcallback-t.md) | Callback for measuring the first meaningful paint of the main content on the page. This callback is triggered when the page finishes loading the main content. Compared with OnLargestContentfulPaintCallback, which focuses on the paint time of the largest content element, and OnFirstScreenPaintCallback, which focuses on the rendering completion of the first screen's visible content, this callback focuses more on whether the main content has finished loading, making it suitable for evaluating the loading experience of user-visible content. |
| [OnFirstScreenPaintCallback](arkts-arkweb-onfirstscreenpaintcallback-t.md) | This callback is triggered when the first screen rendering is detected to be complete. Compared with OnFirstMeaningfulPaintCallback, which focuses on the completion of main content loading, and OnLargestContentfulPaintCallback, which focuses on the paint time of the largest content element, this callback focuses more on the rendering completion time of the first screen's visible content, making it suitable for evaluating the user's first visual experience. |
| [OnFullScreenEnterCallback](arkts-arkweb-onfullscreenentercallback-t.md) | Defines a callback invoked when the **Web** component enters full screen mode. |
| [OnInputmethodAttachedCallback](arkts-arkweb-oninputmethodattachedcallback-t.md) | This callback is triggered when the input method is detected to be successfully attached. |
| [OnIntelligentTrackingPreventionCallback](arkts-arkweb-onintelligenttrackingpreventioncallback-t.md) | Defines a callback invoked when the tracker cookie is intercepted. |
| [OnLargestContentfulPaintCallback](arkts-arkweb-onlargestcontentfulpaintcallback-t.md) | Callback triggered when the largest content area is painted on the web page. Used to obtain performance measurement information for the largest content paint. Applicable to scenarios such as monitoring web page loading performance and optimizing page rendering speed. Compared with OnFirstMeaningfulPaintCallback, which focuses on the completion of main content loading, and OnFirstScreenPaintCallback, which focuses on the rendering completion of the first screen's visible content, this callback focuses on the paint time of the largest content element, making it suitable for evaluating page rendering completeness and performance bottlenecks. |
| [OnMicrophoneCaptureStateChangeCallback](arkts-arkweb-onmicrophonecapturestatechangecallback-t.md) | Defines a callback triggered when the microphone state of the page changes. |
| [OnNativeEmbedObjectParamChangeCallback](arkts-arkweb-onnativeembedobjectparamchangecallback-t.md) | Defines a callback triggered when the **param** element embedded in the same-layer rendered **object** tag is added, modified, or deleted. |
| [OnNativeEmbedVisibilityChangeCallback](arkts-arkweb-onnativeembedvisibilitychangecallback-t.md) | Defines a callback invoked when the visibility of a same-layer tag changes. |
| [OnNavigationEntryCommittedCallback](arkts-arkweb-onnavigationentrycommittedcallback-t.md) | Defines a callback invoked when a navigation entry is submitted. |
| [OnOverrideErrorPageCallback](arkts-arkweb-onoverrideerrorpagecallback-t.md) | Defines a callback of **onOverrideErrorPage**. This callback is triggered when a web page fails to be loaded. |
| [OnOverrideUrlLoadingCallback](arkts-arkweb-onoverrideurlloadingcallback-t.md) | Callback used to intercept URL loading requests. It can block the loading of specific URLs or perform custom processing. Applicable to scenarios such as intercepting ads and blocking redirects to malicious websites. |
| [OnRenderProcessNotRespondingCallback](arkts-arkweb-onrenderprocessnotrespondingcallback-t.md) | Defines a callback invoked when the rendering process does not respond. |
| [OnRenderProcessRespondingCallback](arkts-arkweb-onrenderprocessrespondingcallback-t.md) | Defines a callback invoked when the rendering process transitions back to a normal operating state from an unresponsive state. |
| [OnSafeBrowsingCheckResultCallback](arkts-arkweb-onsafebrowsingcheckresultcallback-t.md) | Defines a callback invoked by a website safe browsing check. |
| [OnSslErrorEventCallback](arkts-arkweb-onsslerroreventcallback-t.md) | Callback invoked when an SSL error occurs during resource loading. Returns detailed information about the SSL error. |
| [OnVerifyPinCallback](arkts-arkweb-onverifypincallback-t.md) | Callback triggered to notify the user of PIN authentication. |
| [OnViewportFitChangedCallback](arkts-arkweb-onviewportfitchangedcallback-t.md) | Defines a callback invoked when the **viewport-fit** configuration in the web page's **\&lt;meta&gt;** tag changes. |
| [TextSelectionChangeCallback](arkts-arkweb-textselectionchangecallback-t.md) | Callback for onTextSelectionChange. Triggered when the text selection content changes. |
| [WebKeyboardCallback](arkts-arkweb-webkeyboardcallback-t.md) | Defines a callback to intercept the soft keyboard initiated from editable elements on a web page. This event is typically called when the **\&lt;input&gt;** tag on the web page is clicked. |
| [WebviewController](arkts-arkweb-webviewcontroller-t.md) | Defines methods for the web controller. |

### Enums

| Name | Description |
| --- | --- |
| [AISessionResultType](arkts-arkweb-aisessionresulttype-e.md) | Defines the result status of AI session operations. |
| [AISessionType](arkts-arkweb-aisessiontype-e.md) | Defines the supported AI session types. |
| [AudioSessionType](arkts-arkweb-audiosessiontype-e.md) | Defines the web audio types in the app, which control the audio stream type and behavior of web audio and help developers optimize the audio experience based on app scenarios, such as supporting simultaneous playback of web game sounds and system music. |
| [BlankScreenDetectionMethod](arkts-arkweb-blankscreendetectionmethod-e.md) | Defines the detection strategy methods used for blank screen detection, which specify the specific algorithms and points for page content detection and help developers strike a balance between detection accuracy and performance overhead, enabling timely identification of page rendering anomalies. |
| [BlurOnKeyboardHideMode](arkts-arkweb-bluronkeyboardhidemode-e.md) | Enumerates whether the **Web** component loses focus when the soft keyboard is hidden. |
| [CacheMode](arkts-arkweb-cachemode-e.md) | Enumerates the cache modes. |
| [CameraCaptureState](arkts-arkweb-cameracapturestate-e.md) | Defines the camera capture states, which identify the current working status of the camera and help developers monitor camera resource usage in real time, optimizing resource management and user privacy protection. |
| [ConsoleMessageSource](arkts-arkweb-consolemessagesource-e.md) | Enumerates the log sources of the console messages. |
| [ContextMenuDataMediaType](arkts-arkweb-contextmenudatamediatype-e.md) | Enumerates the media types that trigger the context menu (enhanced type obtaining capability). |
| [ContextMenuEditStateFlags](arkts-arkweb-contextmenueditstateflags-e.md) | Enumerates the context menu edit state flags. This enum can be used in bitwise OR mode. For example, to support **CAN_CUT**, **CAN_COPY**, and **CAN_SELECT_ALL** at the same time, use **CAN_CUT | [CAN_COPY](arkts-arkweb-contextmenueditstateflags-e.md) | CAN_SELECT_ALL** or **11**. |
| [ContextMenuInputFieldType](arkts-arkweb-contextmenuinputfieldtype-e.md) | Enumerates the input field types. |
| [ContextMenuMediaType](arkts-arkweb-contextmenumediatype-e.md) | Enumerates the media types that trigger the context menu. |
| [ContextMenuSourceType](arkts-arkweb-contextmenusourcetype-e.md) | Enumerates the event source types that trigger the context menu. |
| [CredentialType](arkts-arkweb-credentialtype-e.md) | Defines the credential types used for identity authentication. |
| [DetectedBlankScreenReason](arkts-arkweb-detectedblankscreenreason-e.md) | Defines the specific reasons for the blank screen, which identify the underlying causes of page blank screen phenomena and help developers quickly locate the source of issues, improving the efficiency of troubleshooting page loading problems and user experience. |
| [FileSelectorMode](arkts-arkweb-fileselectormode-e.md) | Defines the file selector mode, which controls how the file selector is opened and behaves, helping developers implement file operation scenarios such as file upload. |
| [GestureFocusMode](arkts-arkweb-gesturefocusmode-e.md) | Enumerates the focus modes. |
| [HitTestType](arkts-arkweb-hittesttype-e.md) | Enumerates the test result types of the click event. |
| [MessageLevel](arkts-arkweb-messagelevel-e.md) | Enumerates the information levels of the console messages. |
| [MicrophoneCaptureState](arkts-arkweb-microphonecapturestate-e.md) | Defines the microphone capture states, which identify the current working status of the microphone and help developers monitor microphone resource usage in real time, optimizing resource management and user privacy protection. |
| [MixedMode](arkts-arkweb-mixedmode-e.md) | Enumerates the mixed content modes. |
| [NativeEmbedParamStatus](arkts-arkweb-nativeembedparamstatus-e.md) | Enumerates the status change types of the **param** element embedded in the same-layer rendering tag **object**. **ADD** is triggered when the **param** element is added, **UPDATE** is triggered when it is modified, and **DELETE** is triggered when it is deleted. |
| [NativeEmbedStatus](arkts-arkweb-nativeembedstatus-e.md) | Enumerates the lifecycles of the same-layer tag. When a same-layer tag exists on the loaded page, **CREATE** is triggered. When a same-layer tag is moved or is enlarged, **UPDATE** is triggered. When the page exits, **DESTROY** is triggered. |
| [NavigationPolicy](arkts-arkweb-navigationpolicy-e.md) | Defines the modes of opening a new window in the WebView, including pop-up windows, new windows, foreground tabs, and background tabs. |
| [OverScrollMode](arkts-arkweb-overscrollmode-e.md) | Enumerates whether to enable overscroll mode. |
| [PdfLoadResult](arkts-arkweb-pdfloadresult-e.md) | Defines the PDF page loading results, which identify various states and error types during PDF file loading and help developers diagnose errors and provide user prompts when PDF display fails. |
| [PinVerifyResult](arkts-arkweb-pinverifyresult-e.md) | Defines the PIN verification results, which identify the execution status of PIN verification. |
| [ProtectedResourceType](arkts-arkweb-protectedresourcetype-e.md) | Defines the types of protected resources that the Web component needs to access. It is used to control access permissions for sensitive resources such as MIDI, camera, microphone, and sensors, helping developers provide rich web functionality while protecting user privacy. |
| [RenderExitReason](arkts-arkweb-renderexitreason-e.md) | Enumerates the reasons why the rendering process exits. |
| [RenderMode](arkts-arkweb-rendermode-e.md) | Enumerates the rendering modes of the **Web** component. By default, the asynchronous rendering mode is used. |
| [RenderProcessNotRespondingReason](arkts-arkweb-renderprocessnotrespondingreason-e.md) | Enumerates the reasons why the rendering process does not respond. |
| [ScrollbarLayoutPolicy](arkts-arkweb-scrollbarlayoutpolicy-e.md) | Defines the enumeration type for scrollbar layout mode control parameters. |
| [ScrollDirectionalLockType](arkts-arkweb-scrolldirectionallocktype-e.md) | Defines the scenario types for scroll direction locking. |
| [SslError](arkts-arkweb-sslerror-e.md) | Enumerates the error codes returned by **onSslErrorEventReceive** API. |
| [ThreatType](arkts-arkweb-threattype-e.md) | Enumerates the website threat types. |
| [ViewportFit](arkts-arkweb-viewportfit-e.md) | Enumerates the viewport types available for **viewport-fit** in the web page **\&lt;meta&gt;** tag. |
| [WebBypassVsyncCondition](arkts-arkweb-webbypassvsynccondition-e.md) | Enumerates whether to allow the rendering process to bypass the vsync scheduling. |
| [WebCaptureMode](arkts-arkweb-webcapturemode-e.md) | Enumerates the web screen capture modes. |
| [WebDarkMode](arkts-arkweb-webdarkmode-e.md) | Configures the web dark mode, which controls the dark theme display of web content and helps developers improve visual experience and readability based on user preferences and system themes. |
| [WebElementType](arkts-arkweb-webelementtype-e.md) | Enumerates the web element types. |
| [WebKeyboardAppearanceMode](arkts-arkweb-webkeyboardappearancemode-e.md) | Defines the input method immersive mode in the WebView, which controls the display style of the soft keyboard and helps developers provide a consistent visual experience based on the app theme and user preferences. It supports the default appearance, system-following, light immersive, and dark immersive styles. |
| [WebKeyboardAvoidMode](arkts-arkweb-webkeyboardavoidmode-e.md) | Enumerates the soft keyboard avoidance modes. |
| [WebLayoutMode](arkts-arkweb-weblayoutmode-e.md) | Configures the web layout mode, which controls the page layout of web content and helps developers optimize web page adaptability and user experience based on screen size and display requirements. |
| [WebNavigationType](arkts-arkweb-webnavigationtype-e.md) | Enumerates the navigation types. |
| [WebResponseType](arkts-arkweb-webresponsetype-e.md) | Enumerates the response types of the menu. |
| [WebRotateEffect](arkts-arkweb-webrotateeffect-e.md) | Enumerates the modes in which the component's content is rendered to fit the new size during its width and height animation process when the component is rotated. |
