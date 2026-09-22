# AlphabetIndexerOptions

```TypeScript
interface AlphabetIndexerOptions
```

Defines the options of the **AlphabetIndexer** component.

> **NOTE:** 

> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrayValue

```TypeScript
arrayValue: Array<string>
```

Array of index items.

**Type:** Array&lt;string&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: number
```

Index of the initial selected item. If the value is out of range, the default value **0** is used. When this parameter and the [selected](arkts-arkui-alphabetindexer-comp-attribute.md#selected) property are set at the same time, the **selected** property has a higher priority.

Value range: [0, arrayValue.length-1]

This parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
