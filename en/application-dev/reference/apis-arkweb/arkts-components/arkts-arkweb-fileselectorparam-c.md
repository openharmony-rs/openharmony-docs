# FileSelectorParam

FileSelectorParam is a file selector parameter class in the ArkWeb component, used to obtain parameter information when a file selection request is triggered by `&lt;input type="file"&gt;` in a web page, including the file selection mode, file filtering type, MIME type, suggested file name, and default starting path. It helps developers efficiently build custom file selectors that comply with HTML specifications.

When a web page initiates a file selection request, developers use FileSelectorParam to obtain the complete parameter information passed from the frontend, and build a custom file selector that matches the frontend requirements based on this information, ensuring that the file selection mode, type filtering, naming, and other behaviors comply with HTML specifications.

Used in scenarios where the Web component needs to custom-handle file upload requests. Register the `onShowFileSelector` callback to intercept file selection requests; obtain the FileSelectorParam instance from the `fileSelector` property of the callback event; read the parameters and build a corresponding system file selector (such as DocumentViewPicker, PhotoViewPicker, etc.); return the selection result to the Web component through FileSelectorResult.

For sample code, see [onShowFileSelector](arkts-arkweb-web-comp-attribute.md#onshowfileselector).

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **FileSelectorParam**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## getAcceptableFileTypes

```TypeScript
getAcceptableFileTypes(): Array<Array<AcceptableFileType>>
```

Obtains the file type information. Corresponds to `types` in the HTML [option](../../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface). The return value is a two-dimensional array, where each sub-array represents a group of allowed file types. Developers should use this return value to set file type filtering rules when building a file selector, ensuring that users can only select files that meet the frontend requirements. The difference between this parameter and getAcceptType and getMimeTypes is that types supports more fine-grained file type control, allowing grouping by MIME type or file extension.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Array&lt;[AcceptableFileType](arkts-arkweb-acceptablefiletype-i.md)&gt;&gt; | File type information, which is a two-dimensional array structure containing detailed information about multiple groups of optional file types. Corresponds to the types attribute of the HTML option. |

## getAcceptType

```TypeScript
getAcceptType(): Array<string>
```

Obtains the file filtering type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Array of file filter types, containing type information used to limit the selectable file range in the file selector. The elements are extensions (such as '.png'), corresponding to the HTML accept attribute. |

## getDefaultPath

```TypeScript
getDefaultPath(): string
```

Obtains the default path of the file selector, which corresponds to **startIn** in HTML's [option](../../../web/web-file-upload.md#customizing-the-file-request-initiated-by-the-javascript-api).

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Default starting path. <br>When the frontend startIn is set to the public directories `downloads` or `pictures`, note that they should be converted to `download` and `images` in the OpenHarmony system, respectively. For details, see [Obtaining and Using Public Directories](../../../file-management/request-dir-permission.md). |

## getDescriptions

```TypeScript
getDescriptions(): Array<string>
```

Obtains the optional description of each group of allowed file types. Corresponds to `description` in the HTML [option](../../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface). The returned description array corresponds one-to-one with the file type groups returned by getAcceptableFileTypes. Developers can use these descriptions as the display text for each file type group when building a file selector, helping users understand the selectable file types. If the frontend does not set description, an empty string is returned.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Array of description strings for file types, containing optional description text for each group of file types. |

## getMimeTypes

```TypeScript
getMimeTypes(): Array<string>
```

Obtains the MIME type of a file.

**Since:** 18

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Value of the accept attribute of the HTML input element, containing the MIME types and file extensions allowed for selection. |

## getMode

```TypeScript
getMode(): FileSelectorMode
```

Obtains the mode of the file selector.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [FileSelectorMode](arkts-arkweb-fileselectormode-e.md) | Mode of the file selector. |

## getSuggestedName

```TypeScript
getSuggestedName(): string
```

Obtains the suggested file name. Corresponds to `suggestedName` in the HTML [option](../../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface). If the frontend does not set suggestedName, an empty string is returned. Developers can use this return value as the default file name when building a file selector, and use it together with [getDefaultPath](#getdefaultpath) to preset the complete file path and name.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | String that suggests the default file name for the file selector. |

## getTitle

```TypeScript
getTitle(): string
```

Obtains the title of this file selector.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Title string of the file selector, which indicates the title text displayed on the UI for the current file selector. |

## isAcceptAllOptionExcluded

```TypeScript
isAcceptAllOptionExcluded(): boolean
```

Obtains whether the file selector excludes the option (*\/*), that is, all files. Corresponds to `excludeAcceptAllOption` in the HTML [option](../../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface).

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether to exclude the "All file types" option.<br>The value **true** means to exclude (the "All file types" option is not included), and **false** means to include (the developer must ensure that the "All file types" option is included in the file selector). |

## isCapture

```TypeScript
isCapture(): boolean
```

Checks whether multimedia capabilities are invoked.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether to invoke multimedia capabilities.<br>The value **true** means that multimedia devices such as the camera or microphone need to be called to obtain files (for example, taking a photo or recording audio), and **false** means that only existing files are selected from the storage device. Corresponds to the **capture** attribute of the HTML input tag. |
