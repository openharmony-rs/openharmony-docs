# ProxyConfig

ProxyConfig是ArkWeb框架中用于配置网络代理规则的类，配合[ProxyController](arkts-arkweb-webview-proxycontroller-c.md)实现对应用中所有Web组件网络请求的代理控制。通过 ProxyConfig，开发者可以灵活定义多种代理规则：指定特定URL使用特定代理服务器、指定某些URL直连服务器、定义绕过代理的规则等。

**起始版本：** 15

<!--Device-webview-class ProxyConfig--><!--Device-webview-class ProxyConfig-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## bypassHostnamesWithoutPeriod

```TypeScript
bypassHostnamesWithoutPeriod(): void
```

没有点字符的域名将绕过代理并直接连接到服务器。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-bypassHostnamesWithoutPeriod(): void--><!--Device-ProxyConfig-bypassHostnamesWithoutPeriod(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## clearImplicitRules

```TypeScript
clearImplicitRules(): void
```

默认情况下，如果某些主机名是本地IP地址或localhost地址，它们会绕过代理。调用此函数以覆盖默认行为，并强制将localhost或本地IP地址通过代理发送。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-clearImplicitRules(): void--><!--Device-ProxyConfig-clearImplicitRules(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enableReverseBypass

```TypeScript
enableReverseBypass(reverse: boolean): void
```

反转bypass规则。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-enableReverseBypass(reverse: boolean): void--><!--Device-ProxyConfig-enableReverseBypass(reverse: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reverse | boolean | 是 | 参数值默认是false，表示与[insertBypassRule](#insertbypassrule)中的 bypassRule匹配的URL会绕过代理，参数值为true时，表示与[insertBypassRule](#insertbypassrule)中的bypassRule 匹配的URL会使用代理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## getBypassRules

```TypeScript
getBypassRules(): Array<string>
```

获取不使用代理的URL列表。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-getBypassRules(): Array<string>--><!--Device-ProxyConfig-getBypassRules(): Array<string>-End-->

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

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-getProxyRules(): Array<ProxyRule>--><!--Device-ProxyConfig-getProxyRules(): Array<ProxyRule>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ProxyRule](arkts-arkweb-webview-proxyrule-c.md)&gt; | 代理规则，每个ProxyRule对象表示一条已配置的代理规则。 |

## insertBypassRule

```TypeScript
insertBypassRule(bypassRule: string): void
```

插入一条bypass规则，指明哪些URL应该绕过代理并直接连接到服务器。当[enableReverseBypass](#enablereversebypass)设置为true 时，与bypassRule匹配的URL会使用代理而非绕过代理。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-insertBypassRule(bypassRule: string): void--><!--Device-ProxyConfig-insertBypassRule(bypassRule: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bypassRule | string | 是 | bypass规则字符串，用于指定绕过代理的URL匹配规则，支持主机名或域名格式（如"example.com"匹配该域名及其子域名）。与bypassRule匹配的 URL会绕过代理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## insertDirectRule

```TypeScript
insertDirectRule(schemeFilter?: ProxySchemeFilter): void
```

插入一条直连规则，指明符合schemeFilter条件的URL将直接连接到服务器。 > **说明：** > > - 与[insertBypassRule](#insertbypassrule)和 > [bypassHostnamesWithoutPeriod](#bypasshostnameswithoutperiod)均可实现URL直连，区别在于匹配维度：本方法通过 > schemeFilter按协议类型匹配；insertBypassRule通过bypassRule字符串按URL模式匹配；bypassHostnamesWithoutPeriod无需传参，自动对不含点号的域名直连。可根据需要 > 直连的URL范围选择合适的方法。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-insertDirectRule(schemeFilter?: ProxySchemeFilter): void--><!--Device-ProxyConfig-insertDirectRule(schemeFilter?: ProxySchemeFilter): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| schemeFilter | [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | 否 | 与schemeFilter匹配的URL会直接与服务器相连。 <br>默认值：MATCH_ALL_SCHEMES。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## insertProxyRule

```TypeScript
insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void
```

插入一条代理规则，与schemeFilter匹配的URL都会使用指定代理。如果未指定schemeFilter参数，将使用默认值MATCH_ALL_SCHEMES，所有URL都将使用指定代理。 代理格式为[scheme://]host[:port]。 scheme是可选的，必须是HTTP、HTTPS或SOCKS。scheme默认值为HTTP。 host是带括号的IPv6字面量、IPv4字面量或由点分隔的一个或多个标签。 端口号是可选的，默认HTTP为80、HTTPS为443、SOCKS为1080。 例如： - example.com host: example.com - https://example.com scheme: https host: example.com - example.com:8888 host: example.com port: 8888 - https://example.com:8888 scheme: https host: example.com port: 8888 - 192.168.1.1 host: 192.168.1.1 - 192.168.1.1:8888 host: 192.168.1.1 port: 8888 - [10:20:30:40:50:60:70:80]

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void--><!--Device-ProxyConfig-insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxyRule | string | 是 | URL要使用的代理。 |
| schemeFilter | [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | 否 | 与schemeFilter匹配的URL会使用代理。 <br>默认值：MATCH_ALL_SCHEMES。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## isReverseBypassEnabled

```TypeScript
isReverseBypassEnabled(): boolean
```

获取[enableReverseBypass](#enablereversebypass)的参数值，详见 [enableReverseBypass](#enablereversebypass)。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyConfig-isReverseBypassEnabled(): boolean--><!--Device-ProxyConfig-isReverseBypassEnabled(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | [enableReverseBypass]{ |

