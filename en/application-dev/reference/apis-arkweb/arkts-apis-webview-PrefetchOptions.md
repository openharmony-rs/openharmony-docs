# Class (PrefetchOptions)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:44:12.760Z pushedAt=2026-08-07T08:11:13.358Z -->

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
| minTimeBetweenPrefetchesMs<sup>21+</sup> | number | No | No | Sets the minimum time interval between two web page prefetches.<br>During each prefetch, the interval from the last prefetch is calculated. If it is less than the set value, the current prefetch is canceled.<br>Value range: [0, 500].<br>If set to a negative number, the default value 0 is used.<br>Unit: ms |
| ignoreCacheControlNoStore<sup>21+</sup> | boolean | No | No | Sets whether to ignore Cache-Control: no-store in the response header.<br>If set to true, the header is ignored; if set to false, it is not ignored. |

## constructor<sup>21+</sup>

constructor()

A constructor used to create a **PrefetchOptions** instance.

**System capability**: SystemCapability.Web.Webview.Core