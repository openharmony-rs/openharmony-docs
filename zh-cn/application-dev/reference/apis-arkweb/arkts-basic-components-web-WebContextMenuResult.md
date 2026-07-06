# Class (WebContextMenuResult)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

WebContextMenuResult是ArkWeb组件中用于处理上下文菜单（长按页面元素或鼠标右键弹出菜单）响应事件的类。它为开发者提供了一系列菜单操作的执行能力，包括文本编辑操作（复制、粘贴、剪切、全选、撤销、重做、粘贴并匹配样式）、图片操作（复制图片、保存图片）、菜单控制（关闭菜单）以及密码自动填充功能。

开发者通常在需要自定义Web组件上下文菜单行为时使用WebContextMenuResult。通过`onContextMenuShow`事件回调获取WebContextMenuResult实例，结合WebContextMenuParam提供的菜单上下文信息，判断用户操作场景并调用相应的响应方法，从而实现自定义菜单交互逻辑。若开发者不执行任何菜单响应操作，则必须调用`closeContextMenu`方法关闭菜单。

示例代码参考[onContextMenuShow<sup>9+</sup>](./arkts-basic-components-web-events.md#oncontextmenushow9)。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准。

## constructor<sup>9+</sup>

constructor()

WebContextMenuResult的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## closeContextMenu<sup>9+</sup>

closeContextMenu(): void

不执行WebContextMenuResult其他接口操作时，需要调用此接口关闭菜单。

**调用说明：**
- 调用WebContextMenuResult的其他方法（如copy、paste、cut等）完成操作后，应调用此方法关闭菜单。
- 如果不再需要执行其他菜单操作，也应及时调用此方法关闭菜单。
- 未调用此方法可能导致菜单资源未正确释放。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## copyImage<sup>9+</sup>

copyImage(): void

当WebContextMenuParam包含图片内容时，用于复制该图片，从API version 24开始支持对canvas图片进行复制。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## copy<sup>9+</sup>

copy(): void

执行复制文本操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## paste<sup>9+</sup>

paste(): void

执行粘贴操作。

> **说明：**
>
> 需要配置权限：[ohos.permission.READ_PASTEBOARD](../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard)。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## cut<sup>9+</sup>

cut(): void

执行剪切操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## selectAll<sup>9+</sup>

selectAll(): void

执行全选操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## undo<sup>20+</sup>

undo(): void

执行撤销操作，撤销上一次的用户操作。

**配合关系：**
- 与redo()方法配合使用，可以恢复被撤销的操作。
- 调用undo()后，可以通过redo()重新执行被撤销的操作。
- 如果用户未执行过撤销操作，则无法使用redo()方法。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

## redo<sup>20+</sup>

redo(): void

执行重做操作，即取消用户上一次的撤销操作。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

## pasteAndMatchStyle<sup>20+</sup>

pasteAndMatchStyle(): void

执行与此上下文菜单相关的粘贴操作，粘贴的内容会匹配目标位置的样式格式。

> **说明：**
>
> 需要配置权限：[ohos.permission.READ_PASTEBOARD](../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard)。

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

## saveImage<sup>24+</sup>

saveImage(): void

保存上下文菜单相关的图片，调用后将触发下载流程。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core