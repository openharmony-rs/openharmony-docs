# Class (ConsoleMessage)

Web组件获取控制台信息对象。示例代码参考[onConsole事件](./arkts-basic-components-web-events.md#onconsole)。

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

constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)

ConsoleMessage的构造函数。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用[constructor](#constructor9)代替。

**系统能力：** SystemCapability.Web.Webview.Core

## constructor<sup>9+</sup>

constructor()

ConsoleMessage的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

## getLineNumber

ArkTS-Dyn: getLineNumber(): number

ArkTS-Sta: getLineNumber(): int

获取ConsoleMessage的行数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型     | 说明                   |
| ------ | -------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 返回ConsoleMessage的行数。 |

## getMessage

getMessage(): string

获取ConsoleMessage的日志信息。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型     | 说明                     |
| ------ | ---------------------- |
| string | 返回ConsoleMessage的日志信息。 |

## getMessageLevel

getMessageLevel(): MessageLevel

获取ConsoleMessage的信息级别。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型                                | 说明                     |
| --------------------------------- | ---------------------- |
| [MessageLevel](./arkts-basic-components-web-e.md#messagelevel) | 返回ConsoleMessage的信息级别。 |

## getSourceId

getSourceId(): string

获取网页源文件路径和名字。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| string | 返回网页源文件路径和名字。 |

## 使用@ohos.transfer进行ConsoleMessage类型转换

ArkTS-Dyn中使用ArkTS-Sta的ConsoleMessage对象。

- 在ArkTS-Sta模块中将ArkTS-Sta ConsoleMessage转换成ArkTS-Dyn ConsoleMessage，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button, $rawfile, OnConsoleEvent } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { consoleMessageStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("Trigger onConsole")
          .onClick(() => {
            try {
              this.controller.loadUrl($rawfile('console.html'));
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onConsole((event: OnConsoleEvent): boolean => {
            console.info('onConsole invoked');
            try {
              let dynamicHandler = transfer.transferDynamic(event.message, 'ArkWeb.ConsoleMessage');
              consoleMessageStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
            return false;
          })
      }
    }
  }
  ```
  加载的console.html文件。
  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <body>
  <script>
      function myFunction() {
          console.log("test onconsole printf");
      }
  </script>
  <button style="width: 200px; height: 100px;" onclick="myFunction()">打印日志</button>
  </body>
  </html>
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn ConsoleMessage的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function consoleMessageStaticToDynamic(handler_: any) {
    try {
      let response: ConsoleMessage = handler_ as ConsoleMessage;
      let result: number = response.getLineNumber();
      console.info('consoleMessageStaticToDynamic result=' + result);
    } catch (e) {
      console.error('consoleMessageStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的ConsoleMessage对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn ConsoleMessage对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { consoleMessageDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("Trigger onConsole")
          .onClick(() => {
            try {
              this.controller.loadUrl($rawfile('console.html'));
            } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onConsole((event: OnConsoleEvent): boolean => {
            if (event) {
              console.log("onConsole start");
              consoleMessageDynamicToStatic(event.message);
            }
            return true;
          })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn ConsoleMessage的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { ConsoleMessage } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function consoleMessageDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: ConsoleMessage = transfer.transferStatic(dynObject, 'ArkWeb.ConsoleMessage') as ConsoleMessage;
        let result: number = handler.getLineNumber();
        console.info('consoleMessageDynamicToStatic result=' + result);
    } catch (e: Error) {
        console.error('consoleMessageDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```