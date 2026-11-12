# Class (ProxyRule)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=f18d113dd90e7361c74b830ab39cc318edd40714 translatedAt=2026-11-06T11:04:25.875Z pushedAt=2026-11-09T11:18:18.166Z nl=1 -->

ProxyRule is a class for read-only proxy rule information in the ArkWeb framework, obtained through the [getProxyRules](./arkts-apis-webview-ProxyConfig.md#getproxyrules15) method. When a developer configures proxy rules through ProxyConfig, the configured rule list can be obtained through getProxyRules, with each rule corresponding to a ProxyRule object used to query the detailed information of the rule.

ProxyRule provides two methods: getSchemeFilter is used to obtain the protocol filter corresponding to the proxy rule (such as MATCH_ALL_SCHEMES, MATCH_HTTP, MATCH_HTTPS, etc.), and getUrl is used to obtain the proxy server URL information specified in the proxy rule. The ProxyRule object is read-only, created by the system when configuring proxy rules, and the app can only query its content but cannot modify it.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 15.
>
> - The sample effect is subject to the actual device.

## getSchemeFilter<sup>15+</sup>

getSchemeFilter(): ProxySchemeFilter

Obtains the **ProxySchemeFilter** information in the proxy rule.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| [ProxySchemeFilter](./arkts-apis-webview-e.md#proxyschemefilter15) | **ProxySchemeFilter** in the proxy rule.|

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## getUrl<sup>15+</sup>

getUrl(): string

Obtains the URL specified in the proxy rule.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| string | URL information of the proxy in the proxy rule. |

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).