# Class (ClientAuthenticationHandler)

Web组件返回的SSL客户端证书请求事件的处理对象。示例代码参考[onClientAuthenticationRequest事件](./arkts-basic-components-web-events.md#onclientauthenticationrequest9)。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块接口从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## constructor<sup>9+</sup>

constructor()

ClientAuthenticationHandler的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## confirm<sup>9+</sup>

confirm(priKeyFile : string, certChainFile : string): void

通知Web组件使用指定的私钥和客户端证书链。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型   | 必填   | 说明               |
| ------------- | ------ | ---- | ------------------ |
| priKeyFile    | string | 是    | 存放私钥文件的完整路径。  |
| certChainFile | string | 是    | 存放证书链文件的完整路径。 |

## confirm<sup>10+</sup>

confirm(authUri : string): void

通知Web组件使用指定的凭据(从证书管理模块获得)。

> **说明：**
>
> 需要配置权限：ohos.permission.ACCESS_CERT_MANAGER。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型   | 必填   | 说明    |
| ------- | ------ | ---- | ------- |
| authUri | string | 是    | 凭据的关键值。 |

## cancel<sup>9+</sup>

cancel(): void

通知Web组件取消相同host和port服务器发送的客户端证书请求事件。同时，相同host和port服务器的请求，不重复上报该事件。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## ignore<sup>9+</sup>

ignore(): void

通知Web组件忽略本次请求。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## 使用@ohos.transfer进行ClientAuthenticationHandler类型转换

ArkTS-Dyn中使用ArkTS-Sta的ClientAuthenticationHandler对象。

- 在ArkTS-Sta模块中将ArkTS-Sta ClientAuthenticationHandler转换成ArkTS-Dyn ClientAuthenticationHandler，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button, OnClientAuthenticationEvent } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { clientAuthenticationHandlerStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("Trigger onClientAuthenticationRequest")
          .onClick(() => {
            try {
              this.controller.loadUrl('https://client.badssl.com/');
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onClientAuthenticationRequest((event: OnClientAuthenticationEvent): void => {
            console.info('onClientAuthenticationRequest invoked');
            try {
              let dynamicHandler = transfer.transferDynamic(event.handler, 'ArkWeb.ClientAuthenticationHandler');
              clientAuthenticationHandlerStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn ClientAuthenticationHandler的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function clientAuthenticationHandlerStaticToDynamic(handler_: any) {
    try {
      let handler: ClientAuthenticationHandler = handler_ as ClientAuthenticationHandler;
      handler.cancel();
      console.info('clientAuthenticationHandlerStaticToDynamic done');
    } catch (e) {
      console.error('clientAuthenticationHandlerStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的ClientAuthenticationHandler对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn ClientAuthenticationHandler对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { clientAuthenticationHandlerDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("Trigger onClientAuthenticationRequest")
          .onClick(() => {
            try {
              this.controller.loadUrl('https://client.badssl.com/');
            } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onClientAuthenticationRequest((event: OnClientAuthenticationEvent): void => {
            if (event) {
              console.log("onClientAuthenticationRequest start");
              clientAuthenticationHandlerDynamicToStatic(event.handler);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn ClientAuthenticationHandler的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { ClientAuthenticationHandler } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function clientAuthenticationHandlerDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: ClientAuthenticationHandler = transfer.transferStatic(dynObject, 'ArkWeb.ClientAuthenticationHandler') as ClientAuthenticationHandler;
        handler.cancel();
        console.info('clientAuthenticationHandlerDynamicToStatic done');
    } catch (e: Error) {
        console.error('clientAuthenticationHandlerDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```