# 使用Web组件打印前端页面
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

Web组件打印HTML页面时可通过W3C标准协议接口和应用接口两种方式实现。

使用打印功能前，请在module.json5中配置相关权限，添加方法请参考[在配置文件中声明权限](../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

  ```json
  "requestPermissions":[
      {
        "name" : "ohos.permission.PRINT"
      }
    ]
  ```

## 使用W3C标准协议接口拉起打印
通过创建打印适配器，拉起打印应用，并对当前Web页面内容进行渲染，渲染后生成的PDF文件信息通过文件描述符（fd）传递给打印框架。W3C标准协议接口window.print()方法用于打印当前页面或弹出打印对话框。该方法没有任何参数，只需要在JavaScript中调用即可。

可通过前端CSS样式控制是否打印，例如@media print。再通过Web加载该HTML页面的方式运行。

- print.html页面代码。

  示例一：

  ```html
  <!DOCTYPE html>
  <html>

  <head>
      <meta charset="utf-8">
      <title>printTest</title>
      <style>
          @media print {
              h1 {
                  display: none;
              }
          }
      </style>
  </head>

  <body>
      <div>
          <h1><b>
                  <p style="text-align: center;">This is a test page for printing</p>
              </b>
              <hr color="#00cc00" width="95%">
          </h1>
          <button class="Button Button--outline" onclick="window.print();">Print</button>
          <p> content content content </p>
          <div id="printableTable">
              <table>
                  <thead>
                      <tr>
                          <td>Thing</td>
                          <td>Chairs</td>
                      </tr>
                  </thead>
                  <tbody>
                      <tr>
                          <td>1</td>
                          <td>blue</td>
                      </tr>
                      <tr>
                          <td>2</td>
                          <td>green</td>
                      </tr>
                  </tbody>
              </table>
          </div>
          <p> content content content </p>
          <p> content content content </p>
      </div>
  </body>
  ```
  
  示例二（iframe嵌套页面的方式）：


  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>iframe嵌套页面打印</title>
  </head>
  <body>
      <button id="printIframe">打印iframe嵌套页面</button>
      <iframe id="contentIframe" hidden></iframe>

      <script>
          document.getElementById("printIframe").addEventListener("click", () => {
              var ctIframe = document.getElementById("contentIframe");
              if(!ctIframe.contentWindow || !ctIframe.contentWindow.document) {
                console.error("iframe页面初始化失败");
                return;
              }
              var ctIframeDoc = ctIframe.contentWindow.document;
              ctIframeDoc.write("嵌套页面");
              ctIframeDoc.close();
              ctIframe.contentWindow.print();
          });
      </script>
  </body>
  </html>
  ```

- 应用侧代码。

  <!-- @[w3c_print_html](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ProcessWebPageCont/entry/src/main/ets/pages/InitiatePrintW3CAPI.ets) -->

ArkTS-Dyn示例：  
  ``` TypeScript
  import { webview } from '@kit.ArkWeb';
  
  @Entry
  @Component
  struct Index {
    controller: webview.WebviewController = new webview.WebviewController();
  
    build() {
      Row() {
        Column() {
          Web({ src: $rawfile('print.html'), controller: this.controller })
            .javaScriptAccess(true)
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

ArkTS-Sta示例：
``` TypeScript
// xxx.ets
'use static'
import { $rawfile, Entry, Row, Column, Component, Web } from '@kit.ArkUI';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController(undefined);

  build() {
    Row() {
      Column() {
        Web({ src: $rawfile('print.html'), controller: this.controller })
          .javaScriptAccess(true)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## 通过调用应用侧接口拉起打印
应用侧通过调用[createWebPrintDocumentAdapter](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#createwebprintdocumentadapter11)创建打印适配器，通过将适配器传入打印的print接口调起打印。
<!-- @[create_web_print_document](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ProcessWebPageCont/entry/src/main/ets/pages/InitiatePrintAppAPI.ets) -->

ArkTS-Dyn示例：
``` TypeScript
import { webview } from '@kit.ArkWeb';
import { BusinessError, print } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('createWebPrintDocumentAdapter')
        .onClick(() => {
          try {
            let webPrintDocadapter = this.controller.createWebPrintDocumentAdapter('example.pdf');
            print.print('example_job_id', webPrintDocadapter, null, this.getUIContext().getHostContext());
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller });
    }
  }
}
```

ArkTS-Sta示例：
``` TypeScript
// xxx.ets
'use static'
import print from '@ohos.print';
import { Entry, Column, Component, Button, Web } from '@kit.ArkUI';
import { webview } from '@kit.ArkWeb';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

const myPrintAttributes: print.PrintAttributes = {
  copyNumber: 1 as int,
  pageRange: {
    startPage: 1 as int,
    endPage: 1 as int,
    pages: [1] as Array<int>
  },
  pageSize: {
    id: 'PAGE_ISO_A4',
    name: 'A4',
    width: 210 as int,
    height: 297 as int
  },
  directionMode: print.PrintDirectionMode.DIRECTION_MODE_PORTRAIT,
  colorMode: print.PrintColorMode.COLOR_MODE_COLOR,
  duplexMode: print.PrintDuplexMode.DUPLEX_MODE_NONE,
}

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);

  build() {
    Column() {
      Button('createWebPrintDocumentAdapter')
        .onClick(() => {
          try {
            let webPrintDocadapter = this.controller.createWebPrintDocumentAdapter('example.pdf');
            print.print('example_jobid', webPrintDocadapter, myPrintAttributes, this.getUIContext().getHostContext() as common.UIAbilityContext);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```
