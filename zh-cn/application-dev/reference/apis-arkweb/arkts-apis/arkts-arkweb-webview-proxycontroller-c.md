# ProxyController

This class is used for set proxy for ArkWeb.

**起始版本：** 15

<!--Device-webview-class ProxyController--><!--Device-webview-class ProxyController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="applyproxyoverride"></a>
## applyProxyOverride

```TypeScript
static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void
```

设置应用中所有Web使用的代理配置，与[insertBypassRule](arkts-arkweb-webview-proxyconfig-c.md#insertbypassrule-1)中插入的bypass规则匹配的URL将不会使用代理，而是直接向URL指定的源地址发起请求。代理设置成功后，不保证网络连接后会立即使用新的代理设置，在加载页面之前请等待监听器触发，这个监听器将在UI线程上被调用。注意：调用 `applyProxyOverride` 会导致忽略任何现有的系统范围设置。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyController-static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void--><!--Device-ProxyController-static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxyConfig | [ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md) | 是 | 对代理的配置。 |
| callback | [OnProxyConfigChangeCallback](arkts-arkweb-webview-onproxyconfigchangecallback-t.md) | 是 | 代理设置成功的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

<a id="removeproxyoverride"></a>
## removeProxyOverride

```TypeScript
static removeProxyOverride(callback: OnProxyConfigChangeCallback): void
```

移除代理配置。移除代理配置后，不保证网络连接后会立即使用新的代理设置，在加载页面之前等待监听器，这个监听器将在UI线程上被调用。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyController-static removeProxyOverride(callback: OnProxyConfigChangeCallback): void--><!--Device-ProxyController-static removeProxyOverride(callback: OnProxyConfigChangeCallback): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnProxyConfigChangeCallback](arkts-arkweb-webview-onproxyconfigchangecallback-t.md) | 是 | 代理配置变更的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

