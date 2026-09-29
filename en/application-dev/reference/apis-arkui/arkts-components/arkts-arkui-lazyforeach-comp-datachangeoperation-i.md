# DataChangeOperation

```TypeScript
interface DataChangeOperation
```

Represents an operation for changing data.

**Since:** 12

<!--Device-unnamed-interface DataChangeOperation--><!--Device-unnamed-interface DataChangeOperation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the changed data. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataChangeOperation-index: number--><!--Device-DataChangeOperation-index: number-End-->

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

<!--Device-DataChangeOperation-key?: string--><!--Device-DataChangeOperation-key?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.CHANGE
```

Data change type.

**Type:** [DataOperationType.CHANGE](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataChangeOperation-type: DataOperationType.CHANGE--><!--Device-DataChangeOperation-type: DataOperationType.CHANGE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
