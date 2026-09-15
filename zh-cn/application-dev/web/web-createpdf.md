# 使用Web组件保存前端页面为PDF
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

从API version 14开始，支持使用Web组件的[createPdf](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#createpdf14)方法，为应用提供了保存前端页面为PDF的功能。

使用[createPdf](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#createpdf14)生成实例后，调用`pdfArrayBuffer`方法获取二进制数据流，再使用基础文件IO接口（[ohos.file.fs](../reference/apis-core-file-kit/js-apis-file-fs.md)）将二进制数据流保存为PDF文件。用户可以将前端页面内容保存为PDF以便分享或保存。例如，生成报告、发票等，方便用户保存和传输。
> **说明**
>
> 通过[pdfConfiguration](../reference/apis-arkweb/arkts-apis-webview-i.md#pdfconfiguration14)的配置，可调整PDF每页大小、前端页面缩放比例等；推荐使用前端页面适配策略，通过CSS媒体查询（@media print）优化PDF排版。

## 需要权限
若涉及网络文档获取，需在module.json5中配置网络访问权限。具体添加方法请参考[在配置文件中声明权限](../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

<!-- @[web_createpdf_permissions](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb/ArkWebCreatePdf/entry/src/main/module.json5) -->

``` JSON5
"requestPermissions": [
  {
    "name": "ohos.permission.INTERNET"
  }
],
```

## callback方式保存PDF
通过callback方式调用`createPdf`接口，获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件。

ArkTS-Dyn示例：
<!-- @[web_createpdf_callback](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb/ArkWebCreatePdf/entry/src/main/ets/pages/WebCreatePdfCallback.ets) -->

``` TypeScript
import { fileIo as fs } from '@kit.CoreFileKit';
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController();
  pdfConfig: webview.PdfConfiguration = {
    width: 8.27,
    height: 11.69,
    marginTop: 0,
    marginBottom: 0,
    marginRight: 0,
    marginLeft: 0,
    shouldPrintBackground: true
  };

  build() {
    Column() {
      Button('SavePDF')
        .onClick(() => {
          // 触发PDF生成，需要确保页面渲染完成，可使用onPageEnd事件监听
          this.controller.createPdf(
            this.pdfConfig,
            (error, result: webview.PdfData) => {
              try {
                // 获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件
                let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let filePath = context.filesDir + '/test.pdf';
                let file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
                fs.write(file.fd, result.pdfArrayBuffer().buffer).then((writeLen: number) => {
                  console.info('createPDF write data to file succeed and size is:' + writeLen);
                }).catch((err: BusinessError) => {
                  console.error('createPDF write data to file failed with error message: ' + err.message +
                      ', error code: ' + err.code);
                }).finally(() => {
                  // 关闭file
                  fs.closeSync(file);
                });
              } catch (resError) {
                console.error(
                  `ErrorCode: ${(resError as BusinessError).code},  Message: ${resError as BusinessError).message}`);
              }
            });
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

ArkTS-Sta示例：
<!-- @[web_createpdf_callback](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/CreatePdf/entry/src/main/ets/pages/WebCreatePdfCallback.ets) -->

``` TypeScript
// xxx.ets
'use static'
import fileIo from '@ohos.file.fs';
import { Entry, Column, Component, Button, Web } from '@kit.ArkUI';
import { webview } from '@kit.ArkWeb';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  pdfConfig: webview.PdfConfiguration = {
    width: 8.27,
    height: 11.69,
    marginTop: 0,
    marginBottom: 0,
    marginRight: 0,
    marginLeft: 0,
    shouldPrintBackground: true
  } as webview.PdfConfiguration

  build() {
    Column() {
      Button('SavePDF')
        .onClick(() => {
          // 触发PDF生成，需要确保页面渲染完成，可使用onPageEnd事件监听
          this.controller.createPdf(
            this.pdfConfig,
            (error, result: webview.PdfData | undefined) => {
              try {
                // 获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件
                let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let filePath = context.filesDir + "/test.pdf";
                let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
                let arrayBuffer: Uint8Array = result?.pdfArrayBuffer() as Uint8Array;
                fileIo.write(file.fd, arrayBuffer.buffer).then((writeLen: long) => {
                  console.info("createPDF write data to file succeed and size is:" + writeLen);
                }).catch((err: Error) => {
                  console.error("createPDF write data to file failed with error message: " + err.message +
                    ", error code: " + err.code);
                }).finally(() => {
                  // 关闭file
                  fileIo.closeSync(file);
                });
              } catch (resError) {
                console.error(`ErrorCode: ${(resError as BusinessError).code},  Message: ${(resError as BusinessError).message}`);
              }
            });
        })
      Web({ src: "www.example.com", controller: this.controller })
    }
  }
}
```

## Promise方式保存PDF
通过Promise方式调用`createPdf`接口，获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件。

ArkTS-Dyn示例：
<!-- @[web_createpdf_promise](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb/ArkWebCreatePdf/entry/src/main/ets/pages/WebCreatePdfPromise.ets) --> 

``` TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController();
  pdfConfig: webview.PdfConfiguration = {
    width: 8.27,
    height: 11.69,
    marginTop: 0,
    marginBottom: 0,
    marginRight: 0,
    marginLeft: 0,
    shouldPrintBackground: true
  };

  build() {
    Column() {
      Button('SavePDF')
        .onClick(() => {
          // 触发PDF生成，需要确保页面渲染完成，可使用onPageEnd事件监听
          this.controller.createPdf(this.pdfConfig)
            .then((result: webview.PdfData) => {
              try {
                // 获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件
                let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let filePath = context.filesDir + '/test.pdf';
                let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
                fileIo.write(file.fd, result.pdfArrayBuffer().buffer).then((writeLen: number) => {
                  console.info('createPDF write data to file succeed and size is:' + writeLen);
                }).catch((err: BusinessError) => {
                  console.error('createPDF write data to file failed with error message: ' + err.message +
                      ', error code: ' + err.code);
                }).finally(() => {
                  // 关闭file
                  fileIo.closeSync(file);
                });
              } catch (resError) {
                console.error(
                  `ErrorCode: ${(resError as BusinessError).code},  Message: ${(resError as BusinessError).message}`);
              }
            })
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

ArkTS-Sta示例：
<!-- @[web_createpdf_promise](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/CreatePdf/entry/src/main/ets/pages/WebCreatePdfPromise.ets) --> 

``` TypeScript
import fileIo from '@ohos.file.fs';
import { Entry, Column, Component, Button, Web } from '@kit.ArkUI';
import { webview } from '@kit.ArkWeb';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  pdfConfig: webview.PdfConfiguration = {
    width: 8.27,
    height: 11.69,
    marginTop: 0,
    marginBottom: 0,
    marginRight: 0,
    marginLeft: 0,
    shouldPrintBackground: true
  } as webview.PdfConfiguration

  build() {
    Column() {
      Button('SavePDF')
        .onClick(() => {
          // 触发PDF生成，需要确保页面渲染完成，可使用onPageEnd事件监听
          this.controller.createPdf(this.pdfConfig)
            .then((result: webview.PdfData) => {
              try {
                // 获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件
                let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let filePath = context.filesDir + "/test.pdf";
                let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
                fileIo.write(file.fd, result.pdfArrayBuffer().buffer).then((writeLen: long) => {
                  console.info("createPDF write data to file succeed and size is:" + writeLen);
                }).catch((err: Error) => {
                  console.error("createPDF write data to file failed with error message: " + err.message +
                    ", error code: " + err.code);
                }).finally(() => {
                  // 关闭file
                  fileIo.closeSync(file);
                });
              } catch (resError) {
                console.error(`ErrorCode: ${(resError as BusinessError).code},  Message: ${(resError as BusinessError).message}`);
              }
            })
        })
      Web({ src: "www.example.com", controller: this.controller })
    }
  }
}
```

