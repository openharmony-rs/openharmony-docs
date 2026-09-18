# AlphabetIndexer

The **AlphabetIndexer** component can create a logically indexed array of items in a container for instant location.

> **NOTE**

## Child Components

Not supported

## AlphabetIndexer

```TypeScript
AlphabetIndexer(options: AlphabetIndexerOptions)
```

Creates an **AlphabetIndexer** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | Yes | Options of the **AlphabetIndexer** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | Defines the options of the **AlphabetIndexer** component. |

### Types

| Name | Description |
| --- | --- |
| [OnAlphabetIndexerPopupSelectCallback](arkts-arkui-onalphabetindexerpopupselectcallback-t.md) | Represents the callback invoked when a secondary index item in the pop-up window is selected. |
| [OnAlphabetIndexerRequestPopupDataCallback](arkts-arkui-onalphabetindexerrequestpopupdatacallback-t.md) | Represents the callback invoked when an index item is selected and [usingPopup](arkts-arkui-alphabetindexer-comp-attribute.md#usingpopup) is set to **true**. |
| [OnAlphabetIndexerSelectCallback](arkts-arkui-onalphabetindexerselectcallback-t.md) | Represents the callback invoked when an index item is selected. |

### Enums

| Name | Description |
| --- | --- |
| [IndexerAlign](arkts-arkui-indexeralign-e.md) | Enumerates the alignment styles of the indexer pop-up window. |

## Examples

```TypeScript
### Example 1: Setting the Display Text for the Index Pop-up Window

This example demonstrates how to customize the display text for the index pop-up window using the [onRequestPopupData](arkts-arkui-alphabetindexer-comp-attribute.md#onrequestpopupdata) event.


```

```TypeScript
### Example 2: Enabling Adaptive Collapse Mode

This example demonstrates how to enable adaptive collapse mode using the [autoCollapse](#autocollapse11) attribute.


```

```TypeScript
### Example 3: Setting the Background Blur Style of the Pop-up Window

This example demonstrates how to apply a background blur effect to the pop-up window using the [popupBackgroundBlurStyle](#popupbackgroundblurstyle12) attribute.
```
