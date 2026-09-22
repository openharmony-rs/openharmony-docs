# TextController

```TypeScript
declare class TextController
```

Defines the controller of the **Text** component.

## Objects to Import

```ts
controller: TextController = new TextController()
```

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

Closes the custom or default text selection menu.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLayoutManager

```TypeScript
getLayoutManager(): LayoutManager
```

Obtains the **LayoutManager** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LayoutManager](../arkts-apis/arkts-arkui-layoutmanager-i.md) | **LayoutManager** object. |

## setStyledString

```TypeScript
setStyledString(value: StyledString): void
```

Binds to or updates the specified styled string.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | Yes | Styled string.<br>**NOTE:** <br>The child class [MutableStyledString](../arkts-apis/arkts-arkui-mutablestyledstring-c.md) of **StyledString** can also serve as the argument. |

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number | undefined, selectionEnd: number | undefined,
                   options?: SelectionOptions): void
```

Sets the text selection area, which will be highlighted.

> **NOTE:** 
> 
> If [copyOption](arkts-arkui-text-comp-attribute.md#copyoption) is set to **CopyOptions.None**, the setting of
> **setTextSelection** does not take effect.
> 
> If [textOverflow](arkts-arkui-text-comp-attribute.md#textoverflow) is set to **TextOverflow.MARQUEE**, the setting of
> **setTextSelection** does not take effect.
> 
> If the value of **selectionStart** is greater than or equal to that of **selectionEnd**, no text will be
> selected. The value range is [0, textSize], where **textSize** indicates the maximum number of characters in the
> text content. If the value is less than 0, the value **0** will be used. If the value is greater than
> **textSize**, **textSize** will be used.
> 
> If the selection range falls within a truncated or invisible area, selection is ignored. When truncation is
> disabled, selection can extend beyond the parent component's bounds.
> 
> On PC or 2-in-1 devices, calling **setTextSelection** does not show the menu even if **options** is set to
> **MenuPolicy.SHOW**.
> 
> When an emoji is truncated by the selection range, the emoji is selected if its start position is within the
> specified text selection range.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number &#124; undefined | Yes | Start position of the text selection range.<br>Value range: [0, +∞). Negative values and **undefined** are treated as **0**. |
| selectionEnd | number &#124; undefined | Yes | End position of the text selection range.<br>Value range: [0, +∞). Negative values and **undefined** are treated as **0**. |
| options | [SelectionOptions](arkts-arkui-common-comp-selectionoptions-i.md) | No | Configuration options for text selection.<br>Default value: **MenuPolicy.DEFAULT** in **SelectionOptions** |
