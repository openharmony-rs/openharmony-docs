# FileSelectorParam

Encompassed message information as parameters to [onFileSelectorShow](../../apis-arkweb/arkts-components/arkts-arkweb-web-attribute.md#onfileselectorshow) method.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class FileSelectorParam--><!--Device-unnamed-export declare class FileSelectorParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-FileSelectorParam-constructor()--><!--Device-FileSelectorParam-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getAcceptType

```TypeScript
getAcceptType(): Array<string>
```

Gets an array of acceptable MIME type.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Gets an array of selected types for web page files.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-FileSelectorParam-getAcceptableFileTypes(): Array<Array<AcceptableFileType>>--><!--Device-FileSelectorParam-getAcceptableFileTypes(): Array<Array<AcceptableFileType>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Array&lt;[AcceptableFileType](arkts-na-web-acceptablefiletype-i.md)&gt;&gt; | Return an array of selected types for web page files. |

## getDefaultPath

```TypeScript
getDefaultPath(): string
```

Get the default path opened when pulling up the selector.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Gets a description array of file types.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Gets an array of raw acceptable MIME type.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Gets the FileSelectorMode of this file selector.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-FileSelectorParam-getMode(): FileSelectorMode--><!--Device-FileSelectorParam-getMode(): FileSelectorMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileSelectorMode](arkts-na-web-fileselectormode-e.md) | Return the FileSelectorMode of this file selector. |

## getSuggestedName

```TypeScript
getSuggestedName(): string
```

Gets suggested file names.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Gets the title of this file selector.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Gets whether to filter fully matching file types.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Gets whether this file selector use a live media captured value.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-FileSelectorParam-isCapture(): boolean--><!--Device-FileSelectorParam-isCapture(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return { |

