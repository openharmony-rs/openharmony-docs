# FileSelectorResult

The FileSelectorResult class in the ArkWeb component is used to notify the Web component of file selection results. It supports custom file selection behavior at the app layer and a unified file selection result return mechanism, making it suitable for scenarios where the app needs to take over the file selection process, such as returning selected file results to a web page after launching the system file picker, gallery picker, or camera picker. When an HTML page in the Web component initiates a file selection request through `&lt;input type="file"&gt;` or similar means, the app can use FileSelectorResult to return the user-selected file list to the Web component, completing the file selection process. This class is primarily used in the `onShowFileSelector` event callback, enabling the app to flexibly control file selection interactions and improve user experience consistency.

For details about the sample code, see [onShowFileSelector](arkts-arkweb-web-comp-attribute.md#onshowfileselector).

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **FileSelectorResult**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## handleFileList

```TypeScript
handleFileList(fileList: Array<string>): void
```

Notifies the Web component of the user-selected files through the passed file list (fileList), completing the file selection process. The Web component can use the passed file list for subsequent processing.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fileList | Array&lt;string&gt; | Yes | Array of file URI strings, used to pass the file paths selected by the user to the Web component. |
