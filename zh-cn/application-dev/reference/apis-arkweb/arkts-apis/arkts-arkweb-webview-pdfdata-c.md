# PdfData

PdfData是Web组件用于封装网页生成的PDF数据流的类。当应用需要将Web组件加载的网页内容以PDF格式保存时，通过[WebviewController](arkts-arkweb-webview-webviewcontroller-c.md)的 [createPdf](arkts-arkweb-webview-webviewcontroller-c.md#createpdf) 方法将网页内容转换为PDF数据流，该方法在回调或Promise中以PdfData对象返回。应用再通过PdfData的pdfArrayBuffer方法获取Uint8Array格式的数据流，结合文件IO接口将数据写入本地PDF文件。PdfData适用于需要离线保存网页内容、生成网页PDF报告等场景。使用时需先加载Web组件并确保网页内容已渲染完成，再调用createPdf生成PDF数据流。

> **说明：**
> 
> - 在网页生成PDF过程中，返回的是数据流，由PdfData类封装。

**起始版本：** 14

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## pdfArrayBuffer

```TypeScript
pdfArrayBuffer(): Uint8Array
```

获取网页生成的PDF数据流。完整示例代码参考 [createPdf](arkts-arkweb-webview-webviewcontroller-c.md#createpdf) 。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 网页生成的PDF数据流，可结合文件IO接口将数据写入本地PDF文件。 |
