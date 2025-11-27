# Class (DataResubmissionHandler)

通过DataResubmissionHandler可以重新提交表单数据或取消提交表单数据。

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

DataResubmissionHandler的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

## resend<sup>9+</sup>

resend(): void

重新发送表单数据。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**示例：**

ArkTS-Dyn示例：

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .onDataResubmitted((event) => {
            console.info('onDataResubmitted');
            event.handler.resend();
          })
      }
    }
  }
  ```

ArkTS-Sta示例：

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  import { Web, Column, Component, Entry, OnDataResubmittedEvent } from '@kit.ArkUI';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .onDataResubmitted((event: OnDataResubmittedEvent): void => {
            console.info('onDataResubmitted');
            event.handler.resend();
          })
      }
    }
  }
  ```

## cancel<sup>9+</sup>

cancel(): void

取消重新发送表单数据。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**示例：**

ArkTS-Dyn示例：

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .onDataResubmitted((event) => {
            console.info('onDataResubmitted');
            event.handler.cancel();
          })
      }
    }
  }
  ```

ArkTS-Sta示例：

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  import { Web, Column, Component, Entry, OnDataResubmittedEvent } from '@kit.ArkUI';
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .onDataResubmitted((event: OnDataResubmittedEvent): void => {
            console.info('onDataResubmitted');
            event.handler.cancel();
          })
      }
    }
  }
  ```

  ## 使用@ohos.transfer进行DataResubmissionHandler类型转换

ArkTS-Dyn中使用ArkTS-Sta的DataResubmissionHandler对象。

- 在ArkTS-Sta模块中将ArkTS-Sta DataResubmissionHandler转换成ArkTS-Dyn DataResubmissionHandler，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button, $rawfile, OnDataResubmittedEvent } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { dataResubmissionHandlerStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("Trigger onDataResubmitted")
          .onClick(() => {
            try {
              this.controller.loadUrl($rawfile('index.html'));
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Button('refresh')
          .onClick(() => {
            try {
              this.controller.refresh(); // 在网页中点击提交之后，点击refresh按钮可以重新提交时的触发函数。
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onDataResubmitted((event: OnDataResubmittedEvent): void => {
            console.info('onDataResubmitted invoked');
            try {
              let dynamicHandler = transfer.transferDynamic(event.handler, 'ArkWeb.DataResubmissionHandler');
              dataResubmissionHandlerStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
      }
    }
  }
  ```
  加载的index.html文件。
  ```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>dataSubmit</title>
    <style>
        body{
            background-color:gray;
        }
        .box {
            width: 200px;
            height: 150px;
            line-height: 150px;
            text-align: center;
            background-color: orange;
            position: absolute;
            top: 50%;
            left: 50%;
            margin-left: -100px;
            margin-top: -75px;
         }
         a{
            font-size:3em;
         }
    </style>
</head>
<body>
<form action="http://httpbin.org/post" method="post">
    <input type="text" name="username">
    <div class="box">
        <input id="submit" type="submit" name="提交">
    </div>
</form>
</body>
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn DataResubmissionHandler的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function dataResubmissionHandlerStaticToDynamic(handler_: any) {
    try {
      let handler: DataResubmissionHandler = handler_ as DataResubmissionHandler;
      handler.cancel();
      console.info('dataResubmissionHandlerStaticToDynamic done');
    } catch (e) {
      console.error('dataResubmissionHandlerStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的DataResubmissionHandler对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn DataResubmissionHandler对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { dataResubmissionHandlerDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("Trigger onDataResubmitted")
          .onClick(() => {
            try {
              this.controller.loadUrl($rawfile('index.html'));
            } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          })
        Button('refresh')
          .onClick(() => {
            try {
              this.controller.refresh(); // 在网页中点击提交之后，点击refresh按钮可以重新提交时的触发函数。
            } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onDataResubmitted((event: OnDataResubmittedEvent): void => {
            if (event) {
              console.info("onDataResubmitted start");
              dataResubmissionHandlerDynamicToStatic(event.handler);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn DataResubmissionHandler的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { DataResubmissionHandler } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function dataResubmissionHandlerDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: DataResubmissionHandler = transfer.transferStatic(dynObject, 'ArkWeb.DataResubmissionHandler') as DataResubmissionHandler;
        handler.cancel();
        console.info('dataResubmissionHandlerDynamicToStatic done');
    } catch (e: Error) {
        console.error('dataResubmissionHandlerDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```