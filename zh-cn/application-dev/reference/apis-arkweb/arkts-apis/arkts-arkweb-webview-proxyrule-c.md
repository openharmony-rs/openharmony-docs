# ProxyRule

The ProxyRule used by insertProxyRule.

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

<!--Device-webview-class ProxyRule--><!--Device-webview-class ProxyRule-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getSchemeFilter

```TypeScript
getSchemeFilter(): ProxySchemeFilter
```

获取代理规则中的ProxySchemeFilter信息。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyRule-getSchemeFilter(): ProxySchemeFilter--><!--Device-ProxyRule-getSchemeFilter(): ProxySchemeFilter-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProxySchemeFilter](../../apis-na/arkts-apis/arkts-na-webview-proxyschemefilter-e.md) | 代理规则中的ProxySchemeFilter信息。 |

## getUrl

```TypeScript
getUrl(): string
```

获取代理规则中的代理的Url信息。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyRule-getUrl(): string--><!--Device-ProxyRule-getUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 代理规则中的代理的Url信息。 |

