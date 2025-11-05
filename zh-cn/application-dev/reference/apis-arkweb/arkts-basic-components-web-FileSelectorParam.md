# Class (FileSelectorParam)

Web组件获取文件对象。示例代码参考[onShowFileSelector事件](./arkts-basic-components-web-events.md#onshowfileselector9)。

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

FileSelectorParam的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

## getTitle<sup>9+</sup>

getTitle(): string

获取文件选择器标题。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明         |
| ------ | ---------- |
| string | 返回文件选择器标题。 |

## getMode<sup>9+</sup>

getMode(): FileSelectorMode

获取文件选择器的模式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                                       | 说明          |
| ---------------------------------------- | ----------- |
| [FileSelectorMode](./arkts-basic-components-web-e.md#fileselectormode9) | 返回文件选择器的模式。 |

## getAcceptType<sup>9+</sup>

getAcceptType(): Array\<string\>

获取文件过滤类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型              | 说明        |
| --------------- | --------- |
| Array\<string\> | 返回文件过滤类型。 |

## isCapture<sup>9+</sup>

isCapture(): boolean

获取是否调用多媒体能力。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型      | 说明           |
| ------- | ------------ |
| boolean | 返回是否调用多媒体能力。<br>true表示返回调用多媒体能力，false表示返回未调用多媒体能力。 |

## getMimeTypes<sup>18+</sup>

getMimeTypes(): Array\<string\>

获取文件MIME类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型              | 说明        |
| --------------- | --------- |
| Array\<string\> | 返回文件MIME类型。 |

## 使用@ohos.transfer进行FileSelectorParam类型转换

ArkTS-Dyn中使用ArkTS-Sta的FileSelectorParam对象。

- 在ArkTS-Sta模块中将ArkTS-Sta FileSelectorParam转换成ArkTS-Dyn FileSelectorParam，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, OnShowFileSelectorEvent, $rawfile } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { handleFileSelectorParamDynamic } from 'library';

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
                let fileSelectorParamDynamic = transfer.transferDynamic(event.fileSelector, "ArkWeb.FileSelectorParam") as Object;
                handleFileSelectorParamDynamic(fileSelectorParamDynamic);
            } catch (e: Error) {
                console.error('transferDynamic catch error：-----------' + e.message);
            }
            return false;
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

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn FileSelectorParam的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function handleFileSelectorParamDynamic(param_: any) {
    let param: FileSelectorParam = param_ as FileSelectorParam;
    console.info('title: ' + param.getTitle());
    console.info('mode: ' + param.getMode());
    console.info('isCapture: ' + param.isCapture());
    console.info('AcceptType: ' + param.getAcceptType());
    console.info('MimeTypes: ' + param.getMimeTypes());
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的FileSelectorParam对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn FileSelectorParam对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { handleFileSelectorParamStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onShowFileSelector((event: OnShowFileSelectorEvent): boolean => {
            console.info('MyFileUploader onShowFileSelector invoked');
            handleFileSelectorParamStatic(event.fileSelector);
            return false;
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

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn FileSelectorParam的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { FileSelectorParam } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function handleFileSelectorParamStatic(dynObject: Object) {
    try {
        let param: FileSelectorParam = transfer.transferStatic(dynObject, "ArkWeb.FileSelectorParam") as FileSelectorParam;
        console.info('title: ' + param.getTitle());
        console.info('mode: ' + param.getMode());
        console.info('isCapture: ' + param.isCapture());
        console.info('AcceptType: ' + param.getAcceptType());
        console.info('MimeTypes: ' + param.getMimeTypes());
    } catch (e: Error) {
        console.error('transferStatic catch error：-----------' + e.message);
    }
  }
  ```