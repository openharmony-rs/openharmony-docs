# DataExchangeOperation

交换数据操作。

**起始版本：** 12

<!--Device-unnamed-interface DataExchangeOperation--><!--Device-unnamed-interface DataExchangeOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: ExchangeIndex
```

交换位置。取值范围是[0, 数据源长度-1]。

**类型：** ExchangeIndex

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataExchangeOperation-index: ExchangeIndex--><!--Device-DataExchangeOperation-index: ExchangeIndex-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: ExchangeKey
```

分配新的键值，默认使用原键值。

**类型：** ExchangeKey

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataExchangeOperation-key?: ExchangeKey--><!--Device-DataExchangeOperation-key?: ExchangeKey-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.EXCHANGE
```

数据交换类型。

**类型：** DataOperationType.EXCHANGE

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataExchangeOperation-type: DataOperationType.EXCHANGE--><!--Device-DataExchangeOperation-type: DataOperationType.EXCHANGE-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

