# @ohos.atomicservice.AtomicServiceSearch(This section describes the interfaces used by AtomicServiceSearch)

## Modules to Import

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [AtomicServiceSearch](arkts-arkui-atomicservice-atomicservicesearch-atomicservicesearch-s.md) | **AtomicServiceSearch** allows you to customize the default search area, customizable selection area, and function area (a maximum of two). |

### Interfaces

| Name | Description |
| --- | --- |
| [InputFilterParams](arkts-arkui-atomicservice-atomicservicesearch-inputfilterparams-i.md) | Sets regular expression for input filtering. |
| [MenuAlignParams](arkts-arkui-atomicservice-atomicservicesearch-menualignparams-i.md) | Sets the alignment between the drop-down list button and the drop-down list box. |
| [OperationParams](arkts-arkui-atomicservice-atomicservicesearch-operationparams-i.md) | Sets initialization parameters of the function area. |
| [SearchButtonParams](arkts-arkui-atomicservice-atomicservicesearch-searchbuttonparams-i.md) | Sets the search button located next to the search text box. |
| [SearchParams](arkts-arkui-atomicservice-atomicservicesearch-searchparams-i.md) | Provides optional attributes for the search area. |
| [SelectParams](arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md) | Provides optional attributes for the selection area. |

### Types

| Name | Description |
| --- | --- |
| [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | Called when the text content is scrolled. |
| [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | Called when a paste operation is performed. |
| [OnSelectCallback](arkts-arkui-onselectcallback-t.md) | Called when an item in the drop-down list box is selected. |
| [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | Called when the position of the text selection changes or when the cursor position changes during the editing state. |

## Examples

```TypeScript
### Example 1: Adding a Selection Area to AtomicServiceSearch

This example demonstrates how to use the select parameter to add a selection area on the left to the AtomicServiceSearch component.


```

```TypeScript
### Example 2: Adding a Function Item to AtomicServiceSearch

This example demonstrates how to use the operation parameter to add a function item on the right to the AtomicServiceSearch component.


```

```TypeScript
### Example 3: Adding a Selection Area and Function Item to AtomicServiceSearch

This example demonstrates how to add the selection area and function items on the left and right to the AtomicServiceSearch component.


```

```TypeScript
### Example 4: Binding the Search Callback Events to AtomicServiceSearch

This example demonstrates how to use the onWillInsert, onDidInsert, onWillDelete, and onDidDelete APIs to implement insert and delete operations.

The onSubmit API is used to submit content in the search area.

The onChange API is used to listen for the content changes in the search area.


```

```TypeScript
### Example 5: Customizing the Style of AtomicServiceSearch

This example demonstrates how to use the search, select, value, and placeholder parameters to customize the style of the AtomicServiceSearch component.


```

```TypeScript
### Example 6: Setting the Caret Position Using controller

This example demonstrates how to use the controller parameter to set the caret position, select the content in the specified area, and disable the editing state.


```

```TypeScript
### Example 7: Setting the Enter Key Type

This example demonstrates how to use the enterKeyType attribute to dynamically change the effect of the Enter key on the soft keyboard.


```

```TypeScript
### Example 8: Setting Text Feature Effects

This example demonstrates how to use the fontFeature attribute to display text with various typographic features.


```

```TypeScript
### Example 9: Setting Text Auto-Adaptation

This example demonstrates how to use the minFontSize and maxFontSize attributes to implement the text auto-adaptation features.


```

```TypeScript
### Example 10: Setting Custom Menu Extensions

This example demonstrates how to use the editMenuOptions API to create custom menu extensions for text settings. It includes customizing text content, icons, and callbacks for these extensions.


```

```TypeScript
### Example 11: Setting the Horizontal Alignment, Caret Style, and Background Color of the Selected Text

This example shows how to set the horizontal alignment, caret style, and background color of the selected text using textAlign, caretStyle, and selectedBackgroundColor.


```

```TypeScript
### Example 12: Setting Input Filtering

This example shows how to set input filtering using inputFilter.
```
