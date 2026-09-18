# ProxyConfig

ProxyConfig is a class in the ArkWeb framework used to configure network proxy rules. It works with [ProxyController](arkts-arkweb-webview-proxycontroller-c.md) to implement proxy control over network requests of all Web components in an app. Through ProxyConfig, developers can flexibly define various proxy rules: specifying a particular proxy server for specific URLs, specifying direct server connections for certain URLs, defining rules to bypass the proxy, and more.

**Since:** 15

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## bypassHostnamesWithoutPeriod

```TypeScript
bypassHostnamesWithoutPeriod(): void
```

Hostnames without a period character will bypass the proxy and directly connect to the server.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

## clearImplicitRules

```TypeScript
clearImplicitRules(): void
```

Overrides the default behavior and forcibly sends the local host address or local IP address through the proxy. (By default, if host names are local IP addresses or local host addresses, they bypass the proxy.)

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

## enableReverseBypass

```TypeScript
enableReverseBypass(reverse: boolean): void
```

Reverses the bypass rule.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reverse | boolean | Yes | Whether to reverse the bypass rule. The default value is **false**, indicating the bypass rule set in [insertBypassRule](#insertbypassrule) is not reversed. The value **true** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## getBypassRules

```TypeScript
getBypassRules(): Array<string>
```

Obtains the list of URLs that do not use the proxy.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of URLs that do not use the proxy. |

## getProxyRules

```TypeScript
getProxyRules(): Array<ProxyRule>
```

Obtains proxy rules.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[ProxyRule](arkts-arkweb-webview-proxyrule-c.md)&gt; | Proxy rule. Each ProxyRule object represents a configured proxy rule. |

## insertBypassRule

```TypeScript
insertBypassRule(bypassRule: string): void
```

Inserts a bypass rule, specifying which URLs should bypass the proxy and directly connect to the server. When [enableReverseBypass](#enablereversebypass) is set to true, URLs matching bypassRule will use the proxy instead of bypassing it.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bypassRule | string | Yes | Bypass rule string that specifies the URL matching rule for bypassing the proxy. It supports host name or domain name formats (for example, "example.com" matches the domain and its subdomains). URLs matching the bypassRule bypass the proxy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## insertDirectRule

```TypeScript
insertDirectRule(schemeFilter?: ProxySchemeFilter): void
```

Inserts a direct rule, specifying that URLs matching the schemeFilter condition will directly connect to the server.

> **NOTE:** 
> 
> - Both [insertBypassRule](#insertbypassrule) and [bypassHostnamesWithoutPeriod](#bypasshostnameswithoutperiod) can also implement direct URL connection. The difference lies in the matching dimension: this method matches by protocol type through schemeFilter; insertBypassRule matches by URL pattern through a bypassRule string;bypassHostnamesWithoutPeriod requires no parameters and automatically enables direct connection for hostnames without a period. You can choose the appropriate method based on the URL range that needs direct connection.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| schemeFilter | [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | No | Filter used to specify URLs to be directly connected to the server.<br>Default value: **MATCH_ALL_SCHEMES**. <br>If **undefined** or **null** is passed, error code **401** will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## insertProxyRule

```TypeScript
insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void
```

Inserts a proxy rule. URLs matching schemeFilter will use the specified proxy. If the schemeFilter parameter is not specified, the default value MATCH_ALL_SCHEMES will be used, and all URLs will use the specified proxy.

The proxy format is [scheme://]host[:port].

The scheme is optional and must be HTTP, HTTPS, or SOCKS. The default value of scheme is HTTP.

The host is a bracketed IPv6 literal, an IPv4 literal, or one or more labels separated by dots.

The port number is optional. The default port is 80 for HTTP, 443 for HTTPS, and 1080 for SOCKS.

For example:

- example.com host: example.com  
- https://example.com scheme: https host: example.com  
- example.com:8888 host: example.com port: 8888  
- https://example.com:8888 scheme: https host: example.com port: 8888  
- 192.168.1.1 host: 192.168.1.1  
- 192.168.1.1:8888 host: 192.168.1.1 port: 8888  
- [10:20:30:40:50:60:70:80]

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| proxyRule | string | Yes | The specified proxy. |
| schemeFilter | [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | No | Filter used to specify URLs that use the proxy.<br>Default value: **MATCH_ALL_SCHEMES**. <br>If **undefined** or **null** is passed, error code **401** will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## isReverseBypassEnabled

```TypeScript
isReverseBypassEnabled(): boolean
```

Obtains the value of [enableReverseBypass](#enablereversebypass). For details, see [enableReverseBypass](#enablereversebypass).

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Value of [enableReverseBypass](#enablereversebypass). The default value is **false**, indicating the bypass rule set in [insertBypassRule](#insertbypassrule) is not reversed. The value **true** indicates the opposite. |
