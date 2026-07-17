# DataChangeListener

数据变化监听器。

> **说明：**  
>  
> DataChangeListener除onDatasetChange以外的方法中，当参数包含index且值为负数时，会默认用0来替换。onDatasetChange中，当单个DataOperation参数包含index且值在数据源  
> 索引范围之外（DataAddOperation中index可以等于数据源长度），则对应DataOperation不会生效。

**起始版本：** 7

<!--Device-unnamed-declare interface DataChangeListener--><!--Device-unnamed-declare interface DataChangeListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDataAdd

```TypeScript
onDataAdd(index: number): void
```

通知组件index的位置有数据添加。添加数据完成后调用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeListener-onDataAdd(index: number): void--><!--Device-DataChangeListener-onDataAdd(index: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 数据添加位置的索引值。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataAdded

```TypeScript
onDataAdded(index: number): void
```

通知组件index的位置有数据添加。添加数据完成后调用。

> **说明：**

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [onDataAdd](arkts-arkui-lazy-for-each-datachangelistener-i.md#ondataadd-1)

<!--Device-DataChangeListener-onDataAdded(index: number): void--><!--Device-DataChangeListener-onDataAdded(index: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 数据添加位置的索引值。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataChange

```TypeScript
onDataChange(index: number): void
```

通知组件index的位置有数据有变化。改变数据完成后调用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeListener-onDataChange(index: number): void--><!--Device-DataChangeListener-onDataChange(index: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 数据变化位置的索引值。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataChanged

```TypeScript
onDataChanged(index: number): void
```

通知组件index的位置有数据变化。改变数据完成后调用。

> **说明：**

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [onDataChange](arkts-arkui-lazy-for-each-datachangelistener-i.md#ondatachange-1)

<!--Device-DataChangeListener-onDataChanged(index: number): void--><!--Device-DataChangeListener-onDataChanged(index: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 数据变化位置的索引值。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataDelete

```TypeScript
onDataDelete(index: number): void
```

通知组件删除index位置的数据并刷新LazyForEach的展示内容。删除数据完成后调用。

> **说明：**  
>  
> 需要保证dataSource中的对应数据已经在调用onDataDelete前删除，否则页面渲染将出现未定义的行为。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeListener-onDataDelete(index: number): void--><!--Device-DataChangeListener-onDataDelete(index: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 数据删除位置的索引值。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataDeleted

```TypeScript
onDataDeleted(index: number): void
```

通知组件删除index位置的数据并刷新LazyForEach的展示内容。删除数据完成后调用。

> **说明：**

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [onDataDelete](arkts-arkui-lazy-for-each-datachangelistener-i.md#ondatadelete-1)

<!--Device-DataChangeListener-onDataDeleted(index: number): void--><!--Device-DataChangeListener-onDataDeleted(index: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 数据删除位置的索引值。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataMove

```TypeScript
onDataMove(from: number, to: number): void
```

通知组件数据有移动。将from和to位置的数据进行交换。数据移动起始位置与数据移动目标位置交换完成后调用。

> **说明：**  
>  
> 数据移动前后键值要保持不变，如果键值有变化，应使用删除数据和新增数据接口。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeListener-onDataMove(from: number, to: number): void--><!--Device-DataChangeListener-onDataMove(from: number, to: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | number | 是 | 数据移动起始位置。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |
| to | number | 是 | 数据移动目标位置。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataMoved

```TypeScript
onDataMoved(from: number, to: number): void
```

通知组件数据有移动。将from和to位置的数据进行交换。

> **说明：**  
>  
> -  
>  
> - 数据移动前后键值要保持不变，如果键值有变化，应使用删除数据和新增数据接口。数据移动起始位置与数据移动目标位置交换完成后调用。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [onDataMove](arkts-arkui-lazy-for-each-datachangelistener-i.md#ondatamove-1)

<!--Device-DataChangeListener-onDataMoved(from: number, to: number): void--><!--Device-DataChangeListener-onDataMoved(from: number, to: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | number | 是 | 数据移动起始位置。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |
| to | number | 是 | 数据移动目标位置。取值范围是[0, 数据源长度-1]。<br/>小于0时取值为0，大于数据源长度-1时取值为数据源长度-1。 |

## onDataReloaded

```TypeScript
onDataReloaded(): void
```

通知组件重新加载所有数据。键值没有变化的数据项会使用原先的子组件，键值发生变化的会重建子组件。重新加载数据完成后调用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeListener-onDataReloaded(): void--><!--Device-DataChangeListener-onDataReloaded(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDatasetChange

```TypeScript
onDatasetChange(dataOperations: DataOperation[]): void
```

进行批量的数据处理后，调用onDatasetChange接口通知组件按照dataOperations刷新组件。

> **说明：**  
>  
> onDatasetChange接口不能与其他DataChangeListener的更新接口混用。例如，在同一个LazyForEach中，调用过onDataAdd接口后，不能再调用onDatasetChange接口；反之，调用过  
> onDatasetChange接口后，也不能调用onDataAdd等其他更新接口。页面中不同LazyForEach之间互不影响。在同一个onDatasetChange批量处理数据时，如果多个DataOperation操作同一个  
> index，只有第一个DataOperation生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeListener-onDatasetChange(dataOperations: DataOperation[]): void--><!--Device-DataChangeListener-onDatasetChange(dataOperations: DataOperation[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataOperations | [DataOperation](arkts-arkui-dataoperation-t.md)[] | 是 | 一次处理数据的操作。 |

