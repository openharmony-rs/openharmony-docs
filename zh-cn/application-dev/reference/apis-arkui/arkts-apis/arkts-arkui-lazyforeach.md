# LazyForEach

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string
  )
```

LazyForEach从提供的数据源中按需迭代数据，并在每次迭代过程中创建相应的组件。当在滚动容器中使用了LazyForEach，框架会根据滚动容器可视区域按需创建组件，当组件滑出可视区域外时，框架会进行组件销毁回收以降低内存占
用。

**起始版本：** 7

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为7.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | IDataSource | 是 |  |
| itemGenerator | (item: any, index: number) => void | 是 |  |
| keyGenerator | (item: any, index: number) => string | 否 |  |

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
    options?: LazyForEachOptions
  )
```

LazyForEach从提供的数据源中按需迭代数据，并在每次迭代过程中创建相应的组件。当在滚动容器中使用了LazyForEach，框架会根据滚动容器可视区域按需创建组件，当组件滑出可视区域外时，框架会进行组件销毁回收以降低内存占
用。

**起始版本：** 26.0.0

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为26.0.0.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | IDataSource | 是 |  |
| itemGenerator | (item: any, index: number) => void | 是 |  |
| keyGenerator | (item: any, index: number) => string | 否 |  |
| options | LazyForEachOptions | 否 |  |

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
