# ProxyRule

ProxyRule是ArkWeb框架中代理规则只读信息的类，通过[getProxyRules](arkts-arkweb-webview-proxyconfig-c.md#getproxyrules)方法获取。当开发者通过ProxyConfig配置了代理 规则后，可通过getProxyRules获取已配置的规则列表，每条规则对应一个ProxyRule对象，用于查询规则的详细信息。ProxyRule提供两个方法：getSchemeFilter用于获取该代理规则对应的协议过滤器（如MATCH_ALL_SCHEMES、MATCH_HTTP、MATCH_HTTPS等），getUrl用于获取该代理规则中指定的代理服 务器URL信息。ProxyRule对象为只读，由系统在配置代理规则时创建，应用只能查询其内容而不能修改。

**起始版本：** 15

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## getSchemeFilter

```TypeScript
getSchemeFilter(): ProxySchemeFilter
```

获取代理规则中的ProxySchemeFilter信息。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | 代理规则中的ProxySchemeFilter信息。 |

**示例**

完整示例代码参考[removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride)。

## getUrl

```TypeScript
getUrl(): string
```

获取代理规则中代理的URL信息。

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 代理规则中代理的URL信息。 |

**示例**

完整示例代码参考[removeProxyOverride](./arkts-apis-webview-ProxyController.md#removeproxyoverride)。

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  delegate: webview.WebDownloadDelegate = new webview.WebDownloadDelegate();

  build() {
    Column() {
      Button('setDownloadDelegate')
        .onClick(() => {
          try {
            this.delegate.onBeforeDownload((webDownloadItem: webview.WebDownloadItem) => {
              console.info("will start a download, url:" + webDownloadItem.getUrl());
              // 传入一个下载路径，并开始下载。
              webDownloadItem.start("/data/storage/el2/base/cache/web/" + webDownloadItem.getSuggestedFileName());
            })
            this.delegate.onDownloadUpdated((webDownloadItem: webview.WebDownloadItem) => {
              console.info("download update percent complete: " + webDownloadItem.getPercentComplete());
            })
            this.delegate.onDownloadFailed((webDownloadItem: webview.WebDownloadItem) => {
              console.error("download failed guid: " + webDownloadItem.getGuid());
            })
            this.delegate.onDownloadFinish((webDownloadItem: webview.WebDownloadItem) => {
              console.info("download finish guid: " + webDownloadItem.getGuid());
            })
            this.controller.setDownloadDelegate(this.delegate);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('startDownload')
        .onClick(() => {
          try {
            this.controller.startDownload('https://www.example.com');
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

完整示例代码参考constructor。

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('getUrl')
        .onClick(() => {
          try {
            let url = this.controller.getUrl();
            console.info("url: " + url);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```
