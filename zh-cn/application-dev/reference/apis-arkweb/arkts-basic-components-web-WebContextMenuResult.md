# Class (WebContextMenuResult)

实现长按页面元素或鼠标右键弹出来的菜单所执行的响应事件。示例代码参考[onContextMenuShow事件](./arkts-basic-components-web-events.md#oncontextmenushow9)。

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

WebContextMenuResult的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## closeContextMenu<sup>9+</sup>

closeContextMenu(): void

不执行WebContextMenuResult其他接口操作时，需要调用此接口关闭菜单。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## copyImage<sup>9+</sup>

copyImage(): void

WebContextMenuParam有图片内容则复制图片。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## copy<sup>9+</sup>

copy(): void

执行与此上下文菜单相关的拷贝文本操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## paste<sup>9+</sup>

paste(): void

执行与此上下文菜单相关的粘贴操作。

> **说明：**
>
> 需要配置权限：ohos.permission.READ_PASTEBOARD。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## cut<sup>9+</sup>

cut(): void

执行与此上下文菜单相关的剪切操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## selectAll<sup>9+</sup>

selectAll(): void

执行与此上下文菜单相关的全选操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## undo<sup>20+</sup>

undo(): void

执行与此上下文菜单相关的撤销操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

## redo<sup>20+</sup>

redo(): void

执行与此上下文菜单相关的重做操作，即取消用户上一次的撤销操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

## pasteAndMatchStyle<sup>20+</sup>

pasteAndMatchStyle(): void

执行一个和上下文菜单相关的粘贴操作，粘贴的内容会匹配目标格式，以纯文本形式呈现。

> **说明：**
>
> 需要配置权限：ohos.permission.READ_PASTEBOARD。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

## requestPasswordAutoFill<sup>23+</sup>

requestPasswordAutoFill(): void

请求密码保险箱中的用户名或密码数据自动填充到当前获得焦点的输入框中。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

## 使用@ohos.transfer进行WebContextMenuResult类型转换

ArkTS-Dyn中使用ArkTS-Sta的WebContextMenuResult对象。

- 在ArkTS-Sta模块中将ArkTS-Sta WebContextMenuResult转换成ArkTS-Dyn WebContextMenuResult，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, OnContextMenuShowEvent, $rawfile } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { handleWebContextMenuResultDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onContextMenuShow((event: OnContextMenuShowEvent): boolean => {
            console.info('onContextMenuShow invoked');
            try {
                let webContextMenuResultDynamic = transfer.transferDynamic(event.result, "ArkWeb.WebContextMenuResult") as Object;
                handleWebContextMenuResultDynamic(webContextMenuResultDynamic);
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
  <!-- index.html -->
  <!DOCTYPE html>
  <html lang="en">
  <body>
    <h1>onContextMenuShow</h1>
    <a href="http://www.example.com" style="font-size:27px">链接www.example.com</a>
    // rawfile下放任意一张图片命名为example.png
    <div><img src="example.png"></div>
    <p>选中文字鼠标右键弹出菜单</p>
  </body>
  </html>
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebContextMenuResult的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function handleWebContextMenuResultDynamic(result_: any) {
    let result: WebContextMenuResult = result_ as WebContextMenuResult;
    result.copyImage();
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的WebContextMenuResult对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn WebContextMenuResult对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { handleWebContextMenuResultStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onContextMenuShow((event: OnContextMenuShowEvent): boolean => {
            console.info('onContextMenuShow invoked');
            handleWebContextMenuResultStatic(event.result);
            return false;
          })
      }
    }
  }
  ```
  加载的html文件。
  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html lang="en">
  <body>
    <h1>onContextMenuShow</h1>
    <a href="http://www.example.com" style="font-size:27px">链接www.example.com</a>
    // rawfile下放任意一张图片命名为example.png
    <div><img src="example.png"></div>
    <p>选中文字鼠标右键弹出菜单</p>
  </body>
  </html>
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebContextMenuResult的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { WebContextMenuResult } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function handleWebContextMenuResultStatic(dynObject: Object) {
    try {
        let result: WebContextMenuResult = transfer.transferStatic(dynObject, "ArkWeb.WebContextMenuResult") as WebContextMenuResult;
        result.copyImage();
    } catch (e: Error) {
        console.error('transferStatic catch error：-----------' + e.message);
    }
  }
  ```