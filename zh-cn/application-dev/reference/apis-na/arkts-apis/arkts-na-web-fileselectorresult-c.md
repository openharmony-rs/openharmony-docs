# FileSelectorResult

Defines the file selector result, related to [onFileSelectorShow](../../apis-arkweb/arkts-components/arkts-arkweb-web-attribute.md#onfileselectorshow) method.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class FileSelectorResult--><!--Device-unnamed-export declare class FileSelectorResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-FileSelectorResult-constructor()--><!--Device-FileSelectorResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleFileList

```TypeScript
handleFileList(fileList: Array<string>): void
```

select a list of files.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-FileSelectorResult-handleFileList(fileList: Array<string>): void--><!--Device-FileSelectorResult-handleFileList(fileList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileList | Array&lt;string&gt; | 是 | List of files that need to be operated. |

