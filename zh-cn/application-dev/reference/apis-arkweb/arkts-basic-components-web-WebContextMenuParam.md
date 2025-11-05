# Class (WebContextMenuParam)

实现长按页面元素或鼠标右键弹出来的菜单信息。示例代码参考[onContextMenuShow事件](./arkts-basic-components-web-events.md#oncontextmenushow9)。

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

WebContextMenuParam的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

## x<sup>9+</sup>

ArkTS-Dyn: x(): number

ArkTS-Sta: x(): int

弹出菜单的x坐标。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明                 |
| ------ | ------------------ |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 显示正常返回非负整数，否则返回-1。<br>单位：vp。 |

## y<sup>9+</sup>

ArkTS-Dyn: y(): number

ArkTS-Sta: y(): int

弹出菜单的y坐标。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明                 |
| ------ | ------------------ |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 显示正常返回非负整数，否则返回-1。<br>单位：vp。 |

## getLinkUrl<sup>9+</sup>

getLinkUrl(): string

获取链接地址。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明                        |
| ------ | ------------------------- |
| string | 如果长按位置是链接，返回经过安全检查的url链接。 |

## getUnfilteredLinkUrl<sup>9+</sup>

getUnfilteredLinkUrl(): string

获取链接地址。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明                    |
| ------ | --------------------- |
| string | 如果长按位置是链接，返回原始的url链接。 |

## getSourceUrl<sup>9+</sup>

getSourceUrl(): string

获取sourceUrl链接。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明                       |
| ------ | ------------------------ |
| string | 如果选中的元素有src属性，返回src的url。 |

## existsImageContents<sup>9+</sup>

existsImageContents(): boolean

是否存在图像内容。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型      | 说明                        |
| ------- | ------------------------- |
| boolean | 长按位置中有图片返回true，否则返回false。 |

## getMediaType<sup>9+</sup>

getMediaType(): ContextMenuMediaType

获取网页元素媒体类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                                       | 说明        |
| ---------------------------------------- | --------- |
| [ContextMenuMediaType](./arkts-basic-components-web-e.md#contextmenumediatype9) | 网页元素媒体类型。 |

## getSelectionText<sup>9+</sup>

getSelectionText(): string

获取选中文本。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明                   |
| ------ | -------------------- |
| string | 菜单上下文选中文本内容，不存在则返回空。 |

## getSourceType<sup>9+</sup>

getSourceType(): ContextMenuSourceType

获取菜单事件来源。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
| [ContextMenuSourceType](./arkts-basic-components-web-e.md#contextmenusourcetype9) | 菜单事件来源。 |

## getInputFieldType<sup>9+</sup>

getInputFieldType(): ContextMenuInputFieldType

获取网页元素输入框类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                                       | 说明     |
| ---------------------------------------- | ------ |
| [ContextMenuInputFieldType](./arkts-basic-components-web-e.md#contextmenuinputfieldtype9) | 输入框类型。 |

## isEditable<sup>9+</sup>

isEditable(): boolean

获取网页元素是否可编辑标识。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型      | 说明                         |
| ------- | -------------------------- |
| boolean | 网页元素可编辑返回true，不可编辑返回false。 |

## getEditStateFlags<sup>9+</sup>

ArkTS-Dyn: getEditStateFlags(): number

ArkTS-Sta: getEditStateFlags(): int

获取网页元素可编辑标识。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明                                       |
| ------ | ---------------------------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 网页元素可编辑标识，参照[ContextMenuEditStateFlags](./arkts-basic-components-web-e.md#contextmenueditstateflags9)。 |

## getPreviewWidth<sup>13+</sup>

ArkTS-Dyn: getPreviewWidth(): number

ArkTS-Sta: getPreviewWidth(): int

获取预览图的宽。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明       |
| ------ | ----------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 预览图的宽。<br>单位：vp。 |

## getPreviewHeight<sup>13+</sup>

ArkTS-Dyn: getPreviewHeight(): number

ArkTS-Sta: getPreviewHeight(): int

获取预览图的高。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型     | 说明       |
| ------ | ----------  |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 预览图的高。<br>单位：vp。 |

## 使用@ohos.transfer进行WebContextMenuParam类型转换

ArkTS-Dyn中使用ArkTS-Sta的WebContextMenuParam对象。

- 在ArkTS-Sta模块中将ArkTS-Sta WebContextMenuParam转换成ArkTS-Dyn WebContextMenuParam，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, OnContextMenuShowEvent, $rawfile } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { handleWebContextMenuParamDynamic } from 'library';

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
                let webContextMenuParamDynamic = transfer.transferDynamic(event.param, "ArkWeb.WebContextMenuParam") as Object;
                handleWebContextMenuParamDynamic(webContextMenuParamDynamic);
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

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebContextMenuParam的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function handleWebContextMenuParamDynamic(param_: any) {
    let param: WebContextMenuParam = param_ as WebContextMenuParam;
    console.info('x: ' + param.x());
    console.info('y: ' + param.y());
    console.info('LinkUrl: ' + param.getLinkUrl());
    console.info('SourceUrl: ' + param.getSourceUrl());
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的WebContextMenuParam对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn WebContextMenuParam对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { handleWebContextMenuParamStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onContextMenuShow((event: OnContextMenuShowEvent): boolean => {
            console.info('onContextMenuShow invoked');
            handleWebContextMenuParamStatic(event.param);
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

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebContextMenuParam的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { WebContextMenuParam } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function handleWebContextMenuParamStatic(dynObject: Object) {
    try {
        let param: WebContextMenuParam = transfer.transferStatic(dynObject, "ArkWeb.WebContextMenuParam") as WebContextMenuParam;
        console.info('x: ' + param.x());
        console.info('y: ' + param.y());
        console.info('LinkUrl: ' + param.getLinkUrl());
        console.info('SourceUrl: ' + param.getSourceUrl());
    } catch (e: Error) {
        console.error('transferStatic catch error：-----------' + e.message);
    }
  }
  ```
