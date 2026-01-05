# Class (FileSelectorResult)

通知Web组件的文件选择结果。示例代码参考[onShowFileSelector事件](./arkts-basic-components-web-events.md#onshowfileselector9)。

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

FileSelectorResult的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## handleFileList<sup>9+</sup>

handleFileList(fileList: Array\<string\>): void

通知Web组件进行文件选择操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型            | 必填  | 说明         |
| -------- | --------------- | ---- | ------------ |
| fileList | Array\<string\> | 是   | 需要进行操作的文件列表。 |

## 使用@ohos.transfer进行FileSelectorResult类型转换

ArkTS-Dyn中使用ArkTS-Sta的FileSelectorResult对象。

- 在ArkTS-Sta模块中将ArkTS-Sta FileSelectorResult转换成ArkTS-Dyn FileSelectorResult，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, OnShowFileSelectorEvent, $rawfile } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { handleFileSelectorResultDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onShowFileSelector((event: OnShowFileSelectorEvent): boolean => {
            console.info('MyFileUploader onShowFileSelector invoked');
            try {
                let fileSelectorResultDynamic = transfer.transferDynamic(event.result, "ArkWeb.FileSelectorResult") as Object;
                handleFileSelectorResultDynamic(fileSelectorResultDynamic);
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
    <form id="upload-form" enctype="multipart/form-data">
    <input type="file" id="upload" name="upload" accept="image/*, video/*"/>
    </form>
  </body>
  </html>
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn FileSelectorResult的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function handleFileSelectorResultDynamic(result_: any) {
    let result: FileSelectorResult = result_ as FileSelectorResult;
    result.handleFileList(new Array<string>("file:///data/storage/xxx/xxx.mp4"));
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的FileSelectorResult对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn FileSelectorResult对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { handleFileSelectorResultStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onShowFileSelector((event: OnShowFileSelectorEvent): boolean => {
            console.info('MyFileUploader onShowFileSelector invoked');
            handleFileSelectorResultStatic(event.result);
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
    <form id="upload-form" enctype="multipart/form-data">
    <input type="file" id="upload" name="upload" accept="image/*, video/*"/>
    </form>
  </body>
  </html>
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn FileSelectorResult的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { FileSelectorResult } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function handleFileSelectorResultStatic(dynObject: Object) {
    try {
        let result: FileSelectorResult = transfer.transferStatic(dynObject, "ArkWeb.FileSelectorResult") as FileSelectorResult;
        result.handleFileList(new Array<string>("file:///data/storage/xxx/xxx.mp4"));
    } catch (e: Error) {
        console.error('transferStatic catch error：-----------' + e.message);
    }
  }
  ```