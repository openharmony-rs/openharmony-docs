# Class (HttpAuthHandler)

Web组件返回的http auth认证请求确认或取消和使用缓存密码认证功能对象。示例代码参考[onHttpAuthRequest事件](./arkts-basic-components-web-events.md#onhttpauthrequest9)。

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

HttpAuthHandler的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## cancel<sup>9+</sup>

cancel(): void

通知Web组件用户取消HTTP认证操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## confirm<sup>9+</sup>

confirm(userName: string, password: string): boolean

使用用户名和密码进行HTTP认证操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型   | 必填  | 说明       |
| -------- | ------ | ---- | ---------- |
| userName | string | 是   | HTTP认证用户名。 |
| password      | string | 是   | HTTP认证密码。  |

**返回值：**

| 类型      | 说明                    |
| ------- | --------------------- |
| boolean | 认证成功返回true，失败返回false。 |

## isHttpAuthInfoSaved<sup>9+</sup>

isHttpAuthInfoSaved(): boolean

通知Web组件用户使用服务器缓存的账号密码认证。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型      | 说明                        |
| ------- | ------------------------- |
| boolean | 存在密码认证成功返回true，其他返回false。 |

## 使用@ohos.transfer进行HttpAuthHandler类型转换

ArkTS-Dyn中使用ArkTS-Sta的HttpAuthHandler对象。

- 在ArkTS-Sta模块中将ArkTS-Sta HttpAuthHandler转换成ArkTS-Dyn HttpAuthHandler，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button, OnHttpAuthRequestEvent } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { httpAuthHandlerStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("Trigger onHttpAuthRequest")
          .onClick(() => {
            try {
              this.controller.loadUrl('http://httpbin.org/basic-auth/2222/3333');
            } catch (e: Error) {
                console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onHttpAuthRequest((event: OnHttpAuthRequestEvent): boolean => {
            console.info('onHttpAuthRequest invoked');
            try {
              let dynamicHandler = transfer.transferDynamic(event.handler, 'ArkWeb.HttpAuthHandler');
              httpAuthHandlerStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
                console.error('transferDynamic catch error：-----------' + e.message);
            }
            return false;
          })
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn HttpAuthHandler的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function httpAuthHandlerStaticToDynamic(handler_: any) {
    try {
      let handler: HttpAuthHandler = handler_ as HttpAuthHandler;
      let result: boolean = handler.isHttpAuthInfoSaved();
      console.info('httpAuthHandlerStaticToDynamic result=' + result);
    } catch (e) {
        console.error('httpAuthHandlerStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的HttpAuthHandler对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn HttpAuthHandler对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { httpAuthHandlerDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("Trigger onHttpAuthRequest")
          .onClick((e: ClickEvent) => {
            try {
              this.controller.loadUrl('http://httpbin.org/basic-auth/2222/3333');
            } catch (error) {
              console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onHttpAuthRequest((event: OnHttpAuthRequestEvent): boolean => {
            if (event) {
              console.log("onHttpAuthRequest start");
              httpAuthHandlerDynamicToStatic(event.handler);
            }
            return true;
          })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn HttpAuthHandler的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { HttpAuthHandler } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function httpAuthHandlerDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: HttpAuthHandler = transfer.transferStatic(dynObject, 'ArkWeb.HttpAuthHandler') as HttpAuthHandler;
        let result: boolean = handler.isHttpAuthInfoSaved();
        console.info('httpAuthHandlerDynamicToStatic result=' + result);
    } catch (e: Error) {
        console.error('transferStatic catch error：-----------' + e.message);
    }
  }
  ```