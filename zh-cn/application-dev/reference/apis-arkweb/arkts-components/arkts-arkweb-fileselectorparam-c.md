# FileSelectorParam

封装消息信息，作为 {@link onFileSelectorShow} 方法的入参。

**起始版本：** 9

<!--Device-unnamed-declare class FileSelectorParam--><!--Device-unnamed-declare class FileSelectorParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

FileSelectorParam的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-constructor()--><!--Device-FileSelectorParam-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getAcceptType

```TypeScript
getAcceptType(): Array<string>
```

获取可接受的MIME类型数组。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-getAcceptType(): Array<string>--><!--Device-FileSelectorParam-getAcceptType(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | Return an array of acceptable MIME type. |

## getAcceptableFileTypes

```TypeScript
getAcceptableFileTypes(): Array<Array<AcceptableFileType>>
```

获取网页文件的已选类型数组。

**起始版本：** 23

<!--Device-FileSelectorParam-getAcceptableFileTypes(): Array<Array<AcceptableFileType>>--><!--Device-FileSelectorParam-getAcceptableFileTypes(): Array<Array<AcceptableFileType>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Array&lt;AcceptableFileType&gt;&gt; | Return an array of selected types for web page files. |

## getDefaultPath

```TypeScript
getDefaultPath(): string
```

获取拉起选择器时默认打开的路径。

**起始版本：** 23

<!--Device-FileSelectorParam-getDefaultPath(): string--><!--Device-FileSelectorParam-getDefaultPath(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return to the default path opened when pulling up the selector. |

## getDescriptions

```TypeScript
getDescriptions(): Array<string>
```

获取文件类型的描述信息数组。

**起始版本：** 23

<!--Device-FileSelectorParam-getDescriptions(): Array<string>--><!--Device-FileSelectorParam-getDescriptions(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | Return an array of description of the file type. |

## getMimeTypes

```TypeScript
getMimeTypes(): Array<string>
```

获取原始可接受 MIME 类型数组。

**起始版本：** 18

<!--Device-FileSelectorParam-getMimeTypes(): Array<string>--><!--Device-FileSelectorParam-getMimeTypes(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | Return an array of raw acceptable MIME type. |

## getMode

```TypeScript
getMode(): FileSelectorMode
```

获取当前文件选择器的选择模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-getMode(): FileSelectorMode--><!--Device-FileSelectorParam-getMode(): FileSelectorMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileSelectorMode](arkts-arkweb-fileselectormode-e.md) | Return the FileSelectorMode of this file selector. |

## getSuggestedName

```TypeScript
getSuggestedName(): string
```

获取推荐文件名列表。

**起始版本：** 23

<!--Device-FileSelectorParam-getSuggestedName(): string--><!--Device-FileSelectorParam-getSuggestedName(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the suggested file names. |

## getTitle

```TypeScript
getTitle(): string
```

获取此文件选择器的标题。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-getTitle(): string--><!--Device-FileSelectorParam-getTitle(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the title of this file selector. |

## isAcceptAllOptionExcluded

```TypeScript
isAcceptAllOptionExcluded(): boolean
```

获取是否过滤完全匹配的文件类型。

**起始版本：** 23

<!--Device-FileSelectorParam-isAcceptAllOptionExcluded(): boolean--><!--Device-FileSelectorParam-isAcceptAllOptionExcluded(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return whether to filter all matching file types. |

## isCapture

```TypeScript
isCapture(): boolean
```

获取此文件选择器是否使用实时媒体拍摄所得内容。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-isCapture(): boolean--><!--Device-FileSelectorParam-isCapture(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return {@code true} if captured media; return {@code false} otherwise. |

