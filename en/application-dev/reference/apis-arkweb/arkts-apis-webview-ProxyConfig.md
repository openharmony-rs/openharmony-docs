# Class (ProxyConfig)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:45:07.098Z pushedAt=2026-08-07T08:11:15.498Z -->

ProxyConfig is a class in the ArkWeb framework used to configure network proxy rules. It works with [ProxyController](./arkts-apis-webview-ProxyController.md) to implement proxy control over network requests of all Web components in an app. Through ProxyConfig, developers can flexibly define various proxy rules: specifying a particular proxy server for specific URLs, specifying direct server connections for certain URLs, defining rules to bypass the proxy, and more.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 15.
>
> - The sample effect is subject to the actual device.

## insertProxyRule<sup>15+</sup>

insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void

Inserts a proxy rule. URLs matching schemeFilter will use the specified proxy. If the schemeFilter parameter is not specified, the default value MATCH_ALL_SCHEMES will be used, and all URLs will use the specified proxy.

The proxy format is [scheme://]host[:port].

The scheme is optional and must be HTTP, HTTPS, or SOCKS. The default value of scheme is HTTP.

The host is a bracketed IPv6 literal, an IPv4 literal, or one or more labels separated by dots.

The port number is optional. The default port is 80 for HTTP, 443 for HTTPS, and 1080 for SOCKS.

For example:

- example.com host: example.com

- https://example.com  scheme: https  host: example.com

- example.com:8888     host: example.com  port: 8888

- https://example.com:8888  scheme: https  host: example.com  port: 8888

- 192.168.1.1  host: 192.168.1.1

- 192.168.1.1:8888  host: 192.168.1.1 port: 8888

- [10:20:30:40:50:60:70:80]

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type    |  Mandatory | Description          |
| ---------------| ------- | ---- | ------------- |
| proxyRule      | string  | Yes  | The specified proxy.|
| schemeFilter   | [ProxySchemeFilter](./arkts-apis-webview-e.md#proxyschemefilter15)  | No  | Filter used to specify URLs that use the proxy.<br>Default value: **MATCH_ALL_SCHEMES**.<br>If **undefined** or **null** is passed, error code **401** will be thrown.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.  |

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## insertDirectRule<sup>15+</sup>

insertDirectRule(schemeFilter?: ProxySchemeFilter): void

Inserts a direct rule, specifying that URLs matching the schemeFilter condition will directly connect to the server.

> **NOTE**
>
> - Both [insertBypassRule](#insertbypassrule15) and [bypassHostnamesWithoutPeriod](#bypasshostnameswithoutperiod15) can also implement direct URL connection. The difference lies in the matching dimension: this method matches by protocol type through schemeFilter; insertBypassRule matches by URL pattern through a bypassRule string; bypassHostnamesWithoutPeriod requires no parameters and automatically enables direct connection for hostnames without a period. You can choose the appropriate method based on the URL range that needs direct connection.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type    |  Mandatory | Description          |
| ---------------| ------- | ---- | ------------- |
| schemeFilter   | [ProxySchemeFilter](./arkts-apis-webview-e.md#proxyschemefilter15)  | No  | Filter used to specify URLs to be directly connected to the server.<br>Default value: **MATCH_ALL_SCHEMES**.<br>If **undefined** or **null** is passed, error code **401** will be thrown.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.  |

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## insertBypassRule<sup>15+</sup>

insertBypassRule(bypassRule: string): void

Inserts a bypass rule, specifying which URLs should bypass the proxy and directly connect to the server. When [enableReverseBypass](#enablereversebypass15) is set to true, URLs matching bypassRule will use the proxy instead of bypassing it.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type    |  Mandatory | Description          |
| ---------------| ------- | ---- | ------------- |
| bypassRule     | string  | Yes   | Bypass rule string that specifies the URL matching rule for bypassing the proxy. It supports host name or domain name formats (for example, "example.com" matches the domain and its subdomains). URLs matching the bypassRule bypass the proxy. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## bypassHostnamesWithoutPeriod<sup>15+</sup>

bypassHostnamesWithoutPeriod(): void

Hostnames without a period character will bypass the proxy and directly connect to the server.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## clearImplicitRules<sup>15+</sup>

clearImplicitRules(): void

Overrides the default behavior and forcibly sends the local host address or local IP address through the proxy. (By default, if host names are local IP addresses or local host addresses, they bypass the proxy.)

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## enableReverseBypass<sup>15+</sup>

enableReverseBypass(reverse: boolean): void

Reverses the bypass rule.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type    |  Mandatory | Description          |
| ---------------| ------- | ---- | ------------- |
| reverse     | boolean  | Yes  | Whether to reverse the bypass rule. The default value is **false**, indicating the bypass rule set in [insertBypassRule](#insertbypassrule15) is not reversed. The value **true** indicates the opposite.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.  |

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## getBypassRules<sup>15+</sup>

getBypassRules(): Array\<string\>

Obtains the list of URLs that do not use the proxy.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| Array\<string\> | List of URLs that do not use the proxy.|

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## getProxyRules<sup>15+</sup>

getProxyRules(): Array\<ProxyRule\>

Obtains proxy rules.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| Array\<[ProxyRule](./arkts-apis-webview-ProxyRule.md)\> | Proxy rule. Each ProxyRule object represents a configured proxy rule. |

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).

## isReverseBypassEnabled<sup>15+</sup>

isReverseBypassEnabled(): boolean

Obtains the value of [enableReverseBypass](#enablereversebypass15). For details, see [enableReverseBypass](#enablereversebypass15).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| boolean | Value of [enableReverseBypass](#enablereversebypass15). The default value is **false**, indicating the bypass rule set in [insertBypassRule](#insertbypassrule15) is not reversed. The value **true** indicates the opposite.|

**Example**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride15).