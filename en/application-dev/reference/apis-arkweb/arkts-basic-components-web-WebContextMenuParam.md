# Class (WebContextMenuParam)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=579a3b230d60c35cd28258c4ed8312a8dd3cee8c translatedAt=2026-08-07T04:44:06.125Z pushedAt=2026-08-07T08:12:37.989Z -->

WebContextMenuParam is a parameter class in the ArkWeb component used to carry context menu information displayed when a user long presses a web element or right-clicks. As the data carrier for the **onContextMenuShow** event callback, it encapsulates key information such as the menu popup position, link address, media type, selected text, and edit state.

When customizing the context menu of a Web component, use WebContextMenuParam to obtain detailed information about the web element at the long press/right-click position (such as the link URL, image content, media type, input field type, and edit state), determine the user operation scenario, and decide whether to intercept the default menu and build custom menu items.

When customizing the long press or right-click menu of a Web component (such as replacing the default menu, providing differentiated menu items based on element types, or previewing images), use WebContextMenuParam in the **onContextMenuShow** event callback to obtain context information.

For sample code, see [onContextMenuShow](./arkts-basic-components-web-events.md#oncontextmenushow9).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **WebContextMenuParam** object.

**System capability**: SystemCapability.Web.Webview.Core

## x<sup>9+</sup>

x(): number

X coordinate of the context menu, which is the horizontal distance relative to the upper left corner of the Web component.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                                |
| ------ |------------------------------------|
| number | Non-negative integer if successful; -1 otherwise.<br>Unit: px (physical pixel). |

## y<sup>9+</sup>

y(): number

Y coordinate of the context menu, which is the vertical distance relative to the upper left corner of the Web component.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| number | Non-negative integer when obtained successfully, and -1 otherwise.<br>Unit: px (physical pixel). |

## getLinkUrl<sup>9+</sup>

getLinkUrl(): string

Obtains the URL link address that has passed the security check. This can be used to provide operations such as "Open Link", "Share Link", and "Copy Link" when building a custom menu.

> **NOTE**
>
> Compared with getUnfilteredLinkUrl(), this method performs a security check on the URL. Compared with getSourceUrl(), this method obtains the link URL at the long press position, whereas getSourceUrl() obtains the URL of the **src** attribute of the selected element (such as images, media, and other resources).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                       |
| ------ | ------------------------- |
| string | Security-checked URL if the long-press position is a link; otherwise, an empty string. |

## getUnfilteredLinkUrl<sup>9+</sup>

getUnfilteredLinkUrl(): string

Obtains the original URL link address that has not passed the security check.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                   |
| ------ | --------------------- |
| string | If the long-press position is a link, returns the original URL link; otherwise, returns an empty string. |

## getSourceUrl<sup>9+</sup>

getSourceUrl(): string

Obtains the URL link address corresponding to the **src** attribute of the element.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                      |
| ------ | ------------------------ |
| string | If the selected element has the **src** attribute, the URL in the **src** is returned. The maximum size of the returned URL is 2 MB. If the size exceeds the upper limit, an empty string is returned.|

## existsImageContents<sup>9+</sup>

existsImageContents(): boolean

Checks whether there is image content at the current long press or right-click position. This is used to provide image-related functions such as "Save Image" in a custom menu.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description                       |
| ------- | ------------------------- |
| boolean | true if an image exists at the long-press position; false otherwise. |

## getMediaType<sup>9+</sup>

getMediaType(): ContextMenuMediaType

Obtains the media type of the web element.

> **NOTE**
>
> Since API version 22, [getContextMenuMediaType](#getcontextmenumediatype22) provides richer media type identification capabilities.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                                      | Description       |
| ---------------------------------------- | --------- |
| [ContextMenuMediaType](./arkts-basic-components-web-e.md#contextmenumediatype9) | Media type of the web page element.|

## getSelectionText<sup>9+</sup>

getSelectionText(): string

Obtains the content when right-clicking selected text. This is used to provide text operation functions such as "Copy", "Share", "Translate", and "Search" in a custom menu.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                  |
| ------ | -------------------- |
| string | Selected text content. If selected text exists at the right-click position, the selected text is returned; otherwise, an empty string is returned. |

## getSourceType<sup>9+</sup>

getSourceType(): ContextMenuSourceType

Obtains the trigger source type of the context menu event (such as mouse right-click, long press, etc.). This is used to adjust the menu display style or provide differentiated menu options based on different sources.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| [ContextMenuSourceType](./arkts-basic-components-web-e.md#contextmenusourcetype9) | Type of the trigger source for the context menu event, including right-click, long press, and other trigger methods. |

## getInputFieldType<sup>9+</sup>

getInputFieldType(): ContextMenuInputFieldType

Obtains the input field type of the web element (such as text box, password box, search box, etc.). This is used to provide appropriate editing menu options based on the input field type (such as Paste and Select All for text boxes, and Copy or Hide Password for password boxes).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                                      | Description    |
| ---------------------------------------- | ------ |
| [ContextMenuInputFieldType](./arkts-basic-components-web-e.md#contextmenuinputfieldtype9) | Type of the web element input field, including text, password, email, and other types. It is used to identify the type of the input element that currently has focus. |

## isEditable<sup>9+</sup>

isEditable(): boolean

Checks whether a web element is editable. This is used to dynamically show or hide editing-related options in a custom menu (such as displaying Paste, Cut, and Select All when editable, and hiding these options when not editable).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description                        |
| ------- | -------------------------- |
| boolean | true if the web element is editable; false otherwise. |

## getEditStateFlags<sup>9+</sup>

getEditStateFlags(): number

Obtains the edit state flag of the web element. This is used to finely control the display logic of custom menu options (such as displaying corresponding menu items based on whether copying, pasting, or undoing is available).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                                      |
| ------ | ---------------------------------------- |
| number | Obtains the editable flag of the web element. See [ContextMenuEditStateFlags](./arkts-basic-components-web-e.md#contextmenueditstateflags9). |

## getPreviewWidth<sup>13+</sup>

getPreviewWidth(): number

Obtains the width of a preview image.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description      |
| ------ | ----------- |
| number | Width of a preview image.<br>Unit: px (physical pixel)|

## getPreviewHeight<sup>13+</sup>

getPreviewHeight(): number

Obtains the height of a preview image.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description      |
| ------ | ----------  |
| number | Height of a preview image.<br>Unit: px (physical pixel)|

## getContextMenuMediaType<sup>22+</sup>

getContextMenuMediaType(): ContextMenuDataMediaType

Obtains the type of the web element that the user long presses or right-clicks when reporting a context menu event.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description      |
| ------ | ----------  |
| [ContextMenuDataMediaType](./arkts-basic-components-web-e.md#contextmenudatamediatype22) | Media type of the web element, including image, video, audio, and other types, used to distinguish the type of web element tapped by the user. |
<!--no_check-->