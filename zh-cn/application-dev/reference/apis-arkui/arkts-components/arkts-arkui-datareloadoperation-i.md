# DataReloadOperation

重载所有数据操作。当onDatasetChange含有DataOperationType.RELOAD操作时，其余操作全部失效，框架会自己调用keyGenerator进行键值比对。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.RELOAD
```

数据全部重载类型。

**类型：** DataOperationType.RELOAD

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

