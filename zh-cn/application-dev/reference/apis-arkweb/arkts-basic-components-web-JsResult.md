# Class (JsResult)

Web组件返回的弹窗确认或弹窗取消功能对象。示例代码参考[onAlert事件](./arkts-basic-components-web-events.md#onalert)。

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

JsResult的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 20

## handleCancel

handleCancel(): void

通知Web组件用户取消弹窗操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 20

## handleConfirm

handleConfirm(): void

通知Web组件用户确认弹窗操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 20

## handlePromptConfirm<sup>9+</sup>

handlePromptConfirm(result: string): void

通知Web组件用户确认弹窗操作及对话框内容。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填   | 说明        |
| ------ | ------ | ---- | ----------- |
| result | string | 是    | 用户输入的对话框内容。 |

## 使用@ohos.transfer进行JsResult类型转换

ArkTS-Dyn中使用ArkTS-Sta的JsResult对象。

- 在ArkTS-Sta模块中将ArkTS-Sta JsResult转换成ArkTS-Dyn JsResult，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, OnPromptEvent, $rawfile } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { handleJsResultDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onPrompt((event: OnPromptEvent): boolean => {
            console.info('onPrompt invoked');
            try {
                let jsResultDynamic = transfer.transferDynamic(event.result, "ArkWeb.JsResult") as Object;
                handleJsResultDynamic(jsResultDynamic);
            } catch (e: Error) {
                console.error('transferDynamic catch error：-----------' + e.message);
            }
            return true;
          })
      }
    }
  }
  ```
  加载的html文件。
  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8">
  </head>

  <body>
    <h1>WebView onPrompt Demo</h1>
    <button onclick="myFunction()">Click here</button>
    <p id="demo"></p>
    <script>
      function myFunction() {
        let message = prompt("Message info", "Hello World");
        if (message != null && message != "") {
          document.getElementById("demo").innerHTML = message;
        }
      }
    </script>
  </body>
  </html>
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn JsResult的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function handleJsResultDynamic(result_: any) {
    let result: JsResult = result_ as JsResult;
    result.handlePromptConfirm("JsResult transfer success");
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的JsResult对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn JsResult对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { handleJsResultStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onPrompt((event: OnPromptEvent): boolean => {
            console.info('onPrompt invoked');
            handleJsResultStatic(event.result);
            return true;
          })
      }
    }
  }
  ```
  加载的html文件。
  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8">
  </head>

  <body>
    <h1>WebView onPrompt Demo</h1>
    <button onclick="myFunction()">Click here</button>
    <p id="demo"></p>
    <script>
      function myFunction() {
        let message = prompt("Message info", "Hello World");
        if (message != null && message != "") {
          document.getElementById("demo").innerHTML = message;
        }
      }
    </script>
  </body>
  </html>
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn JsResult的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { JsResult } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function handleJsResultStatic(dynObject: Object) {
    try {
        let result: JsResult = transfer.transferStatic(dynObject, "ArkWeb.JsResult") as JsResult;
        result.handlePromptConfirm("JsResult transfer success");
    } catch (e: Error) {
        console.error('transferStatic catch error：-----------' + e.message);
    }
  }
  ```