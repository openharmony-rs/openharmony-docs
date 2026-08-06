# IPrefetcher

该接口用于提供预加载操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface IPrefetcher<T>--><!--Device-unnamed-export interface IPrefetcher<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setDataSource

```TypeScript
setDataSource(dataSource: IDataSourcePrefetching<T>): void
```

设置prefetcher对象的数据源。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IPrefetcher-setDataSource(dataSource: IDataSourcePrefetching<T>): void--><!--Device-IPrefetcher-setDataSource(dataSource: IDataSourcePrefetching<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 支持预加载的数据源。 |

## visibleAreaChanged

```TypeScript
visibleAreaChanged(minVisible: int, maxVisible: int): void
```

通知prefetcher屏幕显示范围发生变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IPrefetcher-visibleAreaChanged(minVisible: int, maxVisible: int): void--><!--Device-IPrefetcher-visibleAreaChanged(minVisible: int, maxVisible: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minVisible | int | 是 | 显示范围内第一个元素的序号。 |
| maxVisible | int | 是 | 显示范围内最后一个元素的序号。 |

