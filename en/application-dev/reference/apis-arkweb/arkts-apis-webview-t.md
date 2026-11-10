# Types
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @hwt00888022-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=a40d54eb841d3251f24cd251233d70758a16c2e7 translatedAt=2026-11-06T11:04:35.851Z pushedAt=2026-11-09T11:18:30.988Z nl=1 -->

The ArkWeb Types module is a collection of type aliases and callback function type definitions in the ArkWeb framework. It provides unified data type constraints and callback signature specifications for capabilities such as message communication, proxy configuration, and media playback control of the WebView component, serving as the type support layer in the interface declarations of core classes related to the WebView component.

When using core classes related to the WebView component, developers need to rely on the type definitions in this module to constrain data formats, declare callback signatures, and implement various callback integrations.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual device.

## WebMessage

type WebMessage = ArrayBuffer | string

Defines the data types supported by [WebMessagePort](./arkts-apis-webview-WebMessagePort.md).

**System capability**: SystemCapability.Web.Webview.Core

| Type      | Description                                    |
| -------- | -------------------------------------- |
| string   | String type.|
| ArrayBuffer   | Binary type.|

## OnProxyConfigChangeCallback<sup>15+</sup>

type OnProxyConfigChangeCallback = () => void

Callback invoked when the proxy configuration changes. A successful callback indicates that the proxy settings are applied successfully.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## CreateNativeMediaPlayerCallback<sup>12+</sup>

type CreateNativeMediaPlayerCallback = (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge

Parameter of the [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12) method. A callback invoked when the webpage needs to play media, used to create a player to take over media playback in the webpage. Through this takeover mechanism, the app can use a custom player to implement special features or optimize performance.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| handler | [NativeMediaPlayerHandler](./arkts-apis-webview-NativeMediaPlayerHandler.md) | Yes | Object used by the app to report player status events, such as play, pause, and error, to the ArkWeb kernel, enabling the kernel to synchronize media playback states in web pages. |
| mediaInfo | [MediaInfo](./arkts-apis-webview-i.md#mediainfo12) | Yes| Information about the media on the web page.|

**Return value**

| Type| Description|
|------|------|
| [NativeMediaPlayerBridge](./arkts-apis-webview-NativeMediaPlayerBridge.md) | An interface class that bridges the web media player and the ArkWeb kernel.<br/>The app needs to implement this interface class.<br/>The ArkWeb kernel controls the media player created by the app through this interface object.<br/>If the app returns null, it indicates that the app does not take over the playback of this media, and the ArkWeb kernel plays the media. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).