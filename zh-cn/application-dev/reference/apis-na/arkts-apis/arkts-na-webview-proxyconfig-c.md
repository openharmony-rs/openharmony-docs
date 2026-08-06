# ProxyConfig

The ProxyConfig used by applyProxyOverride.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-class ProxyConfig--><!--Device-webview-class ProxyConfig-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## bypassHostnamesWithoutPeriod

```TypeScript
bypassHostnamesWithoutPeriod(): void
```

Hostnames without a period in them (and that are not IP literals) will skip the proxy and connect the server directly. Examples: "abc", "local", "some-domain".

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-bypassHostnamesWithoutPeriod(): void--><!--Device-ProxyConfig-bypassHostnamesWithoutPeriod(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## clearImplicitRules

```TypeScript
clearImplicitRules(): void
```

By default, certain hostnames implicitly bypass the proxy if they are link-local IPs, or localhost addresses. For instance hostnames matching any of (non-exhaustive list): localhost *.localhost [::1] 127.0.0.1/8 169.254/16 [FE80::]/10 Call this function to override the default behavior and force localhost and link-local URLs to be sent through the proxy.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-clearImplicitRules(): void--><!--Device-ProxyConfig-clearImplicitRules(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enableReverseBypass

```TypeScript
enableReverseBypass(reverse: boolean): void
```

Reverse the bypass rules. If false all URLs will use proxy settings except URLs match the bypass rules. If true only URLs in the bypass list will use proxy, and all other URLs will be connected to directly.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-enableReverseBypass(reverse: boolean): void--><!--Device-ProxyConfig-enableReverseBypass(reverse: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reverse | boolean | 是 | If reverse the bypass rule. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## getBypassRules

```TypeScript
getBypassRules(): Array<string>
```

Returns the bypass rules.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-getBypassRules(): Array<string>--><!--Device-ProxyConfig-getBypassRules(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | The bypass rules. |

## getProxyRules

```TypeScript
getProxyRules(): Array<ProxyRule>
```

Returns the proxy rules.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-getProxyRules(): Array<ProxyRule>--><!--Device-ProxyConfig-getProxyRules(): Array<ProxyRule>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ProxyRule&gt; | The proxy rules. |

## insertBypassRule

```TypeScript
insertBypassRule(bypassRule: string): void
```

Insert a bypass rule that indicates URLs that should skip the override proxy and connect the server directly instead. These maybe URLs or IP addresses and wildcards are supported. e.g. " *.example.com" means that requests to "https://www.example.com" and "http://test.example.com" will connect the server directly.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-insertBypassRule(bypassRule: string): void--><!--Device-ProxyConfig-insertBypassRule(bypassRule: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bypassRule | string | 是 | The bypass rule. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## insertDirectRule

```TypeScript
insertDirectRule(schemeFilter?: ProxySchemeFilter): void
```

Insert a proxy rule that indicates URLs that match the schemeFilter will connect the server directly.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-insertDirectRule(schemeFilter?: ProxySchemeFilter): void--><!--Device-ProxyConfig-insertDirectRule(schemeFilter?: ProxySchemeFilter): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemeFilter | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | The scheme filter for this rule. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## insertProxyRule

```TypeScript
insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void
```

Insert a proxy rule which indicates that requests matching the schemeFilter should use an override proxy, all requests will use the proxy rule if schemeFilter is null. The format for proxy is [scheme://]host[:port]. Scheme is optional and must be HTTP, HTTPS, or SOCKS if present. Scheme defaults to HTTP. Host is an IPv6 literal with brackets, an IPv4 literal or one or more labels seperated by a period. Port number is optional and defaults to 80 for HTTP, 443 for HTTPS and 1080 for SOCKS. e.g. example.com host: example.com https://example.com scheme: https host: example.com example.com:8888 host: example.com port: 8888 https://example.com:8888 scheme:https host: example.com port:8888 192.168.1.1 host: 192.168.1.1 192.168.1.1:8888 host:192.168.1.1 port: 8888 [10:20:30:40:50:60:70:80]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void--><!--Device-ProxyConfig-insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxyRule | string | 是 | The proxy rule. |
| schemeFilter | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | The scheme filter for this rule. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## isReverseBypassEnabled

```TypeScript
isReverseBypassEnabled(): boolean
```

Returns if reverse bypass rules.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ProxyConfig-isReverseBypassEnabled(): boolean--><!--Device-ProxyConfig-isReverseBypassEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If reverse bypass enabled. |

