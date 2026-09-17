# AccessibilityNextFocusParams

Defines the detailed parameter object that can be used during the accessibility custom next focus processing.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isConsiderDescendants

```TypeScript
isConsiderDescendants?: boolean
```

Whether to search for the focus in descendant nodes during custom next-focus processing for accessibility.

The value **true** means to search for the focus in descendant nodes during custom next-focus processing for accessibility; the value **false** means not to search for the focus in descendant nodes during custom next-focus processing for accessibility.

Default value: **false**

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
