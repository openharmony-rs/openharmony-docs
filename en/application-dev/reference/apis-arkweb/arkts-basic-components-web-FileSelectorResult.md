# Class (FileSelectorResult)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=35181dc1ccfbe6cad3ff7ad0c647f99450ab4961 translatedAt=2026-08-07T04:41:33.709Z pushedAt=2026-08-07T13:49:56.910Z -->

The FileSelectorResult class in the ArkWeb component is used to notify the Web component of file selection results. It supports custom file selection behavior at the app layer and a unified file selection result return mechanism, making it suitable for scenarios where the app needs to take over the file selection process, such as returning selected file results to a web page after launching the system file picker, gallery picker, or camera picker. When an HTML page in the Web component initiates a file selection request through `<input type="file">` or similar means, the app can use FileSelectorResult to return the user-selected file list to the Web component, completing the file selection process. This class is primarily used in the `onShowFileSelector` event callback, enabling the app to flexibly control file selection interactions and improve user experience consistency.

For details about the sample code, see [onShowFileSelector](./arkts-basic-components-web-events.md#onshowfileselector9).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **FileSelectorResult**.

**System capability**: SystemCapability.Web.Webview.Core

## handleFileList<sup>9+</sup>

handleFileList(fileList: Array\<string\>): void

Notifies the Web component of the user-selected files through the passed file list (fileList), completing the file selection process. The Web component can use the passed file list for subsequent processing.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name     | Type           | Mandatory | Description        |
| -------- | --------------- | ---- | ------------ |
| fileList | Array\<string\> | Yes | Array of file URI strings, used to pass the file paths selected by the user to the Web component. |