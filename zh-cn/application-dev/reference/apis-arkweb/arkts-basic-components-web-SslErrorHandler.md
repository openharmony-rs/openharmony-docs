# Class (SslErrorHandler)

Web组件返回的SSL错误通知事件的处理对象。示例代码参考[onSslErrorEvent](./arkts-basic-components-web-events.md#onsslerrorevent12)事件。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## constructor<sup>9+</sup>

constructor()

SslErrorHandler的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## handleCancel<sup>9+</sup>

handleCancel(): void

通知Web组件取消此请求。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## handleConfirm<sup>9+</sup>

handleConfirm(): void

通知Web组件继续使用SSL证书。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## handleCancel<sup>20+</sup>

handleCancel(abortLoading: boolean): void

通知Web组件取消此请求，并根据参数abortLoading决定是否停止加载。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名          | 类型 | 必填  | 说明             |
| --------------- | -------- | ----  |------- |
| abortLoading    | boolean  | 是    | 是否在取消请求后停止加载页面。<br>true表示停止加载页面，false表示继续加载页面。<br>默认值为false。 |

## 使用@ohos.transfer进行SslErrorHandler类型转换

ArkTS-Dyn中使用ArkTS-Sta的SslErrorHandler对象。

- 在ArkTS-Sta模块中将ArkTS-Sta SslErrorHandler转换成ArkTS-Dyn SslErrorHandler，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button, OnSslErrorEventReceiveEvent } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { sslErrorHandlerStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("Trigger onSslErrorEventReceive")
          .onClick(() => {
            try {
              this.controller.loadUrl('https://untrusted-root.badssl.com/');
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onSslErrorEventReceive((event: OnSslErrorEventReceiveEvent): void => {
            console.info('onSslErrorEventReceive invoked');
            try {
              let dynamicHandler = transfer.transferDynamic(event.handler, 'ArkWeb.SslErrorHandler');
              sslErrorHandlerStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn SslErrorHandler的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function sslErrorHandlerStaticToDynamic(handler_: any) {
    try {
      let handler: SslErrorHandler = handler_ as SslErrorHandler;
      handler.handleCancel();
      console.info('sslErrorHandlerStaticToDynamic done');
    } catch (e) {
      console.error('sslErrorHandlerStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的SslErrorHandler对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn SslErrorHandler对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { sslErrorHandlerDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("Trigger onSslErrorEventReceive")
          .onClick(() => {
            try {
              this.controller.loadUrl('https://untrusted-root.badssl.com/');
            } catch (error) {
              console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onSslErrorEventReceive((event: OnSslErrorEventReceiveEvent): void => {
            if (event) {
              console.info("onSslErrorEventReceive start");
              sslErrorHandlerDynamicToStatic(event.handler);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn SslErrorHandler的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { SslErrorHandler } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function sslErrorHandlerDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: SslErrorHandler = transfer.transferStatic(dynObject, 'ArkWeb.SslErrorHandler') as SslErrorHandler;
        handler.handleCancel();
        console.info('sslErrorHandlerDynamicToStatic done');
    } catch (e: Error) {
        console.error('sslErrorHandlerDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```