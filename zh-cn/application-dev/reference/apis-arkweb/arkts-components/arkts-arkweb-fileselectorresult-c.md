# FileSelectorResult

定义文件选择器结果，与 {@link onFileSelectorShow} 方法相关联。

**起始版本：** 9

<!--Device-unnamed-declare class FileSelectorResult--><!--Device-unnamed-declare class FileSelectorResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

FileSelectorResult的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorResult-constructor()--><!--Device-FileSelectorResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="handlefilelist"></a>
## handleFileList

```TypeScript
handleFileList(fileList: Array<string>): void
```

选择文件列表。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorResult-handleFileList(fileList: Array<string>): void--><!--Device-FileSelectorResult-handleFileList(fileList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileList | Array&lt;string&gt; | 是 | List of files that need to be operated. |

