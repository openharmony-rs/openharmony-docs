# ProxyRule

The ProxyRule used by insertProxyRule.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-class ProxyRule--><!--Device-webview-class ProxyRule-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## getSchemeFilter

```TypeScript
getSchemeFilter(): ProxySchemeFilter
```

Returns the scheme filter used for this rule.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ProxyRule-getSchemeFilter(): ProxySchemeFilter--><!--Device-ProxyRule-getSchemeFilter(): ProxySchemeFilter-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProxySchemeFilter](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-proxyschemefilter-e.md) | The scheme filter used for this rule. |

## getUrl

```TypeScript
getUrl(): string
```

Returns the proxy URL.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ProxyRule-getUrl(): string--><!--Device-ProxyRule-getUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The proxy URL. |

