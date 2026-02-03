# Class (ProxyRule)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

Implements a **ProxyRule** object used in [insertProxyRule](./arkts-apis-webview-ProxyConfig.md#insertproxyrule15).

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
| string | URL specified in the proxy rule.|

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).
