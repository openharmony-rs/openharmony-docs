# DataDeleteOperation

```TypeScript
interface DataDeleteOperation
```

Represents an operation for deleting data.

**Since:** 12

<!--Device-unnamed-interface DataDeleteOperation--><!--Device-unnamed-interface DataDeleteOperation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

Number of data items to delete. It must be a positive integer (greater than 0), and the sum of **index** and **count** must not exceed the data source length. The default value is 1. If a negative number is passed in, this operation is ignored. If 0 is passed in, the data item at the **index** position is abnormally marked for deletion. If the sum of **index** and **count** exceeds the data source length, rendering may be abnormal.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataDeleteOperation-count?: number--><!--Device-DataDeleteOperation-count?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the start position for deletion. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataDeleteOperation-index: number--><!--Device-DataDeleteOperation-index: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.DELETE
```

Data deletion type.

**Type:** [DataOperationType.DELETE](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataDeleteOperation-type: DataOperationType.DELETE--><!--Device-DataDeleteOperation-type: DataOperationType.DELETE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
