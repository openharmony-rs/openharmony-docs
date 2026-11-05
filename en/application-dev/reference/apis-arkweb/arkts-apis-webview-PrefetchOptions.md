# Class (PrefetchOptions)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T10:56:49.937Z pushedAt=2026-11-04T11:21:19.512Z nl=1 -->

PrefetchOptions is a configuration class in the ArkWeb framework for customizing web page prefetch behavior. It is set through the prefetch-related API of [prefetchPage](./arkts-apis-webview-WebviewController.md#prefetchpage21), and the customizable settings include whether to ignore Cache-Control: no-store in the response header and the minimum time interval between two prefetches.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 21.
>
> - The sample effect is subject to the actual device.

## Attributes

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| minTimeBetweenPrefetchesMs<sup>21+</sup> | number | No | No | Sets the minimum time interval between two web page prefetches.<br>Each time a prefetch is performed, the interval from the previous prefetch is calculated. If it is less than the set value, this prefetch is canceled.<br>Value range: [0, 500].<br>When set to a negative number, the default value 0 is used.<br>Unit: ms |
| ignoreCacheControlNoStore<sup>21+</sup> | boolean | No | No | Sets whether to ignore Cache-Control: no-store in the response header.<br>When set to true, it is ignored; when set to false, it is not ignored. |

## constructor<sup>21+</sup>

constructor()

A constructor used to create a **PrefetchOptions** instance.

**System capability**: SystemCapability.Web.Webview.Core