# WebContextMenuParam

WebContextMenuParam is a parameter class in the ArkWeb component used to carry context menu information displayed when a user long presses a web element or right-clicks. As the data carrier for the **onContextMenuShow** event callback, it encapsulates key information such as the menu popup position, link address, media type, selected text, and edit state.

When customizing the context menu of a Web component, use WebContextMenuParam to obtain detailed information about the web element at the long press/right-click position (such as the link URL, image content, media type, input field type, and edit state), determine the user operation scenario, and decide whether to intercept the default menu and build custom menu items.

When customizing the long press or right-click menu of a Web component (such as replacing the default menu, providing differentiated menu items based on element types, or previewing images), use WebContextMenuParam in the **onContextMenuShow** event callback to obtain context information.

For sample code, see [onContextMenuShow](arkts-arkweb-web-comp-attribute.md#oncontextmenushow).

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **WebContextMenuParam** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## existsImageContents

```TypeScript
existsImageContents(): boolean
```

Checks whether there is image content at the current long press or right-click position. This is used to provide image-related functions such as "Save Image" in a custom menu.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if an image exists at the long-press position; false otherwise. |

## getContextMenuMediaType

```TypeScript
getContextMenuMediaType(): ContextMenuDataMediaType
```

Obtains the type of the web element that the user long presses or right-clicks when reporting a context menu event.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ContextMenuDataMediaType](arkts-arkweb-contextmenudatamediatype-e.md) | Media type of the web element, including image, video, audio, and other types, used to distinguish the type of web element tapped by the user. |

## getEditStateFlags

```TypeScript
getEditStateFlags(): number
```

Obtains the edit state flag of the web element. This is used to finely control the display logic of custom menu options (such as displaying corresponding menu items based on whether copying, pasting, or undoing is available).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Obtains the editable flag of the web element. See [ContextMenuEditStateFlags](arkts-arkweb-contextmenueditstateflags-e.md). |

## getInputFieldType

```TypeScript
getInputFieldType(): ContextMenuInputFieldType
```

Obtains the input field type of the web element (such as text box, password box, search box, etc.). This is used to provide appropriate editing menu options based on the input field type (such as Paste and Select All for text boxes, and Copy or Hide Password for password boxes).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ContextMenuInputFieldType](arkts-arkweb-contextmenuinputfieldtype-e.md) | Type of the web element input field, including text, password, email, and other types. It is used to identify the type of the input element that currently has focus. |

## getLinkUrl

```TypeScript
getLinkUrl(): string
```

Obtains the URL link address that has passed the security check. This can be used to provide operations such as "Open Link", "Share Link", and "Copy Link" when building a custom menu.

> **NOTE:** 
> 
> Compared with getUnfilteredLinkUrl(), this method performs a security check on the URL. Compared with
> getSourceUrl(), this method obtains the link URL at the long press position, whereas getSourceUrl() obtains the
> URL of the **src** attribute of the selected element (such as images, media, and other resources).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Security-checked URL if the long-press position is a link; otherwise, an empty string. |

## getMediaType

```TypeScript
getMediaType(): ContextMenuMediaType
```

Obtains the media type of the web element.

> **NOTE:** 
> 
> Since API version 22, [getContextMenuMediaType](#getcontextmenumediatype) provides
> richer media type identification capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ContextMenuMediaType](arkts-arkweb-contextmenumediatype-e.md) | Media type of the web page element. |

## getPreviewHeight

```TypeScript
getPreviewHeight(): number
```

Obtains the height of a preview image.

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Height of a preview image.<br>Unit: px (physical pixel) |

## getPreviewWidth

```TypeScript
getPreviewWidth(): number
```

Obtains the width of a preview image.

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Width of a preview image.<br>Unit: px (physical pixel) |

## getSelectionText

```TypeScript
getSelectionText(): string
```

Obtains the content when right-clicking selected text. This is used to provide text operation functions such as "Copy", "Share", "Translate", and "Search" in a custom menu.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Selected text content. If selected text exists at the right-click position, the selected text is returned; otherwise, an empty string is returned. |

## getSourceType

```TypeScript
getSourceType(): ContextMenuSourceType
```

Obtains the trigger source type of the context menu event (such as mouse right-click, long press, etc.). This is used to adjust the menu display style or provide differentiated menu options based on different sources.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ContextMenuSourceType](arkts-arkweb-contextmenusourcetype-e.md) | Type of the trigger source for the context menu event, including right-click, long press, and other trigger methods. |

## getSourceUrl

```TypeScript
getSourceUrl(): string
```

Obtains the URL link address corresponding to the **src** attribute of the element.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | If the selected element has the **src** attribute, the URL in the **src** is returned. The maximum size of the returned URL is 2 MB. If the size exceeds the upper limit, an empty string is returned. |

## getUnfilteredLinkUrl

```TypeScript
getUnfilteredLinkUrl(): string
```

Obtains the original URL link address that has not passed the security check.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | If the long-press position is a link, returns the original URL link; otherwise, returns an empty string. |

## isEditable

```TypeScript
isEditable(): boolean
```

Checks whether a web element is editable. This is used to dynamically show or hide editing-related options in a custom menu (such as displaying Paste, Cut, and Select All when editable, and hiding these options when not editable).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if the web element is editable; false otherwise. |

## x

```TypeScript
x(): number
```

X coordinate of the context menu, which is the horizontal distance relative to the upper left corner of the Web component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Non-negative integer if successful; -1 otherwise.<br>Unit: px (physical pixel). |

## y

```TypeScript
y(): number
```

Y coordinate of the context menu, which is the vertical distance relative to the upper left corner of the Web component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Non-negative integer when obtained successfully, and -1 otherwise.<br>Unit: px (physical pixel). |
