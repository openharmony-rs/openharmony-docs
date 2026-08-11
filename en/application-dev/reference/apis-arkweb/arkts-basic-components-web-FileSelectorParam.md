# Class (FileSelectorParam)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=623aa80705a77d40ce586d33f4c6fd8a1890d6f9 translatedAt=2026-08-07T04:44:15.482Z pushedAt=2026-08-07T08:12:17.903Z -->

FileSelectorParam is a file selector parameter class in the ArkWeb component, used to obtain parameter information when a file selection request is triggered by `<input type="file">` in a web page, including the file selection mode, file filtering type, MIME type, suggested file name, and default starting path. It helps developers efficiently build custom file selectors that comply with HTML specifications.

When a web page initiates a file selection request, developers use FileSelectorParam to obtain the complete parameter information passed from the frontend, and build a custom file selector that matches the frontend requirements based on this information, ensuring that the file selection mode, type filtering, naming, and other behaviors comply with HTML specifications.

Used in scenarios where the Web component needs to custom-handle file upload requests. Register the `onShowFileSelector` callback to intercept file selection requests; obtain the FileSelectorParam instance from the `fileSelector` property of the callback event; read the parameters and build a corresponding system file selector (such as DocumentViewPicker, PhotoViewPicker, etc.); return the selection result to the Web component through FileSelectorResult.

For sample code, see [onShowFileSelector](./arkts-basic-components-web-events.md#onshowfileselector9).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **FileSelectorParam**.

**System capability**: SystemCapability.Web.Webview.Core

## getTitle<sup>9+</sup>

getTitle(): string

Obtains the title of this file selector.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description        |
| ------ | ---------- |
| string | Title string of the file selector, which indicates the title text displayed on the UI for the current file selector. |

## getMode<sup>9+</sup>

getMode(): FileSelectorMode

Obtains the mode of the file selector.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                                      | Description         |
| ---------------------------------------- | ----------- |
| [FileSelectorMode](./arkts-basic-components-web-e.md#fileselectormode9) | Mode of the file selector.|

## getAcceptType<sup>9+</sup>

> **NOTE**
>
> Correspondence with getMimeTypes and getAcceptableFileTypes: getAcceptType and getMimeTypes correspond to the accept attribute of the HTML input tag, and getAcceptableFileTypes corresponds to the types attribute of the options parameter of the HTML showOpenFilePicker, showDirectoryPicker, and showSaveFilePicker interfaces. According to HTML specifications, the accept attribute and the types attribute are mutually exclusive and should not be used at the same time.

getAcceptType(): Array\<string\>

Obtains the file filtering type.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type             | Description       |
| --------------- | --------- |
| Array\<string\> | Array of file filter types, containing type information used to limit the selectable file range in the file selector. The elements are extensions (such as '.png'), corresponding to the HTML accept attribute. |

## isCapture<sup>9+</sup>

isCapture(): boolean

Checks whether multimedia capabilities are invoked.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description          |
| ------- | ------------ |
| boolean | Whether to invoke multimedia capabilities.<br>The value **true** means that multimedia devices such as the camera or microphone need to be called to obtain files (for example, taking a photo or recording audio), and **false** means that only existing files are selected from the storage device. Corresponds to the **capture** attribute of the HTML input tag.|

## getMimeTypes<sup>18+</sup>

getMimeTypes(): Array\<string\>

Obtains the MIME type of a file.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type             | Description       |
| --------------- | --------- |
| Array\<string\> | Value of the accept attribute of the HTML input element, containing the MIME types and file extensions allowed for selection. |

## getSuggestedName<sup>23+</sup>

getSuggestedName(): string

Obtains the suggested file name. Corresponds to `suggestedName` in the HTML [option](../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface). If the frontend does not set suggestedName, an empty string is returned. Developers can use this return value as the default file name when building a file selector, and use it together with [getDefaultPath](#getdefaultpath23) to preset the complete file path and name.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description        |
| ------ | ---------- |
| string | String that suggests the default file name for the file selector. |

## getDefaultPath<sup>23+</sup>

getDefaultPath(): string

Obtains the default path of the file selector, which corresponds to **startIn** in HTML's [option](../../web/web-file-upload.md#customizing-the-file-request-initiated-by-the-javascript-api).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description        |
| ------ | ---------- |
| string | Default starting path.<br>When the frontend startIn is set to the public directories `downloads` or `pictures`, note that they should be converted to `download` and `images` in the OpenHarmony system, respectively. For details, see [Obtaining and Using Public Directories](../../file-management/request-dir-permission.md). |

## getDescriptions<sup>23+</sup>

getDescriptions(): Array\<string\>

Obtains the optional description of each group of allowed file types. Corresponds to `description` in the HTML [option](../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface). The returned description array corresponds one-to-one with the file type groups returned by getAcceptableFileTypes. Developers can use these descriptions as the display text for each file type group when building a file selector, helping users understand the selectable file types. If the frontend does not set description, an empty string is returned.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type             | Description       |
| --------------- | --------- |
| Array\<string\> | Array of description strings for file types, containing optional description text for each group of file types. |

## isAcceptAllOptionExcluded<sup>23+</sup>

isAcceptAllOptionExcluded(): boolean

Obtains whether the file selector excludes the option (*/*), that is, all files. Corresponds to `excludeAcceptAllOption` in the HTML [option](../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description          |
| ------- | ------------ |
| boolean | Whether to exclude the "All file types" option.<br>The value **true** means to exclude (the "All file types" option is not included), and **false** means to include (the developer must ensure that the "All file types" option is included in the file selector). |

## getAcceptableFileTypes<sup>23+</sup>

getAcceptableFileTypes(): Array\<Array\<AcceptableFileType\>>

Obtains the file type information. Corresponds to `types` in the HTML [option](../../web/web-file-upload.md#custom-handling-of-file-requests-initiated-by-js-interface). The return value is a two-dimensional array, where each sub-array represents a group of allowed file types. Developers should use this return value to set file type filtering rules when building a file selector, ensuring that users can only select files that meet the frontend requirements. The difference between this parameter and getAcceptType and getMimeTypes is that types supports more fine-grained file type control, allowing grouping by MIME type or file extension.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type             | Description       |
| --------------- | --------- |
| Array\<Array\<[AcceptableFileType](./arkts-basic-components-web-i.md#acceptablefiletype23)\>> | File type information, which is a two-dimensional array structure containing detailed information about multiple groups of optional file types. Corresponds to the types attribute of the HTML option. |
<!--no_check-->