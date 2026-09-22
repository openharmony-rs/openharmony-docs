# TabsSidebarSearchableOptions

```TypeScript
declare interface TabsSidebarSearchableOptions
```

Defines the options for the searchable sidebar tab bar.

**Since:** 26.2.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## searchCallback

```TypeScript
searchCallback?: (text: string) => void
```

Callback triggered when the search text changes.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | The current search text. |

## searchFilter

```TypeScript
searchFilter?: TabsSidebarSearchFilterCallback
```

Filter function to determine whether a tab should be displayed based on the search text.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Placeholder text displayed when the search input is empty.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## searchText

```TypeScript
searchText?: ResourceStr
```

Sets the text input in the search text box.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
