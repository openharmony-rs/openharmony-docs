# ProxyController

ProxyController是ArkWeb框架中用于管理应用中所有Web组件代理配置的静态类。通过ProxyController，开发者可以统一为应用中的所有Web请求设置或移除代理配置，适用于需要将Web流量路由到特定代理服务 器的场景（如企业网络环境、内容过滤、流量监控等）。 ProxyController提供两个核心方法：applyProxyOverride用于应用代理配置，接受一个[ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md)对象和代理设置成功的回调函数； removeProxyOverride用于移除当前代理配置，恢复为默认网络连接方式。需要注意的是，代理设置或移除后不会立即生效，在加载页面之前需等待回调函数触发，该回调函数会在UI线程上被调用。

**起始版本：** 15

<!--Device-webview-class ProxyController--><!--Device-webview-class ProxyController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## applyProxyOverride

```TypeScript
static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void
```

设置应用中所有Web使用的代理配置，与[insertBypassRule](arkts-arkweb-webview-proxyconfig-c.md#insertbypassrule)中插入的bypass规则匹配的URL将不会使用代理，而是直接向 URL指定的源地址发起请求。代理设置成功后，不保证网络连接后会立即使用新的代理配置，在加载页面之前请等待回调函数触发，该回调函数将在UI线程上被调用。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyController-static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void--><!--Device-ProxyController-static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxyConfig | [ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md) | 是 | 对代理的配置。 |
| callback | [OnProxyConfigChangeCallback](arkts-arkweb-webview-onproxyconfigchangecallback-t.md) | 是 | 代理配置变更的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## removeProxyOverride

```TypeScript
static removeProxyOverride(callback: OnProxyConfigChangeCallback): void
```

移除代理配置。移除代理配置后，不保证网络连接后会立即恢复为默认网络连接方式，在加载页面之前等待回调函数触发，该回调函数将在UI线程上被调用。

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

