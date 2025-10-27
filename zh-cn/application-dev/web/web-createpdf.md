# 使用Web组件保存前端页面为PDF
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

从API version 14开始，支持使用Web组件的[createPdf](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#createpdf14)方法，为应用提供了保存前端页面为PDF的功能。

通过[createPdf](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#createpdf14)生成实例后，调用`pdfArrayBuffer`方法获取二进制数据流，再使用`fileIo`方法将二进制数据流保存为PDF文件。用户可以将前端页面内容保存为PDF以便分享或保存。例如，生成报告、发票等，方便用户保存和传输。

## 需要权限
若涉及网络文档获取，需在module.json5中配置网络访问权限。具体添加方法请参考[在配置文件中声明权限](../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

<!-- @[web_createpdf_permissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ArkWebCreatePdf/entry/src/main/module.json5) -->

## callback方式保存PDF
通过callback方式调用`createPdf`接口，获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件。

<!-- @[web_createpdf_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ArkWebCreatePdf/entry/src/main/ets/pages/WebCreatePdfCallback.ets) -->


## Promise方式保存PDF
通过Promise方式调用`createPdf`接口，获取到的result通过`pdfArrayBuffer`接口取得PDF二进制数据流，最后使用`fileIo`方法将二进制数据流保存为PDF文件。

<!-- @[web_createpdf_promise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ArkWebCreatePdf/entry/src/main/ets/pages/WebCreatePdfPromise.ets) -->
