# Class (FullScreenExitHandler)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @runlei-->
<!--Designer: @shulssins-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=a40d54eb841d3251f24cd251233d70758a16c2e7 translatedAt=2026-11-06T11:21:08.013Z pushedAt=2026-11-09T11:40:11.463Z nl=1 -->

FullScreenExitHandler is a full-screen exit handler class provided by the Web component, used to respond to the event of a web page exiting full-screen mode. This class notifies developers through the exitFullScreen method that the Web component has exited the full-screen state, helping developers handle full-screen state changes in a timely manner, adjust the application UI layout, or execute corresponding logic. For sample code, see [onFullScreenEnter](./arkts-basic-components-web-events.md#onfullscreenenter9).

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **FullScreenExitHandler** API.

**System capability**: SystemCapability.Web.Webview.Core

## exitFullScreen<sup>9+</sup>

exitFullScreen(): void

Exits full screen mode.

**System capability**: SystemCapability.Web.Webview.Core