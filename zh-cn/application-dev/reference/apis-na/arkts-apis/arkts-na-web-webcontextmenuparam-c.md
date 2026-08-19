# WebContextMenuParam

Defines the context menu param, related to [WebContextMenuParam](#webcontextmenuparam) method.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class WebContextMenuParam--><!--Device-unnamed-export declare class WebContextMenuParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-constructor()--><!--Device-WebContextMenuParam-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## existsImageContents

```TypeScript
existsImageContents(): boolean
```

Long press menu location has image content.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-existsImageContents(): boolean--><!--Device-WebContextMenuParam-existsImageContents(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return whether this context menu has image content. |

## getContextMenuMediaType

```TypeScript
getContextMenuMediaType(): ContextMenuDataMediaType
```

Returns the type of context node.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getContextMenuMediaType(): ContextMenuDataMediaType--><!--Device-WebContextMenuParam-getContextMenuMediaType(): ContextMenuDataMediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuDataMediaType](arkts-na-web-contextmenudatamediatype-e.md) | Returns the type of context node. |

## getEditStateFlags

```TypeScript
getEditStateFlags(): int
```

Returns the context editable flags [ContextMenuEditStateFlags](arkts-na-web-contextmenueditstateflags-e.md).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getEditStateFlags(): int--><!--Device-WebContextMenuParam-getEditStateFlags(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int |  |

## getInputFieldType

```TypeScript
getInputFieldType(): ContextMenuInputFieldType
```

Returns input field type if the context menu was invoked on an input field.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getInputFieldType(): ContextMenuInputFieldType--><!--Device-WebContextMenuParam-getInputFieldType(): ContextMenuInputFieldType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuInputFieldType](arkts-na-web-contextmenuinputfieldtype-e.md) | Input field type if the context menu was invoked on an input field. |

## getLinkUrl

```TypeScript
getLinkUrl(): string
```

If the long-press location is the link returns the link's security-checked URL.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getLinkUrl(): string--><!--Device-WebContextMenuParam-getLinkUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | If relate to a link return link url, else return null. |

## getMediaType

```TypeScript
getMediaType(): ContextMenuMediaType
```

Returns the type of context node.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getMediaType(): ContextMenuMediaType--><!--Device-WebContextMenuParam-getMediaType(): ContextMenuMediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuMediaType](arkts-na-web-contextmenumediatype-e.md) | Returns the type of context node. |

## getPreviewHeight

```TypeScript
getPreviewHeight(): int
```

Returns the selection menu preview height.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getPreviewHeight(): int--><!--Device-WebContextMenuParam-getPreviewHeight(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The preview menu height. Unit: px. |

## getPreviewWidth

```TypeScript
getPreviewWidth(): int
```

Returns the selection menu preview width.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getPreviewWidth(): int--><!--Device-WebContextMenuParam-getPreviewWidth(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The preview menu width. Unit: px. |

## getSelectionText

```TypeScript
getSelectionText(): string
```

Returns the text of the selection.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getSelectionText(): string--><!--Device-WebContextMenuParam-getSelectionText(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the text of the selection, or return null if no text is selected. |

## getSourceType

```TypeScript
getSourceType(): ContextMenuSourceType
```

Returns the context menu source type.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getSourceType(): ContextMenuSourceType--><!--Device-WebContextMenuParam-getSourceType(): ContextMenuSourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuSourceType](arkts-na-web-contextmenusourcetype-e.md) |  |

## getSourceUrl

```TypeScript
getSourceUrl(): string
```

Returns the SRC URL if the selected element has a SRC attribute.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getSourceUrl(): string--><!--Device-WebContextMenuParam-getSourceUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | If this context menu is "src" attribute, return link url, else return null. |

## getUnfilteredLinkUrl

```TypeScript
getUnfilteredLinkUrl(): string
```

If the long-press location is the link returns the link's original URL.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-getUnfilteredLinkUrl(): string--><!--Device-WebContextMenuParam-getUnfilteredLinkUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | If relate to a link return unfiltered link url, else return null. |

## isEditable

```TypeScript
isEditable(): boolean
```

Returns whether the context is editable.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-isEditable(): boolean--><!--Device-WebContextMenuParam-isEditable(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean |  |

## x

```TypeScript
x(): int
```

Horizontal offset coordinates of the menu within the Web component.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-x(): int--><!--Device-WebContextMenuParam-x(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The context menu x coordinate. Returns a non-negative integer if normal, otherwise returns -1. Unit: px. |

## y

```TypeScript
y(): int
```

Vertical offset coordinates for the menu within the Web component.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuParam-y(): int--><!--Device-WebContextMenuParam-y(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The context menu y coordinate. Returns a non-negative integer if normal, otherwise returns -1. Unit: px. |

