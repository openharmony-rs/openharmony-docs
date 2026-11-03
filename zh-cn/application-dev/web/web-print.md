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
  
  
  示例二（iframe嵌套页面的方式）：
  
  ``` HTML
  <!DOCTYPE html>
    <html lang='en'>
    <head>
        <meta charset='UTF-8'>
        <meta name='viewport' content='width=device-width, initial-scale=1.0'>
        <title>iframe嵌套页面打印</title>
    </head>
    <body>
        <button id='printIframe'>打印iframe嵌套页面</button>
        <iframe id='contentIframe' hidden></iframe>
  
        <script>
            document.getElementById('printIframe').addEventListener('click', () => {
                var ctIframe = document.getElementById('contentIframe');
                if (!ctIframe.contentWindow || !ctIframe.contentWindow.document) {
                  console.error('iframe页面初始化失败');
                  return;
                }
                var ctIframeDoc = ctIframe.contentWindow.document;
                ctIframeDoc.write('嵌套页面');
                ctIframeDoc.close();
                ctIframe.contentWindow.print();
            });
        </script>
    </body>
    </html>
  ```

- 应用侧代码。

  <!-- @[w3c_print_html](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ProcessWebPageCont/entry/src/main/ets/pages/InitiatePrintW3CAPI.ets) -->
  
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
      Web({ src: 'www.example.com', controller: this.controller });
    }
  }
}
```