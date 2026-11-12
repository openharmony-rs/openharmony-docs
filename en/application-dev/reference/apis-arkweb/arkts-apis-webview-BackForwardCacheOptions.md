# Class (BackForwardCacheOptions)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=f18d113dd90e7361c74b830ab39cc318edd40714 translatedAt=2026-11-06T11:00:18.115Z pushedAt=2026-11-10T02:05:06.285Z nl=1 -->

BackForwardCacheOptions is a parameter class in the ArkWeb framework used to configure the forward/backward cache (BFCache) behavior of Web components. BFCache is a page caching mechanism that caches a complete snapshot of a page (including its JavaScript state) when the user navigates forward or backward in the browsing history, enabling instant loading and significantly improving user experience. With BackForwardCacheOptions, developers can control the maximum number of pages allowed to be cached for each Web component and the maximum duration a page can remain in the cache.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

**System capability**: SystemCapability.Web.Webview.Core

## Attributes

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| size<sup>12+</sup> | number | No | No | Sets the maximum number of pages that each Web component can cache.<br>The default value is 1, and the maximum configurable value is 50.<br>When set to 0 or a negative number, the forward/backward cache feature does not take effect.<br>The Web component reclaims the cache based on memory pressure. |
| timeToLive<sup>12+</sup> | number | No| No| The time that a **Web** component allows a page to stay in the back-forward cache.<br>If this parameter is set to **0** or a negative value, the back-forward cache is disabled.<br>Default value: **600**<br>Unit: second|

## constructor<sup>12+</sup>

constructor()

Constructs a **BackForwardCacheOptions** object.

**System capability**: SystemCapability.Web.Webview.Core