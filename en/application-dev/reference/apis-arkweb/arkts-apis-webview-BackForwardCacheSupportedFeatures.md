# Class (BackForwardCacheSupportedFeatures)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=f18d113dd90e7361c74b830ab39cc318edd40714 translatedAt=2026-11-06T11:00:29.386Z pushedAt=2026-11-09T09:22:17.683Z nl=1 -->

BackForwardCacheSupportedFeatures is a configuration class in the ArkWeb framework used to selectively allow pages that use specific web features to enter the Back/Forward Cache (BFCache). By default, pages using features such as native embed or media takeover are blocked from entering BFCache, because the browser cannot safely save and restore these complex states bound to system controls. By setting the properties in this class, developers can explicitly allow pages with these features to enter BFCache, but they must manage the lifecycle of the related system controls themselves to avoid resource leaks. For the complete sample code, see [enableBackForwardCache](./arkts-apis-webview-WebviewController.md#enablebackforwardcache12).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## Attributes

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| nativeEmbed<sup>12+</sup> | boolean | No | No | Whether to allow pages using native embed to enter the back-forward cache.<br>If allowed, you need to maintain the lifecycle of system controls created for native embed elements to avoid resource leaks.<br>true: allowed; false: not allowed.<br>Default value: false. |
| mediaTakeOver<sup>12+</sup> | boolean | No | No | Whether to allow pages using media takeover to enter the back-forward cache.<br>If allowed, you need to maintain the lifecycle of system controls created for video elements to avoid resource leaks.<br>true: allowed; false: not allowed.<br>Default value: false. |

## constructor<sup>12+</sup>

constructor()

Constructs a **BackForwardCacheSupportedFeatures** object.

**System capability**: SystemCapability.Web.Webview.Core