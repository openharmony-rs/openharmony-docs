# ProxyConfig

The ProxyConfig used by applyProxyOverride.

**起始版本：** 15

**系统能力：** SystemCapability.Web.Webview.Core

## bypassHostnamesWithoutPeriod

```TypeScript
bypassHostnamesWithoutPeriod(): void
```

主机名中不包含句点（且不是IP字面量）的主机名将跳过代理，直接连接到服务器。示例："abc"、"local"、"some-domain"。

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## clearImplicitRules

```TypeScript
clearImplicitRules(): void
```

默认情况下，某些主机名如果属于链路本地 IP 或 localhost 地址，则会自动绕过代理。
例如，匹配以下任意条件（非详尽列表）的主机名：localhost、*.localhost、[::1]、127.0.0.1/8、169.254/16、[FE80::]/10。
调用此函数可覆盖默认行为，并强制将 localhost 和链路本地 URL 通过代理发送。

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## enableReverseBypass

```TypeScript
enableReverseBypass(reverse: boolean): void
```

反转bypass规则。

若为 false，所有URL都将使用代理设置，除非URL匹配了绕过规则。
若为 true，仅绕过列表中的URL会使用代理，其余所有URL都将直接连接。

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reverse | boolean | 是 | 参数值默认是false，表示与[insertBypassRule](arkts-arkweb-proxyconfig-c.md#insertbypassrule-1)中的bypassRule匹配的URL会绕过代理，参数值为true时，表示与[insertBypassRule](arkts-arkweb-proxyconfig-c.md#insertbypassrule-1)中的bypassRule匹配的URL会使用代理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## getBypassRules

```TypeScript
getBypassRules(): Array<string>
```

获取不使用代理的URL列表。

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 不使用代理的URL列表。 |

## getProxyRules

```TypeScript
getProxyRules(): Array<ProxyRule>
```

获取代理规则。

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ProxyRule&gt; | 代理规则。 |

## insertBypassRule

```TypeScript
insertBypassRule(bypassRule: string): void
```

插入一个旁路规则，该规则指示哪些URL应跳过覆盖代理，直接连接到服务器。
这些可能是URL或IP地址，并且支持通配符。例如，"*.example.com" 表示对以下地址的请求：
"https://www.example.com"和"http://test.example.com"将直接连接服务器。

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bypassRule | string | 是 | 与bypassRule匹配的URL会绕过代理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## insertDirectRule

```TypeScript
insertDirectRule(schemeFilter?: ProxySchemeFilter): void
```

插入一条代理规则，指明符合schemeFilter条件的URL将直接连接到服务器。

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemeFilter | ProxySchemeFilter | 否 | 与schemeFilter匹配的URL会直接与服务器相连。<br>默认值：MATCH_ALL_SCHEMES。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## insertProxyRule

```TypeScript
insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void
```

插入一条代理规则，与schemeFilter匹配的URL都会使用指定代理。如果schemeFilter为空，所有URL都将使用指定代理。
use the proxy rule if schemeFilter is null.

代理的格式为[scheme://]host[:port]。Scheme是可选的，如果存在，必须为 HTTP、HTTPS 或 SOCKS。Scheme默认为 HTTP。
host可以是带括号的 IPv6 字面量、IPv4 字面量，或者一个或多个由点分隔的标签。port是可选的，默认为 HTTP 的 80、
HTTPS 的 443 和 SOCKS 的 1080。

例如 example.com host: example.com
https://example.com scheme: https host: example.com
example.com:8888 host: example.com port: 8888
https://example.com:8888 scheme:https host: example.com port:8888
192.168.1.1 host: 192.168.1.1
192.168.1.1:8888 host:192.168.1.1 port: 8888
[10:20:30:40:50:60:70:80]

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxyRule | string | 是 | URL要使用的代理。 |
| schemeFilter | ProxySchemeFilter | 否 | 与schemeFilter匹配的URL会使用代理。<br>默认值：MATCH_ALL_SCHEMES。<br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## isReverseBypassEnabled

```TypeScript
isReverseBypassEnabled(): boolean
```

Returns if reverse bypass rules.

**起始版本：** 15

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | If reverse bypass enabled. |

