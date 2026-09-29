# DataExchangeOperation

```TypeScript
interface DataExchangeOperation
```

Represents an operation for exchanging data.

**Since:** 12

<!--Device-unnamed-interface DataExchangeOperation--><!--Device-unnamed-interface DataExchangeOperation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: ExchangeIndex
```

Exchange position. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.

**Type:** [ExchangeIndex](arkts-arkui-lazyforeach-comp-exchangeindex-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataExchangeOperation-index: ExchangeIndex--><!--Device-DataExchangeOperation-index: ExchangeIndex-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: ExchangeKey
```

New keys to assign to the exchanged data. The original keys are used by default.

**Type:** [ExchangeKey](arkts-arkui-lazyforeach-comp-exchangekey-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataExchangeOperation-key?: ExchangeKey--><!--Device-DataExchangeOperation-key?: ExchangeKey-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.EXCHANGE
```

Data exchange type.

**Type:** [DataOperationType.EXCHANGE](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataExchangeOperation-type: DataOperationType.EXCHANGE--><!--Device-DataExchangeOperation-type: DataOperationType.EXCHANGE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
