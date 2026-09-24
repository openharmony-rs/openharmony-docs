# ProxyController

```TypeScript
class ProxyController
```

ProxyController is a static class in the ArkWeb framework used to manage the proxy configuration of all Web components in an app. With ProxyController, developers can uniformly set or remove proxy configurations for all Web requests in the app, which is suitable for scenarios where Web traffic needs to be routed to a specific proxy server (such as enterprise network environments, content filtering, and traffic monitoring).

ProxyController provides two core methods: **applyProxyOverride** is used to apply a proxy configuration, which accepts a [ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md) object and a callback function for successful proxy setup; **removeProxyOverride** is used to remove the current proxy configuration and restore the default network connection. Note that the proxy setting or removal does not take effect immediately. Before loading a page, wait for the callback function to be triggered. The callback function is invoked on the UI thread.

**Since:** 15

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## applyProxyOverride

```TypeScript
static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void
```

Sets the proxy configuration used by all Web instances in the app. URLs that match the bypass rules inserted through [insertBypassRule](arkts-arkweb-webview-proxyconfig-c.md#insertbypassrule) will not use the proxy but instead send requests directly to the origin address specified by the URL. After the proxy is successfully set, there is no guarantee that the new proxy configuration will be used immediately after the network is connected. Before loading a page, wait for the callback function to be triggered. The callback function is invoked on the UI thread.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| proxyConfig | [ProxyConfig](arkts-arkweb-webview-proxyconfig-c.md) | Yes | Configuration of the proxy. |
| callback | [OnProxyConfigChangeCallback](arkts-arkweb-webview-onproxyconfigchangecallback-t.md) | Yes | Callback invoked when the proxy configuration changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

**Examples**

For details about the sample code, see [removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride).

## removeProxyOverride

```TypeScript
static removeProxyOverride(callback: OnProxyConfigChangeCallback): void
```

Removes the proxy configuration. After the proxy configuration is removed, there is no guarantee that the default network connection will be restored immediately after the network is connected. Before loading a page, wait for the callback function to be triggered. The callback function is invoked on the UI thread.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnProxyConfigChangeCallback](arkts-arkweb-webview-onproxyconfigchangecallback-t.md) | Yes | Callback for proxy configuration changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  proxyRules: webview.ProxyRule[] = [];

  build() {
    Row() {
      Column() {
        Button("applyProxyOverride").onClick(()=>{
          let proxyConfig:webview.ProxyConfig = new webview.ProxyConfig();
          // Use the first proxy configuration https://proxy.XXX.com first
          // Fall back to direct server connection insertDirectRule after proxy failure.
          try {
            proxyConfig.insertProxyRule("https://proxy.XXX.com", webview.ProxySchemeFilter.MATCH_ALL_SCHEMES);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
          try {
            proxyConfig.insertDirectRule(webview.ProxySchemeFilter.MATCH_HTTP);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
          try {
            proxyConfig.insertBypassRule("*.example.com");
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
          proxyConfig.clearImplicitRules();
          proxyConfig.bypassHostnamesWithoutPeriod();
          try {
            proxyConfig.enableReverseBypass(true);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
          let bypassRules = proxyConfig.getBypassRules();
          for (let i = 0; i < bypassRules.length; i++) {
            console.info("bypassRules: " + bypassRules[i]);
          }
          this.proxyRules = proxyConfig.getProxyRules();
          for (let i = 0; i < this.proxyRules.length; i++) {
            console.info("SchemeFilter: " + this.proxyRules[i].getSchemeFilter());
            console.info("Url: " + this.proxyRules[i].getUrl());
          }
          let isReverseBypassRule = proxyConfig.isReverseBypassEnabled();
          console.info("isReverseBypassRules: " + isReverseBypassRule);
          try {
            webview.ProxyController.applyProxyOverride(proxyConfig, () => {
              console.info("PROXYCONTROLLER proxy changed");
            });
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
        Button("loadUrl-https").onClick(()=>{
          this.controller.loadUrl("https://www.example.com")
        })
        Button("loadUrl-http").onClick(()=>{
          this.controller.loadUrl("http://www.example.com")
        })
        Button("removeProxyOverride").onClick(()=>{
          try {
            webview.ProxyController.removeProxyOverride(() => {
            console.info("PROXYCONTROLLER proxy changed");
          });
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
        Web({ src: 'www.example.com', controller: this.controller})
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
