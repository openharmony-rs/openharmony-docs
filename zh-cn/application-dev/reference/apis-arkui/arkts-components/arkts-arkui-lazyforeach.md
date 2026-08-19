# LazyForEach

> **说明** > 开发者指南见：[LazyForEach开发者指南](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)。 LazyForEach是一种懒加载渲染控制组件，从提供的数据源中按需迭代数据并创建相应组件。在大量子组件的场景下，LazyForEach与缓存列表项、动态预加载、组件复用等方法配合使用，可以进一步提升滑动帧率并降低应用内存占用。

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string
  )
```

LazyForEach从提供的数据源中按需迭代数据，并在每次迭代过程中创建相应的组件。当在滚动容器中使用了LazyForEach，框架会根据滚动容器可视区域按需创建组件，当组件滑出可视区域外时，框架会进行组件销毁回收以降低内存占 用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-idatasource-i.md) | 是 | LazyForEach数据源，需要开发者实现相关接口。 |
| itemGenerator | (item: any, index: number) =&gt; void | 是 | 子组件生成函数，为数组中的每一个数据项创建一个子组件。 <br>**说明：** <br>- item是当前数据项（可选），index是数据项索引值（可选）。 <br>- 建议item的数据类型与数据源的数据类型保持一致，否则，当itemGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 <br>- itemGenerator的函数体必须使用大括号{...}。 <br>- itemGenerator每次迭代只能并且必须生成一个子组件。 <br>- itemGenerator中可以使用if语句，但是必须保证if语句每个分支都会创建一个相同类型的子组件。 |
| keyGenerator | (item: any, index: number) =&gt; string | 否 | 键值生成函数，用于给数据源中的每一个数据项生成唯一且固定的键值。修改数据源中的一个数据项若不影响其生成的键值，则对应组件不会被更新，否则对应组件就会被重建更新。 `keyGenerator`参数是可选的，但是，为了使开发框架能够更好地识别数组更改并正确更新组件，建议提供。 <br>默认使用框架内置的键值生成函数（详见下方说明）。 <br>**说明：** <br>- item是当前数据项（可选），index是数据项索引值（可选）。 <br>- 建议item的数据类型与数据源的数据类型保持一致，否则，当keyGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 <br>- `keyGenerator`缺省时，使用默认的键值生成函数，即 `(item: Object, index: number) => { return viewId + '-' + index.toString(); }`，生成键值仅受索引值index影响（viewId在编译器转换过程中 生成，同一个LazyForEach组件内的viewId一致）。 <br>- 为保证`LazyForEach`正确、高效地更新子组件，避免渲染结果异常、渲染效率降低等问题，键值应满足以下条件。 <br>1. 键值具有唯一性，每个数据项对应的键值互不相同。 <br>2. 键值具有一致性，数据项不变时对应的键值也不变。 |

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
    options?: LazyForEachOptions
  )
```

LazyForEach从提供的数据源中按需迭代数据，并在每次迭代过程中创建相应的组件。当在滚动容器中使用了LazyForEach，框架会根据滚动容器可视区域按需创建组件，当组件滑出可视区域外时，框架会进行组件销毁回收以降低内存占 用。 > **说明：**> > 从API版本26.0.0开始，LazyForEach支持传入[LazyForEachOptions](arkts-arkui-lazyforeachoptions-i.md)，用于使能自定义组件冻结和配置内存优化策略、资源释放策略。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-idatasource-i.md) | 是 | LazyForEach数据源，需要开发者实现相关接口。 |
| itemGenerator | (item: any, index: number) =&gt; void | 是 | 子组件生成函数，为数组中的每一个数据项创建一个子组件。 <br>**说明：** <br>- item是当前数据项（可选），index是数据项索引值（可选）。 <br>- 建议item的数据类型与数据源的数据类型保持一致，否则，当itemGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 <br>- itemGenerator的函数体必须使用大括号{...}。 <br>- itemGenerator每次迭代只能并且必须生成一个子组件。 <br>- itemGenerator中可以使用if语句，但是必须保证if语句每个分支都会创建一个相同类型的子组件。 |
| keyGenerator | (item: any, index: number) =&gt; string | 否 | 键值生成函数，用于给数据源中的每一个数据项生成唯一且固定的键值。修改数据源中的一个数据项若不影响其生成的键值，则对应组件不会被更新，否则对应组件就会被重建更 新。`keyGenerator`参数是可选的，但是，为了使开发框架能够更好地识别数组更改并正确更新组件，建议提供。 <br>默认使用框架内置的键值生成函数（详见下方说明）。 <br>**说明：** <br>- item是当前数据项（可选），index是数据项索引值（可选）。 <br>- 建议item的数据类型与数据源的数据类型保持一致，否则，当keyGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 <br>- `keyGenerator`缺省时，使用默认的键值生成函数，即 `(item: Object, index: number) => { return viewId + '-' + index.toString(); }`，生成键值仅受索引值index影响（viewId在编译器转换过程中 生成，同一个LazyForEach组件内的viewId一致）。 <br>- 为保证`LazyForEach`正确、高效地更新子组件，避免渲染结果异常、渲染效率降低等问题，键值应满足以下条件。 <br>1. 键值具有唯一性，每个数据项对应的键值互不相同。 <br>2. 键值具有一致性，数据项不变时对应的键值也不变。 |
| options | [LazyForEachOptions](arkts-arkui-lazyforeachoptions-i.md) | 否 | 开发者配置项，用于使能自定义组件冻结和配置内存优化策略、资源释放策略。使用此配置项时，必须设置键值生成函数，否则将编译失败。不传入时使用默认配置（ 自定义组件冻结模式默认为AUTO，资源释放策略默认为BATCH，内存优化策略默认为DEFAULT）。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [DataAddOperation](arkts-arkui-dataaddoperation-i.md) | 添加数据操作。 |
| [DataChangeListener](arkts-arkui-datachangelistener-i.md) | 数据变化监听器，用于在数据源发生变化时通知LazyForEach组件进行相应的渲染更新，支持数据添加、删除、改变、移动、交换、重载等多种数据变化类型的监听。 |
| [DataChangeOperation](arkts-arkui-datachangeoperation-i.md) | 改变数据操作。 |
| [DataDeleteOperation](arkts-arkui-datadeleteoperation-i.md) | 删除数据操作。 |
| [DataExchangeOperation](arkts-arkui-dataexchangeoperation-i.md) | 交换数据操作。 |
| [DataMoveOperation](arkts-arkui-datamoveoperation-i.md) | 移动数据操作。 |
| [DataReloadOperation](arkts-arkui-datareloadoperation-i.md) | 重载所有数据操作，并配置是否允许在更新过程中复用旧的子组件。当onDatasetChange含有DataOperationType.RELOAD操作时，其余操作全部失效，框架会自己调用keyGenerator进行键值比对。 配置允许在更新过程中复用旧的子组件，并和[@Reusable](../../../ui/state-management/arkts-reusable.md)/ [@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md)配合使用时，优先使用复用池中的组件，若复用池中无可复用的组件，而LazyForEach的旧子组件中 有可复用的组件，该组件将被回收，并复用为新的子组件。当LazyForEach的旧子组件中也没有可复用的组件时，将创建新的子组件。 配置允许在更新过程中复用旧的子组件，未使用@Reusable/@ReusableV2时，键值没有变化的数据项会使用原先的子组件，键值发生变化的会重建子组件。 配置不允许在更新过程中复用旧的子组件，键值没有变化的数据项会使用原先的子组件，键值发生变化的数据项，若使用了@Reusable/@ReusableV2且复用池中有可用的组件，将复用旧组件，否则将创建新的子组件。 |
| [ExchangeIndex](arkts-arkui-exchangeindex-i.md) | 定义交换数据的位置。 |
| [ExchangeKey](arkts-arkui-exchangekey-i.md) | 定义交换数据的新键值。 |
| [IDataSource](arkts-arkui-idatasource-i.md) | LazyForEach的数据源，开发者需要实现该接口以提供数据访问和数据变化通知能力，包括获取数据总数、按索引获取数据、注册和注销数据变化监听器等。 |
| [LazyForEachOptions](arkts-arkui-lazyforeachoptions-i.md) | 用于配置LazyForEach的资源释放策略、内存优化策略，以及是否使能自定义组件冻结。 |
| [MoveIndex](arkts-arkui-moveindex-i.md) | 定义移动数据的位置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DataOperation](arkts-arkui-dataoperation-t.md) | 数据操作类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataOperationType](arkts-arkui-dataoperationtype-e.md) | 枚举类型，数据操作说明。 |
| [LazyForEachCustomComponentFreezeMode](arkts-arkui-lazyforeachcustomcomponentfreezemode-e.md) | 选择是否使能自定义组件冻结。 |
| [LazyForEachMemOptStrategy](arkts-arkui-lazyforeachmemoptstrategy-e.md) | LazyForEach内存优化策略枚举。 |
| [LazyForEachReleaseStrategy](arkts-arkui-lazyforeachreleasestrategy-e.md) | 选择LazyForEach的资源释放策略。 |

