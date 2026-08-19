# DataChangeListener

数据变化监听器。 > **说明：** > > DataChangeListener除onDatasetChange以外的方法中，当参数包含index且值为负数时，会默认用0来替换。onDatasetChange中，当单个DataOperation参数包含index且值在数据源 > 索引范围之外（DataAddOperation中index可以等于数据源长度），则对应DataOperation不会生效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface DataChangeListener--><!--Device-unnamed-export interface DataChangeListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDataAdd

```TypeScript
onDataAdd(index: int): void
```

通知组件index的位置有数据添加。添加数据完成后调用

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeListener-onDataAdd(index: int): void--><!--Device-DataChangeListener-onDataAdd(index: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |

## onDataChange

```TypeScript
onDataChange(index: int): void
```

通知组件index的位置有数据有变化。改变数据完成后调用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeListener-onDataChange(index: int): void--><!--Device-DataChangeListener-onDataChange(index: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |

## onDataDelete

```TypeScript
onDataDelete(index: int): void
```

通知组件删除index位置的数据并重新加载LazyForEach的展示内容。删除数据完成后调用。 > **说明：** > > 需要保证dataSource中的对应数据已经在调用onDataDelete前删除，否则页面渲染将出现未定义的行为。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeListener-onDataDelete(index: int): void--><!--Device-DataChangeListener-onDataDelete(index: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |

## onDataMove

```TypeScript
onDataMove(from: int, to: int): void
```

通知组件数据有移动。将from和to位置的数据进行交换。数据移动起始位置与数据移动目标位置交换完成后调用。 > **说明：** > > 数据移动前后键值要保持不变，如果键值有变化，应使用删除数据和新增数据接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeListener-onDataMove(from: int, to: int): void--><!--Device-DataChangeListener-onDataMove(from: int, to: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | int | 是 |  |
| to | int | 是 |  |

## onDataReloaded

```TypeScript
onDataReloaded(): void
```

通知组件重新加载所有数据。键值没有变化的数据项会使用原先的子组件，键值发生变化的会重建子组件。重新加载数据完成后调用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeListener-onDataReloaded(): void--><!--Device-DataChangeListener-onDataReloaded(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDatasetChange

```TypeScript
onDatasetChange(dataOperations: Array<DataOperation>): void
```

批量数据处理后，调用onDatasetChange接口，通知组件按照dataOperations刷新。 > **说明：** > > onDatasetChange接口不能与其他DataChangeListener的更新接口混用。如在同一个LazyForEach中，调用过onDataAdd接口后，不能再调用onDatasetChange接口；反之，调用过 > onDatasetChange接口后，也不能调用onDataAdd等其他更新接口。页面中不同LazyForEach之间互不影响。 使用`onDatasetChange()`进行批量数据修改时，`DataOperation`每一个数组项需要转换为对应的类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeListener-onDatasetChange(dataOperations: Array<DataOperation>): void--><!--Device-DataChangeListener-onDatasetChange(dataOperations: Array<DataOperation>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataOperations | Array&lt;[DataOperation](arkts-na-dataoperation-t.md)&gt; | 是 |  |

