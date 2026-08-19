# BasicPrefetcher

一种IPrefetcher的基础实现。 此prefetcher提供了一种智能预加载算法，可以根据显示区域的实时变化以及预加载耗时的变化来确定预加载范围并加载数据项，并且可以根据用户的滚动操作来取消相应数据项的预加载请求。

**继承/实现关系：** BasicPrefetcher implements IPrefetcher<T>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class BasicPrefetcher--><!--Device-unnamed-export declare class BasicPrefetcher-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(dataSource?: IDataSourcePrefetching<T>)
```

构建一个基础的prefetcher，并在构建时可以按需设置数据源。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BasicPrefetcher-constructor(dataSource?: IDataSourcePrefetching<T>)--><!--Device-BasicPrefetcher-constructor(dataSource?: IDataSourcePrefetching<T>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](arkts-na-arkui-prefetcher-idatasourceprefetching-i.md)&lt;T&gt; | 否 | 支持预加载的数据源。 |

## setDataSource

```TypeScript
setDataSource(dataSource: IDataSourcePrefetching<T>): void
```

设置prefetcher对象的数据源。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BasicPrefetcher-setDataSource(dataSource: IDataSourcePrefetching<T>): void--><!--Device-BasicPrefetcher-setDataSource(dataSource: IDataSourcePrefetching<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | [IDataSourcePrefetching](arkts-na-arkui-prefetcher-idatasourceprefetching-i.md)&lt;T&gt; | 是 | 支持预加载的数据源。 |

## visibleAreaChanged

```TypeScript
visibleAreaChanged(minVisible: int, maxVisible: int): void
```

通知prefetcher屏幕显示范围发生变化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BasicPrefetcher-visibleAreaChanged(minVisible: int, maxVisible: int): void--><!--Device-BasicPrefetcher-visibleAreaChanged(minVisible: int, maxVisible: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minVisible | int | 是 | 显示范围内第一个元素的序号。 |
| maxVisible | int | 是 | 显示范围内最后一个元素的序号。 |

