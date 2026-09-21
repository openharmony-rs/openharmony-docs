# DataChangeOperation

```TypeScript
interface DataChangeOperation
```

Represents an operation for changing data.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the data to be changed. The value range is [0, data source length - 1].

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

New key to assign to the changed data. The original key is used by default.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.CHANGE
```

Type of data change.

**Type:** [DataOperationType.CHANGE](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
