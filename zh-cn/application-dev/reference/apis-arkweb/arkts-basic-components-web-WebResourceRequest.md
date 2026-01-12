# Class (WebResourceRequest)

Web组件获取资源请求对象。示例代码参考[onErrorReceive事件](./arkts-basic-components-web-events.md#onerrorreceive)。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 8开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## constructor

constructor()

WebResourceRequest的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

## getRequestHeader

getRequestHeader(): Array\<Header\>

获取资源请求头信息。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                         | 说明         |
| -------------------------- | ---------- |
| Array\<[Header](./arkts-basic-components-web-i.md#header)\> | 返回资源请求头信息。 |

## getRequestUrl

getRequestUrl(): string

获取资源请求的URL信息。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| string | 返回资源请求的URL信息。 |

## isMainFrame

isMainFrame(): boolean

判断资源请求是否为主frame。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型      | 说明               |
| ------- | ---------------- |
| boolean | 返回资源请求是否为主frame。<br>true表示返回资源请求为主frame，false表示返回资源请求不为主frame。 |

## isRedirect

isRedirect(): boolean

判断资源请求是否被服务端重定向。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型      | 说明               |
| ------- | ---------------- |
| boolean | 返回资源请求是否被服务端重定向。<br>true表示返回资源请求被服务端重定向，false表示返回资源请求未被服务端重定向。 |

## isRequestGesture

isRequestGesture(): boolean

获取资源请求是否与手势（如点击）相关联。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型      | 说明                   |
| ------- | -------------------- |
| boolean | 返回资源请求是否与手势（如点击）相关联。<br>true表示返回资源请求与手势（如点击）相关联，false表示返回资源请求与手势（如点击）不相关联。 |

## getRequestMethod<sup>9+</sup>

getRequestMethod(): string

获取请求方法。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明      |
| ------ | ------- |
| string | 返回请求方法。 |

## 使用@ohos.transfer进行WebResourceRequest类型转换

ArkTS-Dyn中使用ArkTS-Sta的WebResourceRequest对象。

- 在ArkTS-Sta模块中将ArkTS-Sta WebResourceRequest转换成ArkTS-Dyn WebResourceRequest，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button, OnHttpErrorReceiveEvent } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { webResourceRequestStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("Trigger onHttpErrorReceive")
          .onClick(() => {
            try {
              this.controller.loadUrl('http://httpbin.org/post');
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onHttpErrorReceive((parameter: OnHttpErrorReceiveEvent): void => {
            console.info('onHttpErrorReceive invoked');
            try {
              let dynamicHandler = transfer.transferDynamic(parameter.request, 'ArkWeb.WebResourceRequest');
              webResourceRequestStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebResourceRequest的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function webResourceRequestStaticToDynamic(handler_: any) {
    try {
      let request: WebResourceRequest = handler_ as WebResourceRequest;
      let result: string = request.getRequestUrl();
      console.info('webResourceRequestStaticToDynamic result=' + result);
    } catch (e) {
      console.error('webResourceRequestStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的WebResourceRequest对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn WebResourceRequest对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { webResourceRequestDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("Trigger onHttpErrorReceive")
          .onClick(() => {
            try {
              this.controller.loadUrl('http://httpbin.org/post');
            } catch (error) {
              console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onHttpErrorReceive((parameter: OnHttpErrorReceiveEvent): void => {
            if (parameter) {
              console.info("onHttpErrorReceive start");
              webResourceRequestDynamicToStatic(parameter.request);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebResourceRequest的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { WebResourceRequest } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function webResourceRequestDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let request: WebResourceRequest = transfer.transferStatic(dynObject, 'ArkWeb.WebResourceRequest') as WebResourceRequest;
        let result: string = request.getRequestUrl();
        console.info('webResourceRequestDynamicToStatic result=' + result);
    } catch (e: Error) {
        console.error('webResourceRequestDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```