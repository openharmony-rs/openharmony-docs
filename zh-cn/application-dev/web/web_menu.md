# 使用Web组件菜单处理网页内容
菜单作为用户交互的关键组件，其作用是构建清晰的导航体系，通过结构化布局展示功能入口，使用户能够迅速找到目标内容或执行操作。作为人机交互的重要枢纽，它显著提升了Web组件的可访问性和用户体验，是应用设计中必不可少的部分。Web组件菜单类型包括[文本选中菜单](./web_menu.md#文本选中菜单)、[上下文菜单](./web_menu.md#上下文菜单)和[自定义菜单](./web_menu.md#自定义菜单)，应用可根据具体需求灵活选择。
|菜单类型|目标元素|响应类型|是否支持自定义|
|----|----|----|----|
|[文本选中菜单](./web_menu.md#文本选中菜单)|文本|手势长按|可增减菜单项，菜单样式不可自定义|
|[上下文菜单](./web_menu.md#上下文菜单)|超链接、图片、文字|手势长按、鼠标右键|支持通过菜单组件自定义|
|[自定义菜单](./web_menu.md#自定义菜单)|图片|手势长按|支持通过菜单组件自定义|
## 文本选中菜单
Web组件的文本选中菜单是一种通过自定义元素实现的上下文交互组件，当用户选中文本时会动态显示，提供复制、分享、标注等语义化操作，具备标准化功能与可扩展性，是移动端文本操作的核心功能。文本选中菜单在用户长按选中文本或编辑状态下长按出现单手柄时弹出，菜单项横向排列。系统提供默认的菜单实现。应用可通过[editMenuOptions](../reference/apis-arkweb/ts-basic-components-web-attributes.md#editmenuoptions12)接口对文本选中菜单进行自定义操作。
1. 通过onCreateMenu方法自定义菜单项，通过操作Array<[TextMenuItem](../reference/apis-arkui/arkui-ts/ts-text-common.md#textmenuitem12对象说明)>数组可对显示菜单项进行增减操作，在[TextMenuItem](../reference/apis-arkui/arkui-ts/ts-text-common.md#textmenuitem12对象说明)中定义菜单项名称、图标、ID等内容。
2. 通过onMenuItemClick方法处理菜单项点击事件，当返回false时会执行系统默认逻辑。
3. 创建一个[EditMenuOptions](../reference/apis-arkui/arkui-ts/ts-text-common.md#editmenuoptions)对象，包含onCreateMenu和onMenuItemClick两个方法，通过Web组件的[editMenuOptions](../reference/apis-arkweb/ts-basic-components-web-attributes.md#editmenuoptions12)方法与Web组件绑定。

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem> {
      let items = menuItems.filter((menuItem) => {
        // 过滤用户需要的系统按键
        return (
          menuItem.id.equals(TextMenuItemId.CUT) ||
          menuItem.id.equals(TextMenuItemId.COPY) ||
          menuItem.id.equals(TextMenuItemId.PASTE)
        );
      });
      let customItem1: TextMenuItem = {
        content: 'customItem1',
        id: TextMenuItemId.of('customItem1'),
        icon: $r('app.media.startIcon')
      };
      let customItem2: TextMenuItem = {
        content: $r('app.string.EntryAbility_label'),
        id: TextMenuItemId.of('customItem2'),
        icon: $r('app.media.startIcon')
      };
      items.push(customItem1);// 在选项列表后添加新选项
      items.unshift(customItem2);// 在选项列表前添加选项
      items.push(customItem1);
      items.push(customItem1);
      items.push(customItem1);
      items.push(customItem1);
      items.push(customItem1);
      return items;
    }

    onMenuItemClick(menuItem: TextMenuItem, textRange: TextRange): boolean {
      if (menuItem.id.equals(TextMenuItemId.CUT)) {
        // 用户自定义行为
        console.log("拦截 id：CUT")
        return true; // 返回true不执行系统回调
      } else if (menuItem.id.equals(TextMenuItemId.COPY)) {
        // 用户自定义行为
        console.log("不拦截 id：COPY")
        return false; // 返回false执行系统回调
      } else if (menuItem.id.equals(TextMenuItemId.of('customItem1'))) {
        // 用户自定义行为
        console.log("拦截 id：customItem1")
        return true;// 用户自定义菜单选项返回true时点击后不关闭菜单，返回false时关闭菜单
      } else if (menuItem.id.equals(TextMenuItemId.of($r('app.string.EntryAbility_label')))){
        // 用户自定义行为
        console.log("拦截 id：app.string.customItem2")
        return true;
      }
      return false;// 返回默认值false
    }

    @State EditMenuOptions: EditMenuOptions = { onCreateMenu: this.onCreateMenu, onMenuItemClick: this.onMenuItemClick }

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .editMenuOptions(this.EditMenuOptions)
      }
    }
  }
  ```
  
  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
    <head>
        <title>测试网页</title>
    </head>
    <body>
      <h1>editMenuOptions Demo</h1>
      <span>edit menu options</span>
    </body>
  </html>
  ```
  ![editMenuOption](./figures/editMenuOption.gif)
## 上下文菜单
上下文菜单是用户通过特定操作（如右键点击或长按富文本）触发的快捷菜单，用于提供与当前操作对象或界面元素相关的功能选项。菜单项纵向排列。系统未提供默认实现，若应用未实现，则不显示上下文菜单。要应用需通过[Menu](../reference/apis-arkui/arkui-ts/ts-basic-components-menu.md)组件创建一个菜单子窗口并与Web绑定，通过菜单弹出时的[onContextMenuShow](../reference/apis-arkweb/ts-basic-components-web-events.md#oncontextmenushow9)接口获取上下文菜单的详细信息，包括点击位置的HTML元素信息及点击位置信息。

1. [Menu](../reference/apis-arkui/arkui-ts/ts-basic-components-menu.md)组件作为弹出的菜单，包含所有菜单项行为与样式。
2. 使用bindPopup方法将Menu组件与Web组件绑定。当上下文菜单弹出时，将显示创建的Menu组件。
3. 在onContextMenuShow回调中获取上下文菜单事件信息[onContextMenuShowEvent](../reference/apis-arkweb/ts-basic-components-web-i.md#oncontextmenushowevent12)。其中param为[WebContextMenuParam](../reference/apis-arkweb/ts-basic-components-web.md#webcontextmenuparam9)类型，包含点击位置对应HTML元素信息和位置信息，result为[WebContextMenuResult](../reference/apis-arkweb/ts-basic-components-web.md#webcontextmenuresult9)类型，提供常见的菜单能力。

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { pasteboard } from '@kit.BasicServicesKit';

const TAG = 'ContextMenu';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  private result: WebContextMenuResult | undefined = undefined;
  @State linkUrl: string = '';
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State showMenu: boolean = false;

  @Builder
  // 构建自定义菜单及触发功能接口
  MenuBuilder() {
    // 以垂直列表形式显示的菜单。
    Menu() {
      // 展示菜单Menu中具体的item菜单项。
      MenuItem({
        content: '复制图片',
      })
        .width(100)
        .height(50)
        .onClick(() => {
          this.result?.copyImage();
          this.showMenu = false;
        })
      MenuItem({
        content: '剪切',
      })
        .width(100)
        .height(50)
        .onClick(() => {
          this.result?.cut();
          this.showMenu = false;
        })
      MenuItem({
        content: '复制',
      })
        .width(100)
        .height(50)
        .onClick(() => {
          this.result?.copy();
          this.showMenu = false;
        })
      MenuItem({
        content: '粘贴',
      })
        .width(100)
        .height(50)
        .onClick(() => {
          this.result?.paste();
          this.showMenu = false;
        })
      MenuItem({
        content: '复制链接',
      })
        .width(100)
        .height(50)
        .onClick(() => {
          let pasteData = pasteboard.createData('text/plain', this.linkUrl);
          pasteboard.getSystemPasteboard().setData(pasteData, (error) => {
            if (error) {
              return;
            }
          })
          this.showMenu = false;
        })
      MenuItem({
        content: '全选',
      })
        .width(100)
        .height(50)
        .onClick(() => {
          this.result?.selectAll();
          this.showMenu = false;
        })
    }
    .width(150)
    .height(300)
  }

  build() {
    Column() {
      Web({ src: $rawfile("index.html"), controller: this.controller })
        // 触发自定义弹窗
        .onContextMenuShow((event) => {
          if (event) {
            this.result = event.result
            console.info("x coord = " + event.param.x());
            console.info("link url = " + event.param.getLinkUrl());
            this.linkUrl = event.param.getLinkUrl();
          }
          console.info(TAG, `x: ${this.offsetX}, y: ${this.offsetY}`);
          this.showMenu = true;
          this.offsetX = 0;
          this.offsetY = Math.max(px2vp(event?.param.y() ?? 0) - 0, 0);
          return true;
        })
        .bindPopup(this.showMenu,
          {
            builder: this.MenuBuilder(),
            enableArrow: false,
            placement: Placement.LeftTop,
            offset: { x: this.offsetX, y: this.offsetY },
            mask: false,
            onStateChange: (e) => {
              if (!e.isVisible) {
                this.showMenu = false;
                this.result!.closeContextMenu();
              }
            }
          })
    }
  }
}
```
```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<body>
  <h1>onContextMenuShow</h1>
  <a href="http://www.example.com" style="font-size:27px">超链接www.example.com</a>
  <div><img src="example.png"></div>
  <p>选中文字鼠标右键弹出菜单</p>
</body>
</html>
```
![onContextMenuShow](./figures/onContextMenuShow.gif)
## 自定义菜单
自定义菜单赋予开发者调整菜单触发时机与视觉展现的能力，使应用能够依据用户操作场景动态匹配功能入口，简化开发流程中的界面适配工作，同时使应用交互更符合用户直觉。自定义菜单允许应用通过[bindSelectionMenu](../reference/apis-arkweb/ts-basic-components-web-attributes.md#bindselectionmenu13)，根据事件类型与元素类型弹出自定义菜单，目前支持响应长按图片。
1. 创建[Menu](../reference/apis-arkui/arkui-ts/ts-basic-components-menu.md)组件作为菜单弹窗。
2. 通过Web组件的[bindSelectionMenu](../reference/apis-arkweb/ts-basic-components-web-attributes.md#bindselectionmenu13)方法绑定MenuBuilder菜单弹窗。将[WebElementType](../reference/apis-arkweb/ts-basic-components-web-e.md#webelementtype13)设置为WebElementType.IMAGE，[responseType](../reference/apis-arkweb/ts-basic-components-web-e.md#webresponsetype13)设置为WebResponseType.LONG_PRESS，表示长按图片时弹出菜单。在[options](../reference/apis-arkweb/ts-basic-components-web-i.md#selectionmenuoptionsext13)中定义菜单显示回调onAppear、菜单消失回调onDisappear、预览窗口preview和菜单类型menuType。
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

interface PreviewBuilderParam {
  previewImage: Resource | string | undefined;
  width: number;
  height: number;
}

@Builder function PreviewBuilderGlobal($$: PreviewBuilderParam) {
  Column() {
    Image($$.previewImage)
      .objectFit(ImageFit.Fill)
      .autoResize(true)
  }.width($$.width).height($$.height)
}

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  private result: WebContextMenuResult | undefined = undefined;
  @State previewImage: Resource | string | undefined = undefined;
  @State previewWidth: number = 0;
  @State previewHeight: number = 0;

  @Builder
  MenuBuilder() {
    Menu() {
      MenuItem({ content: '复制', })
        .onClick(() => {
          this.result?.copy();
          this.result?.closeContextMenu();
        })
      MenuItem({ content: '全选', })
        .onClick(() => {
          this.result?.selectAll();
          this.result?.closeContextMenu();
        })
    }
  }
  build() {
    Column() {
      Web({ src: $rawfile("index.html"), controller: this.controller })
        .bindSelectionMenu(WebElementType.IMAGE, this.MenuBuilder, WebResponseType.LONG_PRESS,
          {
            onAppear: () => {},
            onDisappear: () => {
              this.result?.closeContextMenu();
            },
            preview: PreviewBuilderGlobal({
              previewImage: this.previewImage,
              width: this.previewWidth,
              height: this.previewHeight
            }),
            menuType: MenuType.PREVIEW_MENU
          })
        .onContextMenuShow((event) => {
            if (event) {
              this.result = event.result;
              if (event.param.getLinkUrl()) {
                return false;
              }
              this.previewWidth = px2vp(event.param.getPreviewWidth());
              this.previewHeight = px2vp(event.param.getPreviewHeight());
              if (event.param.getSourceUrl().indexOf("resource://rawfile/") == 0) {
                this.previewImage = $rawfile(event.param.getSourceUrl().substr(19));
              } else {
                this.previewImage = event.param.getSourceUrl();
              }1
              return true;
            }
            return false;
          })
    }
  }
}
```
```html
<!--index.html-->
<!DOCTYPE html>
<html>
  <head>
      <title>测试网页</title>
  </head>
  <body>
    <h1>bindSelectionMenu Demo</h1>
    <img src="./img.png" >
  </body>
</html>
```
![bindSelectionMenu](./figures/bindSelectionMenu.gif)
## Web菜单保存图片
1. 创建MenuBuilder组件作为菜单弹窗，使用[SaveButton](../reference/apis-arkui/arkui-ts/ts-security-components-savebutton.md)组件实现图片保存，通过bindContextMenu将MenuBuilder与Web绑定。
2. 在onContextMenuShow中获取图片url，通过copyLocalPicToDir或copyUrlPicToDir将图片保存至应用沙箱。
3. 通过photoAccessHelper将应用沙箱中的图片保存至图库。

  ```ts
import { webview } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';
import { fileIo as fs, ReadOptions, WriteOptions } from '@kit.CoreFileKit';
import { systemDateTime } from '@kit.BasicServicesKit';
import { http } from '@kit.NetworkKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

const Tag = 'web-savePic';
const context = getContext(this) as common.UIAbilityContext;

function copyLocalPicToDir(rawfilePath: string, newFileName: string): string {
  let srcFileDes = context.resourceManager.getRawFdSync(rawfilePath)
  let dstPath = context.filesDir + "/" +newFileName
  let dest: fs.File = fs.openSync(dstPath, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE)
  let bufsize = 4096
  let buf = new ArrayBuffer(bufsize)
  let off = 0, len = 0, readedLen = 0
  while (len = fs.readSync(srcFileDes.fd, buf, { offset: srcFileDes.offset + off, length: bufsize })) {
    readedLen += len
    fs.writeSync(dest.fd, buf, { offset: off, length: len })
    off = off + len
    if ((srcFileDes.length - readedLen) < bufsize) {
      bufsize = srcFileDes.length - readedLen
    }
  }
  fs.close(dest.fd)
  return dest.path
}

async function copyUrlPicToDir(picUrl: string, newFileName: string): Promise<string> {
  let uri = ''
  let httpRequest = http.createHttp();
  let data: http.HttpResponse = await(httpRequest.request(picUrl) as Promise<http.HttpResponse>)
  if (data?.responseCode == http.ResponseCode.OK) {
    let dstPath = context.filesDir + "/" + newFileName;
    let dest: fs.File = fs.openSync(dstPath, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE)
    let writeLen: number = fs.writeSync(dest.fd, data.result as ArrayBuffer)
    uri = dest.path
  }
  return uri
}

@Entry
@Component
struct WebComponent {
  saveButtonOptions: SaveButtonOptions = {
    icon: SaveIconStyle.FULL_FILLED,
    text: SaveDescription.SAVE_IMAGE,
    buttonType: ButtonType.Capsule
  }
  controller: webview.WebviewController = new webview.WebviewController()
  private result: WebContextMenuResult | undefined = undefined
  @State showMenu: boolean = false
  @State imgUrl: string = ''

  @Builder
  MenuBuilder() {
    Column() {
      Row() {
        SaveButton(this.saveButtonOptions)
          .onClick(async (event, result: SaveButtonOnClickResult) => {
            if (result == SaveButtonOnClickResult.SUCCESS) {
              try {
                let context = getContext();
                let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
                let uri = '';
                if (this.imgUrl?.includes('rawfile')) {
                  let rawFileName: string = this.imgUrl.substring(this.imgUrl.lastIndexOf('/') + 1)
                  uri = copyLocalPicToDir(rawFileName, 'copyFile.png')
                } else if (this.imgUrl?.includes('http') || this.imgUrl?.includes('https')) {
                  uri = await copyUrlPicToDir(this.imgUrl, `onlinePic${systemDateTime.getTime()}.png`)
                }
                let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createImageAssetRequest(context, uri)
                await phAccessHelper.applyChanges(assetChangeRequest)
              }
              catch (err) {
                console.error(`create asset failed with error: ${err.code}, ${err.message}`)
              }
            } else {
              console.error(`SaveButtonOnClickResult create asset failed`)
            }
            this.showMenu = false
        })
      }
      .margin({ top: 20, bottom: 20 })
      .justifyContent(FlexAlign.Center)
    }
    .width('80')
    .backgroundColor(Color.White)
    .borderRadius(10)
  }

  build() {
    Column() {
      Web({src: $rawfile("index.html"), controller: this.controller})
        .onContextMenuShow((event) => {
          if (event) {
            let hitValue = this.controller.getHitTestValue()
            this.imgUrl = hitValue.extra
          }
          this.showMenu = true
          return true;
        })
        .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
        .fileAccess(true)
        .javaScriptAccess(true)
        .domStorageAccess(true)
    }
  }
}
  ```
  ```html
<!--index.html-->
<!DOCTYPE html>
<html>
<head>
    <title>SavePicture</title>
</head>
<body>
<h1>SavePicture</h1>
<br>
<br>
<br>
<br>
<br>
<img src="./startIcon.png">
</body>
</html>
  ```
![emptyEditMenuOption](./figures/web-menu-savePic.gif)

## Web菜单获取选中文本
Web组件的[editMenuOptions](../reference/apis-arkweb/ts-basic-components-web-attributes.md#editmenuoptions12)接口中没有提供获取选中文本的方式。开发者可通过[javaScriptProxy](../reference/apis-arkweb/ts-basic-components-web-attributes.md#javascriptproxy)获取到JavaScript的选中文本，实现自定义菜单的逻辑。
1. 创建SelectClass类，通过[javaScriptProxy](../reference/apis-arkweb/ts-basic-components-web-attributes.md#javascriptproxy)将SelectClass对象注册到Web组件中。
2. 在Html侧注册选区变更监听器，在选区变更时通过SelectClass对象将选区设置到ArkTS侧。
  ```ts
import { webview } from '@kit.ArkWeb';
let selectText = '';

class SelectClass {
  constructor() {
  }

  setSelectText(param: String) {
    selectText = param.toString();
  }
}

@Entry
@Component
struct WebComponent {
  webController: webview.WebviewController = new webview.WebviewController();
  @State selectObj: SelectClass = new SelectClass();
  @State textStr: string = '';

  build() {
    Column() {
      Web({ src: $rawfile('index.html'), controller: this.webController})
        .javaScriptProxy({
          object: this.selectObj,
          name: 'selectObjName',
          methodList: ['setSelectText'],
          controller: this.webController
        })
        .height('40%')
      Text('Click here to get the selected text.')
        .fontSize(20)
        .onClick(() => {
          this.textStr = selectText;
        })
        .height('10%')
      Text('Selected text is ' + this.textStr)
        .fontSize(20)
        .height('10%')
    }
  }
}
  ```
  ```html
<!DOCTYPE html>
<html>
<head>
    <title>Test Get Select</title>
    <style>
        body {
          margin: 40px;
          background-color: #f4f4f4;
        }
        .edit-container {
          padding: 20px;
          background-color: #fff;
          border-radius: 8px;
          box-shadow: 0 0 10px rgba(0,0,0,0.1);
          margin: auto;
        }
        textarea {
          width: 100%;
          height: 400px;
          font-size: 16px;
          padding: 10px;
          border: 1px solid #ccc;
          border-radius: 4px;
        }
    </style>
</head>
<body>
<div class="edit-container">
    <textarea placeholder="Enter the text here and select it by long pressing."></textarea>
</div>
<script>
    document.addEventListener('selectionchange', () => {
      var selection = window.getSelection();
      if(selection.rangeCount > 0) {
        var selectedText = selection.toString();
        selectObjName.setSelectText(selectedText);
      }
    })
</script>
</body>
</html>
  ```
![web-menu-get-select](./figures/web-menu-get-select.gif)

## Web菜单识别图片二维码
在二维码跳转页面或者付款场景中，开发者可通过实现上下文菜单，提供给用户扫描二维码入口，获取到[onContextMenuShow](../reference/apis-arkweb/ts-basic-components-web-events.md#oncontextmenushow9)接口中的二维码信息进行处理。
1. 创建MenuBuilder组件作为菜单弹窗，通过bindContextMenu将MenuBuilder与Web绑定。
2. 在onContextMenuShow中获取图片url，通过copyLocalPicToDir或copyUrlPicToDir将图片保存至应用沙箱。
3. 通过detectBarcode.decode描保存在沙箱中的图片，获取扫描到扫描结果。
  ```ts
import { webview } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { systemDateTime } from '@kit.BasicServicesKit';
import { http } from '@kit.NetworkKit';
import { scanCore, scanBarcode, detectBarcode } from '@kit.ScanKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  saveButtonOptions: SaveButtonOptions = {
    icon: SaveIconStyle.FULL_FILLED,
    text: SaveDescription.SAVE_IMAGE,
    buttonType: ButtonType.Capsule
  }
  controller: webview.WebviewController = new webview.WebviewController();
  private result: WebContextMenuResult | undefined = undefined;
  @State showMenu: boolean = false;
  @State imgUrl: string = '';
  @State decodeResult: string = '';
  context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  copyLocalPicToDir(rawfilePath: string, newFileName: string): string {
    let srcFileDes = this.context.resourceManager.getRawFdSync(rawfilePath);
    let dstPath = this.context.filesDir + "/" +newFileName;
    let dest: fs.File = fs.openSync(dstPath, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
    let bufsize = 4096;
    let buf = new ArrayBuffer(bufsize);
    let off = 0, len = 0, readedLen = 0;
    while (len = fs.readSync(srcFileDes.fd, buf, { offset: srcFileDes.offset + off, length: bufsize })) {
      readedLen += len;
      fs.writeSync(dest.fd, buf, { offset: off, length: len });
      off = off + len;
      if ((srcFileDes.length - readedLen) < bufsize) {
        bufsize = srcFileDes.length - readedLen;
      }
    }
    fs.close(dest.fd);
    return dest.path;
  }

  async copyUrlPicToDir(picUrl: string, newFileName: string): Promise<string> {
    let uri = '';
    let httpRequest = http.createHttp();
    let data: http.HttpResponse = await(httpRequest.request(picUrl) as Promise<http.HttpResponse>);
    if (data?.responseCode == http.ResponseCode.OK) {
      let dstPath = this.context.filesDir + "/" + newFileName;
      let dest: fs.File = fs.openSync(dstPath, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
      let writeLen: number = fs.writeSync(dest.fd, data.result as ArrayBuffer);
      uri = dest.path;
    }
    return uri;
  }

  @Builder
  MenuBuilder() {
    Menu() {
      MenuItem({
        content: "Scan QR Code",
      })
        .width(200)
        .height(50)
        .onClick(async () => {
          try {
            let uri = '';
            if (this.imgUrl?.includes('rawfile')) {
              let rawFileName: string = this.imgUrl.substring(this.imgUrl.lastIndexOf('/') + 1);
              uri = this.copyLocalPicToDir(rawFileName, 'copyFile.png');
            } else if (this.imgUrl?.includes('http') || this.imgUrl?.includes('https')) {
              uri = await this.copyUrlPicToDir(this.imgUrl, `onlinePic${systemDateTime.getTime()}.png`);
            }
            let options: scanBarcode.ScanOptions = { scanTypes: [scanCore.ScanType.ALL], enableMultiMode: true, enableAlbum: true }
            let inputImage: detectBarcode.InputImage = { uri: uri };
            try {
              // 调用图片识码接口
              detectBarcode.decode(inputImage, options, (error: BusinessError, result: Array<scanBarcode.ScanResult>) => {
                if (error && error.code) {
                  console.error(`create asset failed with error: ${error.code}, ${error.message}`);
                  return;
                }
              this.decodeResult = JSON.stringify(result);
              });
            } catch (err) {
              console.error(`Failed to detect Barcode. Code: ${err.code}, ${err.message}`);
            }
          }
          catch (err) {
            console.error(`create asset failed with error: ${err.code}, ${err.message}`);
          }
        })
    }
  }

  build() {
    Column() {
      Web({src: $rawfile("index.html"), controller: this.controller})
        .onContextMenuShow((event) => {
          if (event) {
            let hitValue = this.controller.getLastHitTest();
            this.imgUrl = hitValue.extra;
          }
          this.showMenu = true;
          return true;
        })
        .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
        .fileAccess(true)
        .javaScriptAccess(true)
        .domStorageAccess(true)
        .height('40%')
      Text('Decode result is ' + this.decodeResult)
        .fontSize(20)
        .height('10%')
    }
  }
}
  ```
  ```html
<!--index.html-->
<!DOCTYPE html>
<html>
<head>
    <title>test QR code</title>
</head>
<body>
<h1>Long press and click to scan the QR code</h1>
<!--img.png为二维码图片-->
<img src="img.png" >
</body>
</html>
  ```
![web-menu-scan-qr-code](./figures/web-menu-scan-qrcode.gif)

## 常见问题
### 如何禁用长按选择时弹出菜单
可通过[editMenuOptions](../reference/apis-arkweb/ts-basic-components-web-attributes.md#editmenuoptions12)接口将系统默认菜单全部过滤，此时无菜单项，则不会显示菜单。
  ```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem> {
    let items = menuItems.filter((menuItem) => {
      // 过滤用户需要的系统按键
      return false;
    });
    return items;
  }

  onMenuItemClick(menuItem: TextMenuItem, textRange: TextRange): boolean {
    return false;// 返回默认值false
  }

  @State EditMenuOptions: EditMenuOptions = { onCreateMenu: this.onCreateMenu, onMenuItemClick: this.onMenuItemClick }

  build() {
    Column() {
      Web({ src: $rawfile("index.html"), controller: this.controller })
        .editMenuOptions(this.EditMenuOptions)
    }
  }
}
  ```
  ```html
<!--index.html-->
<!DOCTYPE html>
<html>
  <head>
      <title>测试网页</title>
  </head>
  <body>
    <h1>editMenuOptions Demo</h1>
    <span>edit menu options</span>
  </body>
</html>
  ```
![emptyEditMenuOption](./figures/emptyEditMenuOption.gif)

### 出现选区时手柄菜单不显示
可排查是否通过JS的[selection-api](https://www.w3.org/TR/selection-api/)对选区进行了操作，目前通过这种方式改变选区会导致手柄菜单不显示。
### 如何修改文本选中菜单的样式
目前暂不支持修改文本选中菜单的具体样式。