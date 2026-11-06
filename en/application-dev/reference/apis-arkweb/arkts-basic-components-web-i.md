# Interfaces (Others)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=37f8010684f98f039dd93a2bbbd1faa73c74fcbb translatedAt=2026-08-07T04:40:28.641Z pushedAt=2026-08-12T01:46:50.748Z -->

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual device.

## WebOptions

Defines Web options through the [APIs](./arkts-basic-components-web.md#apis), including the web page resource URL, controller, rendering mode, and more.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type                         | Read-Only    | Optional  | Description                                    |
| ---------- | ------------------------------|---- | ---- | ---------------------------------------- |
| src        | string \| [Resource](../apis-arkui/arkui-ts/ts-types.md#resource)   | No    | No    | Web page resource address. If a local resource file is accessed, use the resource protocol or $rawfile resource reference. If a local resource file in the sandbox path outside the app package is loaded (HTML and TXT file types are supported), use file:// sandbox file path.<br>src cannot be dynamically changed through a state variable (for example, @State). To change the address, reload the page through [loadUrl()](./arkts-apis-webview-WebviewController.md#loadurl). |
| controller | [WebController](./arkts-basic-components-web-WebController.md) \| [WebviewController](./arkts-apis-webview-WebviewController.md)  | No    | No   | Controller used to control various behaviors of the Web component, including page navigation, lifecycle state, JavaScript interaction, etc. Since API version 9, WebController is no longer maintained. It is recommended to use [WebviewController](./arkts-basic-components-web-t.md#webviewcontroller9) instead. |
| renderMode<sup>12+</sup> | [RenderMode](./arkts-basic-components-web-e.md#rendermode12)| No    | Yes   | Rendering mode of the current Web component. `RenderMode.ASYNC_RENDER` indicates asynchronous rendering, and `RenderMode.SYNC_RENDER` indicates synchronous rendering. Default value: `RenderMode.ASYNC_RENDER`. This mode does not support dynamic adjustment. |
| incognitoMode<sup>11+</sup> | boolean | No    | Yes | Whether the current Webview is created in incognito mode. The value **true** indicates incognito mode, and **false** indicates normal mode.<br>Default value: **false**.<br>The value is **false** when undefined or null is passed in.<!--RP1--><!--RP1End--> |
| sharedRenderProcessToken<sup>12+</sup> | string | No    | Yes | Token that specifies the shared render process for the current Web component. In multi-render-process mode, Web components with the same token preferentially attempt to reuse the bound render process. The binding occurs during the initialization phase of the render process. When a render process has no associated Web component, its binding relationship is removed.<br>Default value: **""**.  |
| emulateTouchFromMouseEvent<sup>22+</sup> | boolean | No    | Yes |  Whether to convert mouse events to touch events. The value **true** indicates that mouse events are converted to touch events, which is suitable for scenarios where touch and mouse interaction behaviors need to be unified; **false** indicates that mouse events are not converted to touch events.<br>Default value: **false**. |

## WebMediaOptions<sup>10+</sup>

Configures the media policy of the **Web** component, including the audio playback continuation validity period, audio exclusive mode, and more. It is suitable for scenarios where audio playback experience optimization and multi-instance audio management are required, improving media playback stability and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional | Description                                      |
| -------------- | ------- | ---- | ---- | ---------------------------------------- |
| resumeInterval | number | No | Yes | Validity period during which Web audio and video paused by other apps can automatically resume playback, in seconds. Value range: [-2147483648, 2147483647]. The value **0** means no automatic resumption; a value greater than **0** means an attempt to resume within the specified period; a value less than **0** means an attempt to resume within an unlimited period. Due to approximation, this validity period may have an error within one second.<br>**NOTE**<br>After an HLS video is interrupted, it will automatically resume when returning to the foreground, regardless of this time setting.<br/>Default value: **0**.|
| audioExclusive | boolean | No | Yes | Whether the audio of multiple Web instances in an app is exclusive.<br>The value **true** means the audio of multiple Web instances in an app is exclusive, and **false** means the opposite.<br>Default value: **true**.|
| audioSessionType<sup>20+</sup> | [AudioSessionType](./arkts-basic-components-web-e.md#audiosessiontype20) | No | Yes | Web audio type in the app. The default value corresponds to STREAM_USAGE_MUSIC in the system audio stream type [StreamUsage](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage). Used to change the mapping between the component audio type and the system audio type, affecting the ArkWeb audio focus policy.|

## ScriptItem<sup>11+</sup>

Describes the **ScriptItem** object registered with the **Web** component through the [javaScriptOnDocumentStart](./arkts-basic-components-web-attributes.md#javascriptondocumentstart11) attribute.

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Type          | Read-Only| Optional  | Description          |
| ----------- | -------------- | --- | ------|--------------- |
| script      | string         | No |  No   | JavaScript script to be registered and executed.|
| scriptRules | Array\<string> | No  |  No    | A set of matching rules for allowed sources.<br>1. To allow URLs from all sources, use the wildcard "\*".<br>2. To perform exact matching, specify the website address, for example, "https:\//www\.example.com".<br>3. To perform fuzzy matching, use the "\*" wildcard, for example, "https://*.example.com". Patterns such as "x.*.y.com" and "\*foobar.com" are not allowed.<br>4. If the source is an IP address, use rule 2.<br>5. For protocols other than HTTP/HTTPS (custom protocols), exact matching and fuzzy matching are not supported, and the rule must end with `://`, for example, "resource://".<br>6. In a set of scriptRules, if any rule does not meet the above requirements, the entire set of scriptRules does not take effect. |
| urlRegexRules<sup>23+</sup>  | Array\<[UrlRegexRule](./arkts-basic-components-web-i.md#urlregexrule23)\> | No |  Yes   | Regular expression matching rules for allowed sources. **urlRegexRules** is used for matching only when **scriptRules** is set to **[]**.<br> **Model restriction**: This API can be used only in the stage model.|

## UrlRegexRule<sup>23+</sup>

Defines the URL regular expression rule.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Type | Read-Only| Optional| Description           |
| ----------- | ------ | --- | -----|---------------- |
| secondLevelDomain | string | No | No   | Exact match of the second-level domain. For example, the second-level domain name of "https://www.example.com" is **example.com**, and that of "https://www.example.com.cn" is **example.com.cn**. If the URL does not have a second-level domain name, the value is empty.|
| rule | string | No | No   | URL regular expression. URL regular expression matching is performed only after **secondLevelDomain** is matched successfully.|

## NestedScrollOptionsExt<sup>14+</sup>

Sets the nested scrolling rules of the **Web** component, supporting scrolling options in four directions: up, down, left, and right.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type              | Read-Only| Optional| Description                  |
| -------------- | ---------------- | ---- | ---- | -------------------- |
| scrollUp  | [NestedScrollMode](../apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10) | No  | Yes  | Nested scrolling options when the component scrolls up.<br>Default value: **NestedScrollMode.SELF_FIRST**.|
| scrollDown | [NestedScrollMode](../apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10) | No  | Yes  | Nested scrolling options when the component scrolls down.<br>Default value: **NestedScrollMode.SELF_FIRST**.|
| scrollLeft  | [NestedScrollMode](../apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10) | No  | Yes  | Nested scrolling options when the component scrolls left.<br>Default value: **NestedScrollMode.SELF_FIRST**.|
| scrollRight | [NestedScrollMode](../apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10) | No  | Yes  | Nested scrolling options when the component scrolls right.<br>Default value: **NestedScrollMode.SELF_FIRST**.|

## NativeMediaPlayerConfig<sup>12+</sup>

Configures the [enableNativeMediaPlayer](./arkts-basic-components-web-attributes.md#enablenativemediaplayer12) API for the app to take over web page media playback, supporting whether to enable it and whether to override web page content. It is suitable for scenarios where custom media playback behavior is required, improving media playback integration and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
|  enable  | boolean | No | No | Whether to enable the app to take over web media playback.<br/> The value **true** indicates that the app takes over web media playback, and **false** indicates that this feature is disabled.<br/> Default value: **false** |
|  shouldOverlay | boolean | No | No | Whether the player screen of the app-taken-over web video overlays the web content after the app takes over web media playback.<br/> The value **true** indicates that the video layer level is changed to overlay the web content, and **false** indicates that the original layer level is maintained and the video is embedded in the web page.<br>Default value: **false** |

## ExpandedMenuItemOptions<sup>(deprecated)</sup>

Custom menu extension item.

> **NOTE**
>
> This API is supported from API version 12 and deprecated from API version 20. You are advised to use [editMenuOptions](./arkts-basic-components-web-attributes.md#editmenuoptions12) instead.

**System capability**: SystemCapability.Web.Webview.Core

| Name          | Type                                            | Read-Only   | Optional   | Description            |
| ---------- | -----------------------------------------------------| ------ | ------ | ---------------- |
| content   | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr)  | No    | No    | Display content.    |
| startIcon | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr)  | No    | Yes    | Display icon. The default value is empty, and no icon is displayed.    |
| action    | (selectedText: {plainText: string}) => void                    | No     | No     | Callback invoked when the user selects a menu extension item. The callback parameter **selectedText** contains the **plainText** field, which indicates the text content selected by the user.|

## AdsBlockedDetails<sup>12+</sup>

Provides detailed information about the blocked ads when ads are blocked.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type            | Read-Only| Optional  | Description                |
| ---------- | -----------------|---- | ----- | -------------------- |
| url        | string           | No |  No   | URL of the page where ads are blocked.|
| adsBlocked | Array\<string\>  | No |  No   | URLs or dompaths of the blocked ads. If multiple ads have the same URLs, duplicate elements may exist.|

## SelectionMenuOptionsExt<sup>13+</sup>

Represents the selection menu option extension.

**System capability**: SystemCapability.Web.Webview.Core

| Name          | Type                                            | Read-Only   | Optional   | Description            |
| ---------- | -----------------------------------------------------| ------ | ------ | ---------------- |
| onAppear   | Callback\<void\>   | No    | Yes    | Callback invoked when the custom selection menu appears.    |
| onDisappear | Callback\<void\>  | No    | Yes    | Callback invoked when the custom selection menu disappears.    |
| preview    | [CustomBuilder](../apis-arkui/arkui-ts/ts-types.md#custombuilder8)          | No    | Yes    | Preview content style of the custom selection menu. If this parameter is not set, there is no preview content.|
| menuType   | [MenuType](../apis-arkui/arkui-ts/ts-text-common.md#menutype13)     | No    | Yes    | Type of the custom selection menu.<br>Default value: **MenuType.SELECTION_MENU**<br> Since API version 20, **MenuType.PREVIEW_MENU** supports hyperlink preview.    |
| previewMenuOptions<sup>20+</sup> | [PreviewMenuOptions](#previewmenuoptions20) | No    | Yes    | Custom preview menu options.|
| onMenuShow<sup>21+</sup> | Callback\<void\> | No    | Yes    | Callback invoked when the custom context menu on selection is shown.|
| onMenuHide<sup>21+</sup> | Callback\<void\> | No    | Yes    | Callback invoked when the custom context menu on selection is hidden.|

## PreviewMenuOptions<sup>20+</sup>

Configures preview menu options, supporting the vibration effect when the menu pops up. It is suitable for scenarios where enhanced menu interaction feedback is required, improving user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name          | Type                                            | Read-Only   | Optional   | Description            |
| ---------- | -----------------------------------------------------| ------ | ------ | ---------------- |
| hapticFeedbackMode   | [HapticFeedbackMode](../apis-arkui/arkui-ts/ts-universal-attributes-menu.md#hapticfeedbackmode18)   | No    | Yes    | Vibration effect when the menu is displayed. The **ohos.permission.VIBRATE** permission is required.<br>Default value: **HapticFeedbackMode.DISABLED**, indicating no vibration when the menu is displayed.    |

## EmbedOptions<sup>16+</sup>

Configuration for Web same-layer rendering. Configures Web same-layer rendering options, including support for fixed size and CSS display properties. It is suitable for scenarios where same-layer element rendering optimization is required, improving rendering compatibility and flexibility.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional| Description                                      |
| -------------- | ------- | ---- |  ---- |---------------------------------------- |
| supportDefaultIntrinsicSize | boolean | No   | Yes| Whether a same-layer rendering element supports the fixed size of 300 × 150.<br>When the size of an element is set using CSS on the HTML5 side, the size of the same-layer rendering element uses the CSS size. Otherwise, the size is fixed.<br>If the value is **true**, the fixed size is 300 × 150.<br>If the value is **false** and the CSS size is not set on the HTML5 side, the same-layer rendering elements are not rendered.<br>Default value: **false**.<br>Unit: px.|
| supportCssDisplayChange<sup>20+</sup> | boolean | No   | Yes| Whether the same-layer rendering visibility API supports the display attribute.<br>By default, the visibility status of same-layer tags relative to the viewport is supported.<br>If this attribute is set to **true**, CSS attributes can be displayed, including visibility, display, width, and height.<br>Otherwise, CSS attributes are not displayed, and only same-layer tags are visible relative to the viewport.|

## OnAlertEvent<sup>12+</sup>

Defines the callback used when a web page triggers **alert()**.

**System capability**: SystemCapability.Web.Webview.Core

| Name   | Type                                                | Read-Only| Optional| Description                       |
| ------- | ---------------------------------------------------- | ---- | ---- | --------------------------- |
| url     | string                                               | No  | No  | URL of the web page where the dialog box is displayed.  |
| message | string                                               | No  | No  | Information displayed in the dialog box.       |
| result  | [JsResult](./arkts-basic-components-web-JsResult.md) | No  | No  | User operation result that is notified to the **Web** component.|

## OnBeforeUnloadEvent<sup>12+</sup>

Defines the callback triggered when the user is about to leave the current page in refresh or close scenarios. It is suitable for scenarios such as form editing, allowing developers to intercept the leave action and display a confirmation dialog, thereby preventing accidental loss of unsubmitted user data.

**System capability**: SystemCapability.Web.Webview.Core

| Name                  | Type    | Read-Only| Optional | Description                             |
| --------------------- | -------- | -- | ----|--------------------------------- |
| url                   | string   | No| No | URL of the web page where the dialog box is displayed.                |
| message               | string   | No| No | Message displayed in the dialog box.                             |
| result                | [JsResult](./arkts-basic-components-web-JsResult.md) | No| No| User operation.                      |
| isReload<sup>20+</sup>| boolean | No | Yes | Whether the page is reloaded.<br>When the page is about to leave due to a reload, the value of isReload is **true**; when the page is about to leave due to being closed, the value of isReload is **false**.<br>Default value: **false**. |

## OnConfirmEvent<sup>12+</sup>

Defines the callback used when a web page triggers **confirm()**.

**System capability**: SystemCapability.Web.Webview.Core

| Name   | Type                                                | Read-Only| Optional| Description                       |
| ------- | ---------------------------------------------------- | ---- | ---- | --------------------------- |
| url     | string                                               | No  | No  | URL of the web page where the dialog box is displayed.  |
| message | string                                               | No  | No  | Information displayed in the dialog box.       |
| result  | [JsResult](./arkts-basic-components-web-JsResult.md) | No  | No  | User operation result that is notified to the **Web** component.|

## OnPromptEvent<sup>12+</sup>

Defines the callback used when a web page triggers **prompt()**.

**System capability**: SystemCapability.Web.Webview.Core

| Name   | Type                                                | Read-Only| Optional| Description                       |
| ------- | ---------------------------------------------------- | ---- | ---- | --------------------------- |
| url     | string                                               | No  | No  | URL of the web page where the dialog box is displayed.  |
| message | string                                               | No  | No  | Information displayed in the dialog box.       |
| value   | string                                               | No  | No  | Default information returned by the dialog box.     |
| result  | [JsResult](./arkts-basic-components-web-JsResult.md) | No  | No  | User operation result that is notified to the **Web** component.|

## OnConsoleEvent<sup>12+</sup>

Represents the callback invoked to notify the host application of a JavaScript console message.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---------|------------------------------- |
| message | [ConsoleMessage](./arkts-basic-components-web-ConsoleMessage.md) | No| No| Console message.                      |

## OnErrorReceiveEvent<sup>12+</sup>

Defines the callback information triggered when an error occurs during web page loading, including the request and error details. It is suitable for scenarios where monitoring and handling web page loading errors are required, improving error handling timeliness and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------|---------------------------------- |
| request | [WebResourceRequest](./arkts-basic-components-web-WebResourceRequest.md) | No| No| Encapsulation of a web page request.     |
| error   | [WebResourceError](./arkts-basic-components-web-WebResourceError.md)     | No | No | Encapsulated information about the web page resource loading error. |

## OnHttpErrorReceiveEvent<sup>12+</sup>

Defines the callback information triggered when the web page receives an HTTP error during resource loading, including the request and response details. It is suitable for scenarios where monitoring and handling HTTP errors are required, improving network error diagnosis accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name       | Type                                                                       |Read-Only| Optional| Description              |
| ---------- | --------------------------------------------------------------------------- | -- | ----|------------------- |
| request    | [WebResourceRequest](./arkts-basic-components-web-WebResourceRequest.md)    | No| No  | Encapsulation of a web page request. |
| response   | [WebResourceResponse](./arkts-basic-components-web-WebResourceResponse.md)  | No| No  | Encapsulation of a resource response. |

## OnDownloadStartEvent<sup>12+</sup>

Defines the callback information for notifying the host app that a file download has started, including the URL, user agent, and file details. It is suitable for scenarios where monitoring and managing file downloads are required, improving download process controllability and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name             | Type    | Read-Only| Optional | Description                               |
| ---------------- | -------- | --- | -----|----------------------------------- |
| url                | string | No| No| URL for the download task.                          |
| userAgent          | string | No| No| User agent used for download.                         |
| contentDisposition | string | No| No| Content-Disposition response header returned by the server, which may be empty.|
| mimetype           | string | No| No| MIME type of the content returned by the server.               |
| contentLength      | number | No | No | Length of the file returned by the server. Unit: byte.                       |

## OnRefreshAccessedHistoryEvent<sup>12+</sup>

Defines the callback information triggered when navigation is complete, including the URL and refresh status. It is suitable for scenarios where monitoring page navigation history is required, improving navigation behavior tracking accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| url         | string  | No| No| URL to be accessed.                                 |
| isRefreshed | boolean | No| No| Whether the page is reloaded. The value **true** means that the page is reloaded by invoking the [refresh<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#refresh) API, and **false** means the opposite.|
| isMainFrame<sup>22+</sup> | boolean | No| Yes| Whether the event is triggered by the main frame.<br>The value **true** indicates that the event is triggered by the main frame, and **false** indicates the opposite.|

## OnRenderExitedEvent<sup>12+</sup>

Defines the callback triggered when the rendering process exits. It is suitable for scenarios where monitoring rendering process exceptions is required, improving rendering stability and troubleshooting efficiency.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| renderExitReason | [RenderExitReason](./arkts-basic-components-web-e.md#renderexitreason9) | No| No| Cause for the abnormal exit of the rendering process.|

## OnShowFileSelectorEvent<sup>12+</sup>

Defines the callback information for the file selector result, including the result and parameter details.

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Type                                                                    | Read-Only| Optional| Description                           |
| ------------ | ------------------------------------------------------------------------ | ---- | ---- | ------------------------------- |
| result       | [FileSelectorResult](./arkts-basic-components-web-FileSelectorResult.md) | No  | No  | File selection result to be sent to the **Web** component.|
| fileSelector | [FileSelectorParam](./arkts-basic-components-web-FileSelectorParam.md)   | No  | No  | Information about the file selector.         |

## OnResourceLoadEvent<sup>12+</sup>

Defines the callback information triggered when a URL is loaded, including the resource URL. It is suitable for scenarios where monitoring resource loading behavior is required, improving resource management visibility and performance optimization.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| url  | string | No| No| URL of the loaded resource file.|

## OnScaleChangeEvent<sup>12+</sup>

Represents the callback invoked when the display scale of this page changes.

**System capability**: SystemCapability.Web.Webview.Core

| Name    | Type  | Read-Only| Optional| Description                    |
| -------- | ------ | ---- | ---- | ------------------------ |
| oldScale | number | No  | No  | Display scale of the page before the change.|
| newScale | number | No  | No  | Display scale of the page after the change.|

## OnHttpAuthRequestEvent<sup>12+</sup>

Defines the callback information triggered when an HTTP authentication request is received, including the host and realm information. It is suitable for scenarios where handling HTTP authentication is required, improving authentication process flexibility and security.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | -----------|----------------------------- |
| handler | [HttpAuthHandler](./arkts-basic-components-web-HttpAuthHandler.md) | No| No| User operation.  |
| host    | string                               | No| No| Host to which the HTTP authentication credential is applied.|
| realm   | string                               | No| No| Realm to which the HTTP authentication credential is applied. |

## OnInterceptRequestEvent<sup>12+</sup>

Defines the callback information triggered before the **Web** component loads a URL, including the request details. It is suitable for scenarios where intercepting or modifying network requests is required, improving request control flexibility and security.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| request | [WebResourceRequest](./arkts-basic-components-web-WebResourceRequest.md) | No| No| Information about the URL request.|

## OnPermissionRequestEvent<sup>12+</sup>

Defines the callback information triggered when a permission request is received, including the request details. It is suitable for scenarios where handling permission grants is required, improving permission management flexibility and security.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| request | [PermissionRequest](./arkts-basic-components-web-PermissionRequest.md) | No| No| User operation.|

## OnScreenCaptureRequestEvent<sup>12+</sup>

Defines the callback information triggered when a screen capture request is received. It is suitable for scenarios where handling screen recording permissions is required, improving screen recording process controllability and security.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional| Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| handler | [ScreenCaptureHandler](./arkts-basic-components-web-ScreenCaptureHandler.md) | No| No| User operation.|

## OnContextMenuShowEvent<sup>12+</sup>

Defines the callback information triggered during a call to allow for the display of a custom context menu.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only  | Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| param  | [WebContextMenuParam](./arkts-basic-components-web-WebContextMenuParam.md) | No| No| Parameters related to the context menu.    |
| result | [WebContextMenuResult](./arkts-basic-components-web-WebContextMenuResult.md) | No| No| Result of the context menu.|

## OnSearchResultReceiveEvent<sup>12+</sup>

Defines the callback information for the search result on the web page, including the match ordinal and total count. It is suitable for scenarios where monitoring in-page search behavior is required, improving search interaction visibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name               | Type   | Read-Only| Optional| Description                                      |
| ------------------ | ------- | --- | --- |----------------------------- |
| activeMatchOrdinal | number  | No | No | Sequence number of the current match, which starts from 0.                      |
| numberOfMatches    | number  | No | No | Total number of matches.                           |
| isDoneCounting     | boolean | No  | No  | Whether the current in-page search operation is complete.<br>The value **true** indicates that the current in-page search operation is complete, and **false** indicates the opposite.<br>This method may be called back multiple times until isDoneCounting is **true**. |

## OnScrollEvent<sup>12+</sup>

Defines the callback information triggered when the scrollbar scrolls to a specified position, including the horizontal and vertical offsets.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional| Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| xOffset | number |  No  | No  | Position of the scrollbar on the x-axis relative to the leftmost of the web page.<br>Unit: vp.|
| yOffset | number |  No  | No  | Position of the scrollbar on the y-axis relative to the top of the web page.<br>Unit: vp.|

## OnSslErrorEventReceiveEvent<sup>12+</sup>

Defines the callback information triggered when the web page receives an SSL error, including the error code and certificate chain. It is suitable for scenarios where handling SSL errors is required, improving security exception monitoring and handling capabilities.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| handler | [SslErrorHandler](./arkts-basic-components-web-SslErrorHandler.md) | No| No| User operation.|
| error   | [SslError](./arkts-basic-components-web-e.md#sslerror9)           | No| No| Error code.          |
| certChainData<sup>15+</sup>   | Array<Uint8Array\>           | No| Yes| Certificate chain data.          |

## SslErrorEvent<sup>12+</sup>

Callback details triggered when an SSL error occurs during resource loading by the user, including the URL, error type, and certificate chain. It is suitable for scenarios where detailed analysis of SSL errors is required, improving security issue diagnosis and troubleshooting efficiency.

**System capability**: SystemCapability.Web.Webview.Core

| Name    | Type                                | Read-Only| Optional  | Description          |
| ------- | ------------------------------------ | ---- | ------|------------- |
| handler | [SslErrorHandler](./arkts-basic-components-web-SslErrorHandler.md) | No| No   | User operation.|
| error   | [SslError](./arkts-basic-components-web-e.md#sslerror9)            | No| No  | Error code.          |
| url   | string                                 | No| No   | URL.          |
| originalUrl   | string                         | No| No   | Original URL of the request.          |
| referrer   | string                            | No| No   | Referrer URL.          |
| isFatalError   | boolean                       | No | No    | Whether the error is a fatal error. A fatal error prevents the page from loading and rendering properly (for example, certificate verification failure or protocol error), while a non-fatal error affects only the loading of some resources (for example, image loading failure).<br>The value **true** indicates a fatal error, and **false** indicates a non-fatal error.           |
| isMainFrame   | boolean                        | No| No   | Whether the resource is a main resource.<br>The value **true** indicates a main resource, and **false** indicates a non-main resource.          |
| certChainData<sup>20+</sup>   | Array<Uint8Array\>         | No| Yes| Certificate chain data.          |

## OnClientAuthenticationEvent<sup>12+</sup>

Defines the callback information triggered when an SSL client certificate is required, including the host, port, and key type. It is suitable for scenarios where handling client certificate authentication is required, improving authentication process flexibility and security.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| handler  | [ClientAuthenticationHandler](./arkts-basic-components-web-ClientAuthenticationHandler.md) | No| No| User operation. |
| host     | string                                   | No| No| Host name of the server that requests a certificate.   |
| port     | number                                   | No | No | Port number for requesting the certificate server. The valid range is 0-65535, and an exception is thrown when the value is out of range.    |
| keyTypes | Array<string\>                           | No | No | Acceptable asymmetric key types.    |
| issuers  | Array<string\>                           | No| No| Issuer of the certificate that matches the private key.|

## VerifyPinEvent<sup>22+</sup>

Defines the callback triggered to notify the user of PIN verification.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| handler  | [VerifyPinHandler](./arkts-basic-components-web-VerifyPinHandler.md) | No| No| User operation. |
| identity     | string                                   | No| No| Certificate credential ID used for verification.   |

## OnWindowNewEvent<sup>12+</sup>

Defines the callback triggered when the web page requests the user to create a window. Starting from API version 23, you can use [OnWindowNewExtEvent](#onwindownewextevent23) to obtain more window information.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only  | Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| isAlert       | boolean                                  | No| No| Whether to open the target URL in a new window. The value **true** means to open the target URL in a new window, and **false** means to open the target URL in a new tab.   |
| isUserTrigger | boolean                                  | No| No| Whether the creation is triggered by the user. The value **true** means that the creation is triggered by the user, and **false** means the opposite.     |
| targetUrl     | string                                   | No| No| Target URL.                       |
| handler       | [ControllerHandler](./arkts-basic-components-web-ControllerHandler.md) | No| No| **WebviewController** instance for setting the new window.|

## WindowFeatures<sup>23+</sup>

Provides the feature information of the new window requested to be created by the web page, including the size and location. It is suitable for scenarios where precise control of new window attributes is required, improving window layout accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name               | Type                                 | Read-Only| Optional| Description                       |
|-------------------| ------------------------------------ | ---- | ---- |---------------------------|
| x                 | number                              | No   | No| X coordinate of the top-left corner of the new window, in pixels.  |
| y                 | number                              | No   | No| Y coordinate of the top-left corner of the new window, in pixels.           |
| width             | number                              | No   | No| Width of the new window, in pixels.         |
| height            | number                              | No   | No| Height of the new window, in pixels.         |

## OnWindowNewExtEvent<sup>23+</sup>

Defines the callback information triggered when the web page requests to create a window, including the window feature information and window opening method. It is suitable for scenarios where fine-grained control of new window behavior is required, improving window management customization and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only  | Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| isAlert       | boolean                                  | No| No| The value **true** indicates that a dialog box is requested to be created, and the value **false** indicates that a new tab page is requested to be created.   |
| isUserTrigger | boolean                                  | No| No| Whether the creation is triggered by the user. The value **true** means that the creation is triggered by the user, and **false** means the opposite.     |
| targetUrl     | string                                   | No| No| URL to be opened in the new window.                       |
| handler       | [ControllerHandler](./arkts-basic-components-web-ControllerHandler.md) | No| No| **WebviewController** instance for setting the new window.|
| windowFeatures | [WindowFeatures](./arkts-basic-components-web-i.md#windowfeatures23)                                | No| No| Feature information of the new window requested to be created by the web page.|
| navigationPolicy | [NavigationPolicy](./arkts-basic-components-web-e.md#navigationpolicy23)                            | No| No| Window opening mode when the web page requests a user to create a new window.|

## OnTouchIconUrlReceivedEvent<sup>12+</sup>

Defines the callback information triggered when an apple-touch-icon URL is received, including the URL and precomposed status. It is suitable for scenarios where obtaining web page icons is required, improving icon management flexibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| url         | string  | No| No| Received apple-touch-icon URL.|
| precomposed | boolean | No| No| Whether the apple-touch-icon is precomposed.<br>**true** indicates that the apple-touch-icon is precomposed, and **false** indicates the opposite.  |

## OnFaviconReceivedEvent<sup>12+</sup>

Defines the callback information triggered when the app receives a new favicon, including the icon PixelMap object. It is suitable for scenarios where obtaining web page favicons is required, improving icon management flexibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| favicon | [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No| No| **PixelMap** object of the received favicon.|

## OnPageVisibleEvent<sup>12+</sup>

Represents the callback invoked when the old page is not displayed and the new page is about to be visible.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type  | Read-Only  | Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| url  | string | No | No | URL address of the new page. |

## OnDataResubmittedEvent<sup>12+</sup>

Defines the callback information triggered when the web form data can be resubmitted, including the submission handler. It is suitable for scenarios where handling form retry submission is required, improving form interaction reliability and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| handler | [DataResubmissionHandler](./arkts-basic-components-web-DataResubmissionHandler.md) | No| No| Handler for resubmitting web form data.|

## OnAudioStateChangedEvent<sup>12+</sup>

Defines the callback information triggered when the audio playback status on the web page changes, including the playback status. It is suitable for scenarios where monitoring audio playback behavior is required, improving audio management visibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| playing | boolean | No| No| Audio playback status on the current page. The value **true** means that audio is being played, and **false** means the opposite.|

## OnFirstContentfulPaintEvent<sup>12+</sup>

Defines the callback information for the first content paint on the web page, including the load time and paint time. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional| Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| navigationStartTick    | number | No| No| Navigation start time, in microseconds.         |
| firstContentfulPaintMs | number | No| No| Time between navigation and when the content is first rendered, in milliseconds.|

## OnLoadInterceptEvent<sup>12+</sup>

Defines the callback information triggered when resource loading is intercepted, including the request details. It is suitable for scenarios where intercepting or handling resource loading is required, improving resource control flexibility and security.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| data | [WebResourceRequest](./arkts-basic-components-web-WebResourceRequest.md) | No| No| Information about the URL request.|

## OnOverScrollEvent<sup>12+</sup>

Defines the callback information triggered when the web page is overscrolled, including the horizontal and vertical offsets.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional| Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| xOffset | number |  No  | No  | Horizontal overscroll offset based on the leftmost edge of the web page.<br>Unit: vp.|
| yOffset | number |  No  | No  | Vertical overscroll offset based on the top edge of the web page.<br>Unit: vp.|

## JavaScriptProxy<sup>12+</sup>

Defines the JavaScript object to be injected, including the object name, method list, and permission configuration. It is suitable for scenarios where JavaScript-to-native interaction is required, improving cross-language call flexibility and security.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| object     | object                                   | No | No    | Object participating in the registration. Only methods can be declared, not attributes. Methods must be of the function type.                   |
| name       | string                                   | No| No   | Name of the object to be registered, which is the same as that invoked in the window.               |
| methodList | Array\<string\>                          | No| No   | Synchronous methods of the JavaScript object to be registered at the application side.                |
| controller | [WebController](./arkts-basic-components-web-WebController.md) \| [WebviewController](./arkts-apis-webview-WebviewController.md) | No | No    |  Controller. Since API version 9, WebController is no longer maintained. You are advised to use WebviewController instead. |
| asyncMethodList<sup>12+</sup>  | Array\<string\>      | No| Yes   | Asynchronous methods of the JavaScript object to be registered at the application side. Asynchronous methods cannot obtain return values.  |
| permission<sup>12+</sup>  | string  | No| Yes   | JSON string, which is empty by default. This string is used to configure JSBridge permission control and define the URL trustlist at the object and method levels.<br>The **permission** parameter of JavaScriptProxy supports the resource, HTTP, and HTTPS protocols, but does not support the file protocol.<br>For the example, see [Invoking Application Functions on the Frontend Page](../../web/web-in-page-app-function-invoking.md).|

## OnPageEndEvent<sup>12+</sup>

Defines the callback information triggered when the web page loading ends, including the page URL. It is suitable for scenarios where monitoring page loading completion is required, improving page lifecycle management capabilities.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| url | string | No | No | URL of the page after the web page is loaded. |

## OnPageBeginEvent<sup>12+</sup>

Defines the callback information triggered when the web page loading begins, including the page URL. It is suitable for scenarios where monitoring page loading start is required, improving page lifecycle management capabilities.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| url | string | No | No | URL of the page to be loaded when page loading starts. |

## OnProgressChangeEvent<sup>12+</sup>

Defines the callback information triggered when the web page loading progress changes, including the new progress value. It is suitable for scenarios where monitoring page loading progress is required, improving loading process visibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| newProgress | number | No | No | New loading progress, which is an integer in the range [0, 100]. |

## OnTitleReceiveEvent<sup>12+</sup>

Defines the callback information triggered when the document title of the web page is changed, including the title content and source. It is suitable for scenarios where monitoring page title changes is required, improving page information real-time performance and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional   | Description                                      |
| -------------- | ---- | ---- | -------------|--------------------------- |
| title | string | No| No| Document title.                      |
| isRealTitle<sup>20+</sup> | boolean | No| Yes| Whether the document title is a real title. The value true indicates that the title is from the **title** tag of the web page, and **false** indicates that the title is automatically generated based on the URL.<br>Default value: **false**.|

## OnGeolocationShowEvent<sup>12+</sup>

Defines the callback information triggered when a request to obtain the geolocation information is received, including the origin information and geolocation object. It is suitable for scenarios where handling geolocation permissions is required.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional   | Description                                      |
| -------------- | ---- | ---- | -------------|--------------------------- |
| origin | string | No | No | Origin of the web page that initiates the geolocation permission request, used to identify the source of the geolocation request from a specific website. |
| geolocation | [JsGeolocation](./arkts-basic-components-web-JsGeolocation.md) | No| No| User operation.                      |

## NativeEmbedVisibilityInfo<sup>12+</sup>

Provides visibility information about the same-layer tag, including the visibility status and tag ID. It is suitable for scenarios where monitoring same-layer element visibility is required, improving rendering state management accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name          | Type                               | Read-Only| Optional| Description             |
| -------------  | ------------------------------------| ----- | ----- | ------------------ |
| visibility     | boolean                             | No    | No| Whether the same-layer tag is visible.<br>The value **true** indicates that the same-layer tag is visible, and **false** indicates the opposite.        |
| embedId        | string                              | No    | No| ID of the same-layer rendered tag. |

## RenderProcessNotRespondingData<sup>12+</sup>

Provides detailed information about the unresponsive rendering process. It is suitable for scenarios where diagnosing rendering process exceptions is required, improving troubleshooting accuracy and efficiency.

**System capability**: SystemCapability.Web.Webview.Core

| Name                    | Type  | Read-Only  | Optional| Description                                  |
| ------------------------ | ---- | ---- | ---- | -------------------------------------- |
| jsStack | string | No | No | JavaScript call stack information of the web page. |
| pid | number | No| No| Process ID of the web page.|
| reason | [RenderProcessNotRespondingReason](./arkts-basic-components-web-e.md#renderprocessnotrespondingreason12) | No| No| Reason why the rendering process does not respond.|

## FullScreenEnterEvent<sup>12+</sup>

Provides the callback information for the **Web** component to enter the full-screen mode, including the video size and exit handler. It is suitable for scenarios where handling full-screen video is required, improving video playback immersive experience and controllability.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type                                 | Read-Only| Optional  | Description                   |
| -----------     | ------------------------------------ | ---- | ---- | --------------------- |
| handler     | [FullScreenExitHandler](./arkts-basic-components-web-FullScreenExitHandler.md) | No| No | Function handle for exiting full screen mode.|
| videoWidth  | number | No| Yes| Video width, in px. If the element that enters fulls screen mode is a **\<video>** element, the value represents its width; if the element that enters fulls screen mode contains a **\<video>** element, the value represents the width of the first sub-video element; in other cases, the value is **0**.|
| videoHeight  | number | No| Yes | Video height, in px. If the element that enters fulls screen mode is a **\<video>** element, the value represents its height; if the element that enters fulls screen mode contains a **\<video>** element, the value represents the height of the first sub-video element; in other cases, the value is **0**.|

## LoadCommittedDetails<sup>11+</sup>

Provides detailed information about the web page that has been submitted for redirection, including whether it is the main document, the navigation type, and more. It is suitable for scenarios where monitoring page navigation behavior is required, improving navigation state management accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type                                 | Read-Only| Optional  | Description                   |
| -----------     | ------------------------------------ | ---- | -------|-------------- |
| isMainFrame     | boolean                              | No  | No   | Whether it is the main document.<br>The value **true** indicates the main document, and **false** indicates a non-main document. |
| isSameDocument  | boolean                              | No  | No    | Whether the web page navigation is performed without changing the document.<br>The value **true** indicates that the web page navigation is performed without changing the document, and **false** indicates that the web page navigation is performed with the document changed.<br>Examples of same-document navigation: 1. Reference fragment navigation; 2. Navigation triggered by pushState or replaceState; 3. History navigation within the same page.  |
| didReplaceEntry | boolean                              | No| No   | Whether the submitted new entry replaces the existing entry.<br>The value **true** indicates that the submitted new entry replaces the existing entry, and **false** indicates the opposite.<br>In certain scenarios for navigation to a subdocument, although the existing entry is not replaced, some attributes are changed. |
| navigationType  | [WebNavigationType](./arkts-basic-components-web-e.md#webnavigationtype11)  | No| No  | Navigation type.      |
| url             | string                               | No  | No    | URL of the web page to navigate to.          |

## NativeEmbedInfo<sup>11+</sup>

Provides detailed information about the same-layer tag, including the ID, type, size, and location. It is suitable for scenarios where obtaining same-layer element attributes is required, improving same-layer rendering customization and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name               | Type                                 | Read-Only| Optional| Description                       |
|-------------------| ------------------------------------ | ---- | ---- |---------------------------|
| id                | string             | No   | Yes| ID of the same-layer tag.            |
| type              | string                              | No   | Yes| Type of the same-layer tag. The value is in lowercase.  |
| src               | string                              | No   | Yes| **src** information of the same-layer tag.           |
| width             | number  | No   | Yes| Width of the same-layer tag, in px.         |
| height            | number                              | No   | Yes| Height of the same-layer tag, in px.         |
| url               | string                              | No   | Yes| URL of the same-layer tag.           |
| tag<sup>12+</sup> | string              | No   | Yes| Tag name, which is in uppercase.             |
| params<sup>12+</sup>            | Map<string, string> | No    | Yes | List of key-value pairs of the params tag in the object tag. Use the methods provided by Object to operate this object, for example, `embed.info?.params?.["name"]`. |
| position<sup>12+</sup>          | Position            | No   | Yes| Position of the same-layer tag relative to the upper left corner of the **Web** component as the coordinate origin, in pixels. This position is different from the standard position.|

## NativeEmbedParamItem<sup>21+</sup>

Provides detailed information about the **param** element embedded in the same-layer rendering tag **object**, including the status and parameters. It is suitable for scenarios where monitoring param element changes is required, improving same-layer element management flexibility and accuracy.

**System capability**: SystemCapability.Web.Webview.Core

| Name               | Type                                 | Read-Only| Optional| Description                       |
|-------------------| ------------------------------------ | ---- | ---- |---------------------------|
| status     | [NativeEmbedParamStatus](./arkts-basic-components-web-e.md#nativeembedparamstatus21)             | No   | No   | Status change type of the **param** element.|
| id                | string                              | No   | No| ID of the **param** element.            |
| name              | string                              | No   | Yes| Name of the **param** element.          |
| value             | string                              | No   | Yes| Value of the **param** element.         |

## IntelligentTrackingPreventionDetails<sup>12+</sup>

Provides detailed information about intelligent tracking prevention, including the website domain and tracker domain. It is suitable for scenarios where monitoring ad blocking behavior is required, improving privacy protection transparency and controllability.

**System capability**: SystemCapability.Web.Webview.Core

| Name          | Type                               | Read-Only | Optional | Description        |
| ------------- | ------------------------------------| ---- | ---- |------- |
| host          | string                              | No   | No  | Host name.   |
| trackerHost   | string                              | No   | No  | Host name of the tracker. |

## WebKeyboardCallbackInfo<sup>12+</sup>

Input parameters of the callback used to intercept the soft keyboard started from editable elements on a web page, including [WebKeyboardController](./arkts-basic-components-web-WebKeyboardController.md) and the attributes of the editable element. It is suitable for scenarios where custom keyboard interaction is required, improving input experience customization and flexibility.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type  | Read-Only  | Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| controller | [WebKeyboardController](./arkts-basic-components-web-WebKeyboardController.md)  | No| No| Controller used to control the input, deletion, and closure of the custom keyboard.|
| attributes | Record<string, string> | No| No| Attribute of the web page element that triggers the display of the soft keyboard.|

## WebKeyboardOptions<sup>12+</sup>

Return value of the callback that intercepts the soft keyboard started from editable elements on the web page, including the keyboard type and custom keyboard. It is suitable for scenarios where controlling soft keyboard behavior is required.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type  | Read-Only  | Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| useSystemKeyboard | boolean  | No| No| Whether to use the system's default soft keyboard.<br>The value **true** means to use the system's default soft keyboard, and **false** means the opposite.<br>Default value: **true**.|
| enterKeyType | number | No| Yes| Type of the **Enter** key on the system soft keyboard. For details about the value range, see [EnterKeyType](../apis-ime-kit/js-apis-inputmethod.md#enterkeytype10). This parameter is optional and the default value is **UNSPECIFIED**. This parameter is valid only when **useSystemKeyboard** is set to **true** and **enterKeyType** is set to a valid value.|
| customKeyboard | [CustomBuilder](../apis-arkui/arkui-ts/ts-types.md#custombuilder8) | No| Yes| Builder of a custom keyboard. This parameter is required when **useSystemKeyboard** is set to **false**. After it is set, the **Web** component starts the custom keyboard as configured.|

## FirstMeaningfulPaint<sup>12+</sup>

Provides detailed information about the main content paint on the web page, including the navigation time and paint time. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name                    | Type  | Read-Only| Optional| Description                                  |
| ------------------------ | ------ | ---- | ---- | -------------------------------------- |
| navigationStartTime      | number | No| Yes | Start time of the navigation, in microseconds.      |
| firstMeaningfulPaintTime | number | No| Yes  | Time taken for the first meaningful paint of the page, in milliseconds.|

## LargestContentfulPaint<sup>12+</sup>

Provides detailed information about the largest contentful paint on the web page, including the navigation time and various paint times. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name                     | Type  | Read-Only| Optional| Description                                    |
| ------------------------- | ------ | ---- | ---- | ---------------------------------------- |
| navigationStartTime       | number | No| Yes  | Start time of the navigation, in microseconds.        |
| largestImagePaintTime     | number | No| Yes  | Loading time of the maximum image, in milliseconds.  |
| largestTextPaintTime      | number | No| Yes  | Loading time of the maximum text, in milliseconds.    |
| largestImageLoadStartTime | number | No| Yes  | Start time of the loading of the maximum image, in milliseconds.|
| largestImageLoadEndTime   | number | No| Yes  | End time of the loading of the maximum image, in milliseconds.|
| imageBPP                  | number | No| Yes  | Number of pixels of the maximum image.                          |

## NativeEmbedDataInfo<sup>11+</sup>

Provides detailed information about the changes of the same-layer tag lifecycle, including the status and tag information. It is suitable for scenarios where monitoring same-layer element lifecycle is required, improving rendering state management accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type                                 | Read-Only| Optional  | Description                   |
| -----------     | ------------------------------------ | ---- | ---- | --------------------- |
| status     | [NativeEmbedStatus](./arkts-basic-components-web-e.md#nativeembedstatus11)             | No   | Yes   | Lifecycle status of the same-layer tag.|
| surfaceId  | string  | No | Yes    | SurfaceId of the NativeImage. |
| embedId | string                              | No| Yes   | Unique ID of the same-layer tag. |
| info  | [NativeEmbedInfo](#nativeembedinfo11)  | No | Yes    | Detailed information about the same-layer tag.       |

## NativeEmbedTouchInfo<sup>11+</sup>

Provides detailed information about finger touch on a same-layer tag, including the tag ID and touch event. It is suitable for scenarios where handling same-layer element touch interaction is required, improving touch experience customization and flexibility.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type                                 | Read-Only| Optional  | Description                   |
| -----------     | ------------------------------------  | ---- | ---- | --------------------- |
| embedId     | string   | No   | Yes| Unique ID of the same-layer tag.|
| touchEvent  | [TouchEvent](../apis-arkui/arkui-ts/ts-universal-events-touch.md#touchevent) | No| Yes   | Touch action information.|
| result<sup>12+</sup>     | [EventResult](./arkts-basic-components-web-EventResult.md)   | No| Yes   | Gesture event consumption result.|

## NativeEmbedMouseInfo<sup>20+</sup>

Provides detailed information about clicking or touching and holding a same-layer tag using the mouse or touchpad, including the tag ID and mouse event. It is suitable for scenarios where handling same-layer element mouse interaction is required, improving mouse experience customization and flexibility.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type                                 | Read-Only| Optional  | Description                   |
| -----------     | ------------------------------------  | ---- | ---- | --------------------- |
| embedId     | string   | No   | Yes   | Unique ID of the same-layer tag.|
| mouseEvent  | [MouseEvent](../apis-arkui/arkui-ts/ts-universal-mouse-key.md#mouseevent) | No   | Yes   | Information about clicking or touching and holding using the mouse or touchpad.|
| result     | [EventResult](./arkts-basic-components-web-EventResult.md)   | No   | Yes  | Mouse event consumption result.|

## NativeEmbedParamDataInfo<sup>21+</sup>

Provides detailed information about the same-layer tag when the **param** element embedded in the **object** tag changes, including the tag ID and parameter items. It is suitable for scenarios where monitoring param element changes is required, improving same-layer element management flexibility and accuracy.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type                                 | Read-Only| Optional  | Description                   |
| -----------     | ------------------------------------ | ---- | ---- | --------------------- |
| embedId | string                              | No| No   | Unique ID of the same-layer tag. |
| objectAttributeId      | string             | No   | Yes| ID of the same-layer tag.            |
| paramItems  | Array\<[NativeEmbedParamItem](#nativeembedparamitem21)\>   | No  | Yes    | Detailed information about the changed param elements, including the status change type, ID, parameter name, and parameter value of each param element.       |

## OnLoadStartedEvent<sup>20+</sup>

Defines the callback information triggered when the web page loading begins, including the page URL. It is suitable for scenarios where monitoring page loading start is required, improving page lifecycle management capabilities.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| url | string | No| No| URL of the page.                      |

## OnLoadFinishedEvent<sup>20+</sup>

Defines the callback information triggered when the web page loading ends, including the page URL. It is suitable for scenarios where monitoring page loading completion is required, improving page lifecycle management capabilities.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ------------|---------------------------- |
| url | string | No| No| URL of the page.                      |

## OnPdfLoadEvent<sup>20+</sup>

Defines the function triggered when the PDF loading is successful or fails.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| url | string | No| No| URL of the page. |
| result | [PdfLoadResult](./arkts-basic-components-web-e.md#pdfloadresult20) | No| No| The PDF page loading result. |

## OnPdfScrollEvent<sup>20+</sup>

Defines the callback function triggered when the PDF page is scrolled to the bottom.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| url | string | No| No| URL of the page.   |

## Header

Request/response header object returned by the **Web** component. It is suitable for scenarios where reading or modifying HTTP headers is required, improving network request handling flexibility and controllability.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Type | Read-Only| Optional| Description           |
| ----------- | ------ | --- | -----|---------------- |
| headerKey   | string | No | No   | Key of the request or response header.  |
| headerValue | string | No | No   | Value of the request or response header.|

## ScreenCaptureConfig<sup>10+</sup>

Provides the web screen capture configuration options, including the capture mode. It is suitable for scenarios where custom web page screen recording behavior is required, improving screen recording flexibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Type                                     | Read-Only| Optional | Description        |
| ----------- | --------------------------------------- | ---- |----| ---------- |
| captureMode | [WebCaptureMode](./arkts-basic-components-web-e.md#webcapturemode10) | No| No| Web screen capture mode.|

## BlankScreenDetectionEventInfo<sup>22+</sup>

Provides the event information when a blank screen is detected, including the URL, reason, and details. It is suitable for scenarios where monitoring page blank screen issues is required, improving blank screen diagnosis accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| url | string | No| No| URL of the page when a blank screen is detected.   |
| blankScreenReason | [DetectedBlankScreenReason](./arkts-basic-components-web-e.md#detectedblankscreenreason22) | No| No| Reason for the blank screen issue, which depends on the detection method.   |
| blankScreenDetails | [BlankScreenDetails](#blankscreendetails22) | No | Yes | Details of the blank screen detection result. When the detection strategy that detects nodes with content is used and the number of detected nodes with content does not exceed the threshold, this parameter contains detailed information such as the number of nodes with content that are hit. If this strategy is not used or the number of nodes exceeds the threshold, this parameter is empty. |

## BlankScreenDetails<sup>22+</sup>

Provides the result details when a blank screen is detected, including the number of nodes with content. It is suitable for scenarios where analyzing blank screen causes is required, improving blank screen diagnosis detail and accuracy.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| detectedContentfulNodesCount | number | No| Yes| This attribute may exist when the contentful node detection policy is used and the threshold for the number of detected nodes is set. Otherwise, this attribute does not exist.<br>Number of contentful nodes that are detected.   |

## BlankScreenDetectionConfig<sup>22+</sup>

Provides the policy configuration options for blank screen detection, including the detection timing, method, and threshold. It is suitable for scenarios where custom blank screen detection behavior is required, improving blank screen monitoring flexibility and accuracy.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| enable | boolean | No | No | Whether to enable the white screen policy feature. The value **true** indicates enabled, and **false** indicates disabled. |
| detectionTiming | number[] | No | Yes | Sets the timing (in seconds after loading) at which to detect whether a white screen occurs.<br>Unit: second.<br>Note:<br>1. Duplicate values are ignored.<br>2. The value must be greater than 0. Values less than 0 are ignored.<br>Default value: [1.0, 3.0, 5.0]. |
| detectionMethods | [BlankScreenDetectionMethod](./arkts-basic-components-web-e.md#blankscreendetectionmethod22)[] | No| Yes| Methods of the detection policy. The value is an array.<br>**NOTE**<br>1. Duplicate values are ignored.<br>Default value: **[BlankScreenDetectionMethod.DETECTION_CONTENTFUL_NODES_SEVENTEEN]**. |
| contentfulNodesCountThreshold | number | No | Yes | This parameter takes effect only when the contentful node detection strategy is used.<br/>The value ranges from 0 to ${maximum nodes of the detection strategy}. If the value is less than or equal to the threshold, a near-white screen is triggered.<br/>Default value: 0.<br>Note: The maximum nodes of the detection strategy depend on the selected detection strategy.|

## CameraCaptureStateChangeInfo<sup>23+</sup>

Provides the state change information of the camera when the callback is triggered, including the state before the change and the new state. It is suitable for scenarios where monitoring camera state changes is required, improving camera management visibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| originalState | [CameraCaptureState](./arkts-basic-components-web-e.md#cameracapturestate23) | No | No | State before the change. |
| newState | [CameraCaptureState](./arkts-basic-components-web-e.md#cameracapturestate23) | No| No| New state.  |

## MicrophoneCaptureStateChangeInfo<sup>23+</sup>

Provides the state change information of the microphone when the callback is triggered, including the state before the change and the state after the change. It is suitable for scenarios where monitoring microphone state changes is required, improving microphone management visibility and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| originalState | [MicrophoneCaptureState](./arkts-basic-components-web-e.md#microphonecapturestate23) | No | No | State before the change. |
| newState | [MicrophoneCaptureState](./arkts-basic-components-web-e.md#microphonecapturestate23) | No| No| New state.  |

## AcceptableFileType<sup>23+</sup>

Provides the file type information recommended by the file selector, including the MIME type and type array.

**System capability**: SystemCapability.Web.Webview.Core

| Name | Type                    | Read-Only| Optional| Description            |
| :---- | :------------------------- | :--- | :--- | :--------------- |
| mimeType | string | No| No  | MIME type of the file.|
| acceptableType | Array\<string\> | No| No  | Array of acceptable file types.|

## FirstScreenPaint<sup>23+</sup>

Provides the event information when the first screen paint is detected, including the URL and paint time. It is suitable for scenarios where monitoring page first screen rendering performance is required, improving performance optimization accuracy and user experience.

**System capability**: SystemCapability.Web.Webview.Core

| Name            | Type     | Read-Only| Optional  | Description                                      |
| -------------- | ---- | ---- | ---- | ---------------------------------------- |
| url | string | No| No| URL of the first screen paint statistics.   |
| navigationStartTime | number | No | No | Time when navigation starts for the page pointed to by url.<br>Unit: ms. |
| firstScreenPaintTime | number | No | No | Time when the first screen paint is completed for the page pointed to by url.<br>Unit: ms. |

## AISessionEvent

Custom AI session configuration object, used to define the lifecycle callbacks of an AI session, including creation, execution, and destruction.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

| Name | Type | Read-Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| aiSessionType | [AISessionType](./arkts-basic-components-web-e.md#aisessiontype) | No | No | AI session type. |
| onCreateAISession | [OnCreateAISession](./arkts-basic-components-web-t.md#oncreateaisession) | No | No | Callback function triggered when an AI session is created. Returns **true** to skip the system default behavior, and **false** to continue executing the system default logic. |
| onExecuteAIAction | [OnExecuteAIAction](./arkts-basic-components-web-t.md#onexecuteaiaction) | No | No | Callback function triggered when an AI session executes an action. |
| onDestroyAISession | [OnDestroyAISession](./arkts-basic-components-web-t.md#ondestroyaisession) | No | No | Callback function triggered when an AI session is destroyed, used to clean up resources associated with the custom AI model. |