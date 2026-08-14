# DataLoadInfo

用于描述被加载数据的类型与数量。 - 在**数据发送方**中使用，表示实际可提供的数据范围，必须设置该字段。 - 在**数据接收方**中使用，表示期望加载的数据类型与数量，可根据需要设置该字段。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unifiedDataChannel-interface DataLoadInfo--><!--Device-unifiedDataChannel-interface DataLoadInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## recordCount

```TypeScript
recordCount?: long
```

表示期望或可提供的最大数据记录数，默认值为0，取值范围为[0, 2&lt;sup&gt;32&lt;/sup&gt;-1]。超过取值范围时会按默认值处理。设置为浮点数时，仅使用整数部分。当用于拖拽时，会作为角标数量显示，最大支持 2&lt;sup&gt;31&lt;/sup&gt;-1，超过此数值时不显示角标。作为角标数量时，优先级低于DragPreviewOptions中的numberBadge方法。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DataLoadInfo-recordCount?: long--><!--Device-DataLoadInfo-recordCount?: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## types

```TypeScript
types?: Set<string>
```

表示数据类型集合，默认为空集合。

**类型：** Set&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DataLoadInfo-types?: Set<string>--><!--Device-DataLoadInfo-types?: Set<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

