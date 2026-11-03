# Printing Frontend Pages
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=2ad5fc6234f7f269bb6601ed8aa7fb97b91184d8 translatedAt=2026-11-03T03:11:11.535Z pushedAt=2026-11-03T03:24:38.553Z nl=1 -->

The **Web** component can print HTML pages in two ways: through the W3C standard protocol API and through the app-side API.

Before using the print capability, declare related permissions in the **module.json5** file. For details, see [Declaring Permissions in the Configuration File](../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

  ```json
  "requestPermissions":[
      {
        "name" : "ohos.permission.PRINT"
      }
    ]
  ```

## Initiating a Print Task Through the W3C Standards-compliant API
A print adapter is created to start the print app and render the current web page content. The PDF file information generated after rendering is passed to the print framework through a file descriptor (fd). The W3C standard protocol API `window.print()` is used to print the current page or pop up a print dialog box. This method takes no parameters and only needs to be called in JavaScript.

You can use frontend CSS styles to control whether to print, for example, **@media print**. Then load the HTML page in the **Web** component.

- Sample code of the **print.html** page:

  Example 1:

  <!-- @[w3c_print_html_html](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ProcessWebPageCont/entry/src/main/resources/rawfile/print.html) -->
  
  ``` HTML
  <!DOCTYPE html>
  <html>
  
  <head>
      <meta charset='utf-8'>
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
          <center>This is a test page for printing</center>
      </b>
          <hr color=#00cc00 width=95%>
      </h1>
      <button class='Button Button--outline' onclick='window.print();'>Print</button>
      <p> content content content </p>
      <div id='printableTable'>
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
  
  Example 2 (nesting a page in an iframe):

  <!-- @[w3c_print_html_iframe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ProcessWebPageCont/entry/src/main/resources/rawfile/iframe.html) --> 
  
  ``` HTML
  <!DOCTYPE html>
    <html lang='en'>
    <head>
        <meta charset='UTF-8'>
        <meta name='viewport' content='width=device-width, initial-scale=1.0'>
        <title>iframe Nested Page Printing</title>
    </head>
    <body>
        <button id='printIframe'>Print iframe nested page</button>
        <iframe id='contentIframe' hidden></iframe>
  
        <script>
            document.getElementById('printIframe').addEventListener('click', () => {
                var ctIframe = document.getElementById('contentIframe');
                if (!ctIframe.contentWindow || !ctIframe.contentWindow.document) {
                  console.error('iframe page initialization failed');
                  return;
                }
                var ctIframeDoc = ctIframe.contentWindow.document;
                ctIframeDoc.write('Nested page');
                ctIframeDoc.close();
                ctIframe.contentWindow.print();
            });
        </script>
    </body>
    </html>
  ```

- Application code:

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
    }
  }
  ```

## Initiating a Print Task Through the Application API
On the application side, call [createWebPrintDocumentAdapter](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#createwebprintdocumentadapter11) to create a print adapter and pass the adapter to the **print** API to initiate printing.
<!-- @[create_web_print_document](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ProcessWebPageCont/entry/src/main/ets/pages/InitiatePrintAppAPI.ets) -->

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
            let webPrintDocAdapter = this.controller.createWebPrintDocumentAdapter('example.pdf');
            print.print('example_job_id', webPrintDocAdapter, null, this.getUIContext().getHostContext());
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller });
    }
  }
}
```
