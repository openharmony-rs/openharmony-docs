# DataAddOperation

```TypeScript
interface DataAddOperation
```

Represents an operation for adding data.

**Since:** 12

<!--Device-unnamed-interface DataAddOperation--><!--Device-unnamed-interface DataAddOperation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

Number of added data items. It must be a positive integer (greater than 0), and the default value is **1**. Passing 0 or a negative number may cause abnormal rendering.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataAddOperation-count?: number--><!--Device-DataAddOperation-count?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the added data. The value range is [0, data source length]. Rendering is abnormal when the value exceeds the range.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataAddOperation-index: number--><!--Device-DataAddOperation-index: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string | Array<string>
```

Assigns a key to the added data. The original key is used by default. The key supports the string or Array\&lt;string\&gt; type. If the key is an array whose length is greater than **count**, an invalid parameter error is reported.

**Type:** string &#124; Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataAddOperation-key?: string | Array<string>--><!--Device-DataAddOperation-key?: string | Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.ADD
```

Data addition type.

**Type:** [DataOperationType.ADD](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataAddOperation-type: DataOperationType.ADD--><!--Device-DataAddOperation-type: DataOperationType.ADD-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
