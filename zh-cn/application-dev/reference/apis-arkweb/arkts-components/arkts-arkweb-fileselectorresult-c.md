# FileSelectorResult

定义文件选择器结果，与 {@link onFileSelectorShow} 方法相关联。

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

FileSelectorResult的构造函数。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## handleFileList

```TypeScript
handleFileList(fileList: Array<string>): void
```

选择文件列表。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileList | Array&lt;string&gt; | 是 | List of files that need to be operated. |

