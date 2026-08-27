# PrefetchOptions

PrefetchOptions是ArkWeb框架中用于自定义网页预取行为的配置类，通过 [prefetchPage](arkts-arkweb-webview-webviewcontroller-c.md#prefetchpage) 的预取相关接口设置，自定义内容包括是否忽略响应头中的Cache-Control: no-store和设置两次预取间的最小时间间隔。

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

PrefetchOptions的构造函数。

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
import { webview, WebNetErrorList } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('response').onClick(() => {
        let response = new webview.WebSchemeHandlerResponse();
        try {
          response.setUrl("http://www.example.com")
          response.setStatus(200)
          response.setStatusText("OK")
          response.setMimeType("text/html")
          response.setEncoding("utf-8")
          response.setHeaderByName("header1", "value1", false)
          response.setNetErrorCode(WebNetErrorList.NET_OK)
          console.info("[schemeHandler] getUrl:" + response.getUrl())
          console.info("[schemeHandler] getStatus:" + response.getStatus())
          console.info("[schemeHandler] getStatusText:" + response.getStatusText())
          console.info("[schemeHandler] getMimeType:" + response.getMimeType())
          console.info("[schemeHandler] getEncoding:" + response.getEncoding())
          console.info("[schemeHandler] getHeaderByName:" + response.getHeaderByName("header1"))
          console.info("[schemeHandler] getNetErrorCode:" + response.getNetErrorCode())

        } catch (error) {
          console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
        }
      })
      Web({ src: 'https://www.example.com', controller: this.controller })
    }
  }
}
```

## ignoreCacheControlNoStore

```TypeScript
ignoreCacheControlNoStore: boolean
```

设置是否忽略响应头中的Cache-Control: no-store。设置为true时忽略，为false时不忽略。

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## minTimeBetweenPrefetchesMs

```TypeScript
minTimeBetweenPrefetchesMs: number
```

设置两次网页预取的最小时间间隔。每次预取时会计算和上次预取的间隔时间，若小于设置值，则取消本次预取。取值范围[0, 500]。设置为负数时，默认为0。单位：ms

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core
