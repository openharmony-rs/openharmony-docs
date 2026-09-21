# DataExchangeOperation

```TypeScript
interface DataExchangeOperation
```

Represents an operation for exchanging data.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: ExchangeIndex
```

Positions for the exchange. The value range is [0, data source length - 1].

**Type:** [ExchangeIndex](arkts-arkui-lazyforeach-comp-exchangeindex-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.EXCHANGE
```

Type of data exchange.

**Type:** [DataOperationType.EXCHANGE](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
