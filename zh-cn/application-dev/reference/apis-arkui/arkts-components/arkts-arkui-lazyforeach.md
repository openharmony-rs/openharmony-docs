# LazyForEach

> **说明：**

开发者指南见：[LazyForEach开发者指南](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)。

在大量子组件的场景下，LazyForEach与缓存列表项、动态预加载、组件复用等方法配合使用，可以进一步提升滑动帧率并降低应用内存占用。最佳实践请参考
[优化长列表加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-best-practices-long-list)。


## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string
  )
```

LazyForEach从提供的数据源中按需迭代数据，并在每次迭代过程中创建相应的组件。当在滚动容器中使用了LazyForEach，框架会根据滚动容器可视区域按需创建组件，当组件滑出可视区域外时，框架会进行组件销毁回收以降低内存占用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-idatasource-i.md) | 是 | LazyForEach数据源，需要开发者实现相关接口。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支 持在原子化服务中使用。  |
| itemGenerator | (item: any, index: number) =&gt; void | 是 | 子组件生成函数，为数组中的每一个数据项创建一个子组件。<br/>**说明：**<br/>- item是当前数据项（可选），index是数据项索引值（可选）。< br/>- itemGenerator的函数体必须使用大括号{...}。<br />- itemGenerator每次迭代只能并且必须生成一个子组件。<br />- itemGenerator中可以使用if语句，但是必须保 证if语句每个分支都会创建一个相同类型的子组件。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。  |
| keyGenerator | (item: any, index: number) =&gt; string | 否 | 键值生成函数，用于给数据源中的每一个数据项生成唯一且固定的键值。修改数据源中的一个数据项若不影响其生成的键值，则对应组件不会被更新，否则此处组件就会被重建更新。 `keyGenerator`参数是可选的，但是，为了使开发框架能够更好地识别数组更改并正确更新组件，建议提供。<br/>默认值为空回调函数。<br/>**说明：**<br/>- item是当前数据项（可选），index是数 据项索引值（可选）。<br/>- `keyGenerator`缺省时，使用默认的键值生成函数，即 `(item: Object, index: number) => { return viewId + '-' + index.toString(); }`，生成键值仅受索引值index影响（viewId在编译器转换过程中 生成，同一个LazyForEach组件内的viewId一致）。<br/>- 为保证`LazyForEach`正确、高效地更新子组件，避免渲染结果异常、渲染效率降低等问题，键值应满足以下条件。<br/>1. 键值具有唯一性， 每个数据项对应的键值互不相同。<br/>2. 键值具有一致性，数据项不变时对应的键值也不变。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。  |

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
    options?: LazyForEachOptions
  )
```

LazyForEach从提供的数据源中按需迭代数据，并在每次迭代过程中创建相应的组件。当在滚动容器中使用了LazyForEach，框架会根据滚动容器可视区域按需创建组件，当组件滑出可视区域外时，框架会进行组件销毁回收以降低内存占用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-idatasource-i.md) | 是 |  |
| itemGenerator | (item: any, index: number) =&gt; void | 是 |  |
| keyGenerator | (item: any, index: number) =&gt; string | 否 |  |
| options | [LazyForEachOptions](arkts-arkui-lazyforeachoptions-i.md) | 否 |  |

## 汇总

- [DataAddOperation](arkts-arkui-lazyforeach-dataaddoperation-i.md)
- [DataChangeListener](arkts-arkui-lazyforeach-datachangelistener-i.md)
- [DataChangeOperation](arkts-arkui-lazyforeach-datachangeoperation-i.md)
- [DataDeleteOperation](arkts-arkui-lazyforeach-datadeleteoperation-i.md)
- [DataExchangeOperation](arkts-arkui-lazyforeach-dataexchangeoperation-i.md)
- [DataMoveOperation](arkts-arkui-lazyforeach-datamoveoperation-i.md)
- [DataReloadOperation](arkts-arkui-lazyforeach-datareloadoperation-i.md)
- [ExchangeIndex](arkts-arkui-lazyforeach-exchangeindex-i.md)
- [ExchangeKey](arkts-arkui-lazyforeach-exchangekey-i.md)
- [IDataSource](arkts-arkui-lazyforeach-idatasource-i.md)
- [LazyForEachOptions](arkts-arkui-lazyforeach-lazyforeachoptions-i.md)
- [MoveIndex](arkts-arkui-lazyforeach-moveindex-i.md)
- [DataOperation](arkts-arkui-lazyforeach-dataoperation-t.md)
- [DataOperationType](arkts-arkui-lazyforeach-dataoperationtype-e.md)
- [LazyForEachCustomComponentFreezeMode](arkts-arkui-lazyforeach-lazyforeachcustomcomponentfreezemode-e.md)
- [LazyForEachMemOptStrategy](arkts-arkui-lazyforeach-lazyforeachmemoptstrategy-e.md)
- [LazyForEachReleaseStrategy](arkts-arkui-lazyforeach-lazyforeachreleasestrategy-e.md)
