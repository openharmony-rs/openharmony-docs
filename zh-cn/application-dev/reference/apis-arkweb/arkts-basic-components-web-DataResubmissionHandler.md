# Class (DataResubmissionHandler)

通过DataResubmissionHandler可以重新提交表单数据或取消提交表单数据。

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
            console.log('onDataResubmitted');
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
            console.log('onDataResubmitted');
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