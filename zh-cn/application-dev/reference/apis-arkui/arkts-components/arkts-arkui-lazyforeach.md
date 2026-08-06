# LazyForEach

> **说明** > 开发者指南见：[LazyForEach开发者指南](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)。 LazyForEach是一种懒加载渲染控制组件，从提供的数据源中按需迭代数据并创建相应组件。在大量子组件的场景下，LazyForEach与缓存列表项、动态预加载、组件复用等方法配合使用，可以进一步提升滑动帧率并降低应用内存占用。

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | LazyForEach数据源，需要开发者实现相关接口。  |
| itemGenerator | (item: any, index: number) =&gt; void | 是 | 子组件生成函数，为数组中的每一个数据项创建一个子组件。 \_\_\_HTML\_TAG\_USD\_0\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_1\_\_\_- item是当前数据项（可选），index是数据项索引值（可选）。 \_\_\_HTML\_TAG\_USD\_2\_\_\_- 建议item的数据类型与数据源的数据类型保持一致，否则，当itemGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 \_\_\_HTML\_TAG\_USD\_3\_\_\_- itemGenerator的函数体必须使用大括号{...}。 \_\_\_HTML\_TAG\_USD\_4\_\_\_- itemGenerator每次迭代只能并且必须生成一个子组件。 \_\_\_HTML\_TAG\_USD\_5\_\_\_- itemGenerator中可以使用if语句，但是必须保证if语句每个分支都会创建一个相同类型的子组件。  |
| keyGenerator | (item: any, index: number) =&gt; string | 否 | 键值生成函数，用于给数据源中的每一个数据项生成唯一且固定的键值。修改数据源中的一个数据项若不影响其生成的键值，则对应组件不会被更新，否则对应组件就会被重建更新。 \_\_\_INLINE\_CODE\_USD\_0\_\_\_参数是可选的，但是，为了使开发框架能够更好地识别数组更改并正确更新组件，建议提供。 \_\_\_HTML\_TAG\_USD\_4\_\_\_默认使用框架内置的键值生成函数（详见下方说明）。 \_\_\_HTML\_TAG\_USD\_5\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_6\_\_\_- item是当前数据项（可选），index是数据项索引值（可选）。 \_\_\_HTML\_TAG\_USD\_7\_\_\_- 建议item的数据类型与数据源的数据类型保持一致，否则，当keyGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 \_\_\_HTML\_TAG\_USD\_8\_\_\_- \_\_\_INLINE\_CODE\_USD\_1\_\_\_缺省时，使用默认的键值生成函数，即 \_\_\_INLINE\_CODE\_USD\_2\_\_\_，生成键值仅受索引值index影响（viewId在编译器转换过程中 生成，同一个LazyForEach组件内的viewId一致）。 \_\_\_HTML\_TAG\_USD\_9\_\_\_- 为保证\_\_\_INLINE\_CODE\_USD\_3\_\_\_正确、高效地更新子组件，避免渲染结果异常、渲染效率降低等问题，键值应满足以下条件。 \_\_\_HTML\_TAG\_USD\_10\_\_\_1. 键值具有唯一性，每个数据项对应的键值互不相同。 \_\_\_HTML\_TAG\_USD\_11\_\_\_2. 键值具有一致性，数据项不变时对应的键值也不变。  |

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
    options?: LazyForEachOptions
  )
```

LazyForEach从提供的数据源中按需迭代数据，并在每次迭代过程中创建相应的组件。当在滚动容器中使用了LazyForEach，框架会根据滚动容器可视区域按需创建组件，当组件滑出可视区域外时，框架会进行组件销毁回收以降低内存占 用。 > **说明** > > 从API版本26.0.0开始，LazyForEach支持传入[LazyForEachOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，用于使能自定义组件冻结和配置内存优化策略、资源释放策略。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | LazyForEach数据源，需要开发者实现相关接口。  |
| itemGenerator | (item: any, index: number) =&gt; void | 是 | 子组件生成函数，为数组中的每一个数据项创建一个子组件。 \_\_\_HTML\_TAG\_USD\_0\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_1\_\_\_- item是当前数据项（可选），index是数据项索引值（可选）。 \_\_\_HTML\_TAG\_USD\_2\_\_\_- 建议item的数据类型与数据源的数据类型保持一致，否则，当itemGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 \_\_\_HTML\_TAG\_USD\_3\_\_\_- itemGenerator的函数体必须使用大括号{...}。 \_\_\_HTML\_TAG\_USD\_4\_\_\_- itemGenerator每次迭代只能并且必须生成一个子组件。 \_\_\_HTML\_TAG\_USD\_5\_\_\_- itemGenerator中可以使用if语句，但是必须保证if语句每个分支都会创建一个相同类型的子组件。  |
| keyGenerator | (item: any, index: number) =&gt; string | 否 | 键值生成函数，用于给数据源中的每一个数据项生成唯一且固定的键值。修改数据源中的一个数据项若不影响其生成的键值，则对应组件不会被更新，否则对应组件就会被重建更 新。\_\_\_INLINE\_CODE\_USD\_0\_\_\_参数是可选的，但是，为了使开发框架能够更好地识别数组更改并正确更新组件，建议提供。 \_\_\_HTML\_TAG\_USD\_4\_\_\_默认使用框架内置的键值生成函数（详见下方说明）。 \_\_\_HTML\_TAG\_USD\_5\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_6\_\_\_- item是当前数据项（可选），index是数据项索引值（可选）。 \_\_\_HTML\_TAG\_USD\_7\_\_\_- 建议item的数据类型与数据源的数据类型保持一致，否则，当keyGenerator中存在与数据类型强相关的操作时，会导致子组件无法正常渲染，甚至运行时崩溃。 \_\_\_HTML\_TAG\_USD\_8\_\_\_- \_\_\_INLINE\_CODE\_USD\_1\_\_\_缺省时，使用默认的键值生成函数，即 \_\_\_INLINE\_CODE\_USD\_2\_\_\_，生成键值仅受索引值index影响（viewId在编译器转换过程中 生成，同一个LazyForEach组件内的viewId一致）。 \_\_\_HTML\_TAG\_USD\_9\_\_\_- 为保证\_\_\_INLINE\_CODE\_USD\_3\_\_\_正确、高效地更新子组件，避免渲染结果异常、渲染效率降低等问题，键值应满足以下条件。 \_\_\_HTML\_TAG\_USD\_10\_\_\_1. 键值具有唯一性，每个数据项对应的键值互不相同。 \_\_\_HTML\_TAG\_USD\_11\_\_\_2. 键值具有一致性，数据项不变时对应的键值也不变。  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 开发者配置项，用于使能自定义组件冻结和配置内存优化策略、资源释放策略。使用此配置项时，必须设置键值生成函数，否则将编译失败。不传入时使用默认配置（ 自定义组件冻结模式默认为AUTO，资源释放策略默认为BATCH，内存优化策略默认为DEFAULT）。  |

## 汇总

