# Module Description
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @hwt00888022-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d96db6dbe792bc577106b8fe7b2f1f6d0125cb3e translatedAt=2026-11-04T11:08:18.885Z pushedAt=2026-11-04T11:21:57.742Z nl=1 -->

The WebView module is a Web control capability module provided by the HarmonyOS ArkWeb framework, used to programmatically control the behavior of Web components on the application side. This module does not involve the display and rendering of web pages (the display capability is provided by the Web component), but focuses on the control logic during the operation of Web components, including page loading and navigation, JavaScript script execution and bidirectional message communication, cookie and storage management, download task management, network request interception and custom responses, proxy configuration, geolocation permission management, ad filtering, forward and backward cache, media playback hosting, PDF generation, and other capabilities.

When developers use Web components to display web page content, if they need to intervene, monitor, or extend web page behavior on the application side (for example, sending messages to web pages, intercepting specific Scheme requests and returning local resources, managing the download process, configuring proxies, controlling cache policies, etc.), they should implement this through the Controller and various Manager/Delegate classes provided by this module.

For the web page display capability, see [component description](arkts-basic-components-web.md).

<!--RP1--><!--RP1End-->

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual device.
>
> - Static methods must be used on the user interface (UI) thread.

This module provides the following common functionalities for web control:

- [AdsBlockManager](./arkts-apis-webview-AdsBlockManager.md): Ad filtering configuration.
- [AIPageCommand](./arkts-apis-webview-AIPageCommand.md): JSON command protocol supported by [executeAIPageCommand](./arkts-apis-webview-WebviewController.md#executeaipagecommand).
- [BackForwardCacheOptions](./arkts-apis-webview-BackForwardCacheOptions.md): Forward and backward cache configuration.
- [BackForwardCacheSupportedFeatures](./arkts-apis-webview-BackForwardCacheSupportedFeatures.md): Features supported for configuring forward and backward cache.
- [GeolocationPermissions](./arkts-apis-webview-GeolocationPermissions.md): Geolocation permission configuration.
- [JsMessageExt](./arkts-apis-webview-JsMessageExt.md): JavaScript execution result.
- [MediaSourceInfo](./arkts-apis-webview-MediaSourceInfo.md): Media source information.
- [NativeMediaPlayerSurfaceInfo](./arkts-apis-webview-NativeMediaPlayerSurfaceInfo.md): Rendering information when the application takes over media playback.
- [PdfData](./arkts-apis-webview-PdfData.md): Generated PDF output data.
- [ProxyConfig](./arkts-apis-webview-ProxyConfig.md): Network proxy configuration.
- [ProxyController](./arkts-apis-webview-ProxyController.md): Network proxy controller.
- [WebviewController](./arkts-apis-webview-WebviewController.md): **Web** component controller.
- [WebCookieManager](./arkts-apis-webview-WebCookieManager.md): Cookie management.
- [WebDataBase](./arkts-apis-webview-WebDataBase.md): Database management.
- [WebDownloadDelegate](./arkts-apis-webview-WebDownloadDelegate.md): Download task status event.
- [WebDownloadItem](./arkts-apis-webview-WebDownloadItem.md): Download task.
- [WebDownloadManager](./arkts-apis-webview-WebDownloadManager.md): Download task management.
- [WebHttpBodyStream](./arkts-apis-webview-WebHttpBodyStream.md): HTTP request body.
- [WebMessageExt](./arkts-apis-webview-WebMessageExt.md): Data object for communication between the frontend and application.
- [WebResourceHandler](./arkts-apis-webview-WebResourceHandler.md): Resource loading control.
- [WebSchemeHandler](./arkts-apis-webview-WebSchemeHandler.md): Request interceptor of a specified scheme.
- [WebSchemeHandlerRequest](./arkts-apis-webview-WebSchemeHandlerRequest.md): Request intercepted by the interceptor.
- [WebSchemeHandlerResponse](./arkts-apis-webview-WebSchemeHandlerResponse.md): Custom responses for intercepted requests.
- [WebStorage](./arkts-apis-webview-WebStorage.md): Storage operation API of the **Web** component.
- [BackForwardList](./arkts-apis-webview-BackForwardList.md): History information list.
- [NativeMediaPlayerBridge](./arkts-apis-webview-NativeMediaPlayerBridge.md): Bridge API for taking over web media players.
- [NativeMediaPlayerHandler](./arkts-apis-webview-NativeMediaPlayerHandler.md): Event API for taking over web media players.
- [WebMessagePort](./arkts-apis-webview-WebMessagePort.md): Message port between the web page and application.

## Required Permissions

**ohos.permission.INTERNET**, required for accessing online web pages. For details about how to apply for a permission, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

**System capability**: SystemCapability.Web.Webview.Core
