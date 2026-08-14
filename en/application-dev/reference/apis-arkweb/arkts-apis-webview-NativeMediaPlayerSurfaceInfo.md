# Class (NativeMediaPlayerSurfaceInfo)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhangyao75477-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=63dd9a53555af8c592f5447b5465bd04378930df translatedAt=2026-08-07T04:22:20.393Z pushedAt=2026-08-07T08:11:09.778Z -->

NativeMediaPlayerSurfaceInfo uses [enableNativeMediaPlayer](./arkts-basic-components-web-attributes.md#enablenativemediaplayer12) to configure the surface information for same-layer rendering. This class allows an app to take over the web media playback functionality, configuring the surface ID and position information to integrate web media content with the app UI through same-layer rendering and enhance the media playback experience.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## Attributes

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional | Description|
|------|------|------|------|------|
| id<sup>12+</sup> | string | No | No | ID of the surface, which is the surfaceId of the NativeImage used for same-layer rendering.<br>For details, see [NativeEmbedDataInfo](./arkts-basic-components-web-i.md#nativeembeddatainfo11). |
| rect<sup>12+</sup> | [RectEvent](./arkts-apis-webview-i.md#rectevent12) | No | No | Position information of the surface, used to specify the display position and size of the surface during same-layer rendering. |