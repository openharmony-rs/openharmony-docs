# ProxyController

This class is used for set proxy for ArkWeb.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class ProxyController--><!--Device-webview-class ProxyController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## applyProxyOverride

```TypeScript
static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void
```

Sets ProxyConfig which will be used by all Webs in the app. URLs that match patterns in the bypass list will connect the server directly. Instead, the request will use the proxy specified by the config. Requests are not guaranteed to use the new proxy immediately; wait for the listener before loading a page. This listener will be called on the UI thread. Note: calling applyProxyOverride will cause any existing system wide setting to be ignored.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ProxyController-static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void--><!--Device-ProxyController-static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxyConfig | [ProxyConfig](arkts-na-webview-proxyconfig-c.md) | 是 | The proxy config. |
| callback | [OnProxyConfigChangeCallback](arkts-na-webview-onproxyconfigchangecallback-t.md) | 是 | Called when the proxy has been changed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

## removeProxyOverride

```TypeScript
static removeProxyOverride(callback: OnProxyConfigChangeCallback): void
```

Remove the proxy config. Requests are not guaranteed to not use the proxy; Wait for the listener before loading a page. This listener will be called on the UI thread.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ProxyController-static removeProxyOverride(callback: OnProxyConfigChangeCallback): void--><!--Device-ProxyController-static removeProxyOverride(callback: OnProxyConfigChangeCallback): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnProxyConfigChangeCallback](arkts-na-webview-onproxyconfigchangecallback-t.md) | 是 | Called when the proxy has been changed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

