# VirtualScrollOptions

配置懒加载模式下期望加载的数据项总数、复用能力、数据精准懒加载能力。从API版本26.0.0开始，支持配置内存优化策略。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLazyLoading

```TypeScript
onLazyLoading?(index: number): void
```

可选方法，懒加载指定索引的数据。需要开发者给定数据加载方法。

onLazyLoading方法需在懒加载场景下使用。开发者可设置自定义方法，用于向指定的数据源index中写入数据。以下为onLazyLoading的处理规则：

- Repeat读取数据源中index对应的数据之前，会先检查index处是否存在数据。
- 如果不存在数据，但开发者提供了onLazyLoading方法，Repeat将调用此方法。
- 在onLazyLoading方法中，开发者需要向Repeat指定的index中写入数据，方式如下：`arr[index] = ...`，其中`arr`表示传入Repeat的数组。不允许使用除`[]`以外的数组操作，且不允许写入
指定index以外的元素，否则系统将抛出异常。
- onLazyLoading方法执行完成后，若指定index中仍无数据，将导致当前index和后续索引对应的组件无法加载。
- 精准懒加载能力为可选配置项。当onLazyLoading缺省，并且totalCount或onTotalCount的返回值大于数据源长度时，Repeat不负责列表滚动到底部的渲染效果。
- onLazyLoading方法中应避免高耗时操作。若数据加载耗时较长，建议先在onLazyLoading方法中为此数据创建占位符，再创建异步任务加载数据。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 需要加载的数据项对应的索引。<br>取值范围：自然数。 |

## onTotalCount

```TypeScript
onTotalCount?(): number
```

可选方法，计算期望加载的数据项总数。需要开发者给定计算方法，其返回值可以不等于数据源长度（实际传入Repeat的数组的长度）。

[totalCount](arkts-arkui-virtualscrolloptions-i.md#totalcount)和onTotalCount()的返回值都表示期望加载的数据项总数。开发者可直接设置totalCount属性，给出期望加载的数据项
总数，也可以通过onTotalCount()设定自定义方法，计算期望加载的数据项总数。totalCount与onTotalCount()最多设置一个。如果均未设置，则采用默认值：数据源长度；如果同时设置，则忽略
totalCount。

onTotalCount()不同返回值的数据加载处理规则与totalCount一致，具体如下：

- onTotalCount()返回值 = 0时，不加载数据。
- 0 < onTotalCount()返回值 <= 数据源长度时，只加载区间[0, onTotalCount()返回值 - 1]索引范围内的数据。
- onTotalCount()返回值 > 数据源长度时，代表Repeat期望加载区间[0, onTotalCount()返回值 - 1]索引范围内的数据，容器组件滚动条样式根据totalCount值变化。在容器组件滚动过程中，应
用需要保证在列表即将滑动到数据源末尾时请求后续数据。开发者需要对数据请求的错误场景（如网络延迟）进行保护操作，直到数据源全部加载完成，否则列表滑动过程中会出现滚动效果异常。建议配合使用
[onLazyLoading](arkts-arkui-virtualscrolloptions-i.md#onlazyloading-1)实现数据懒加载。
- onTotalCount()返回值是非自然数时，由数据源长度取代其返回值。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 期望加载的数据项总数。<br>取值范围：自然数。 |

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: RepeatMemOptStrategy
```

Repeat的内存优化策略。该参数在创建Repeat时设定，不支持动态修改。
默认值：[DEFAULT]。

**类型：** RepeatMemOptStrategy

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reusable

```TypeScript
reusable?: boolean
```

是否开启复用功能。当Repeat的子组件为[@ReusableV2](../../../../ui/state-management/arkts-new-reusableV2.md)装饰的自定义组件时，Repeat自身的复用能力优先于

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## totalCount

```TypeScript
totalCount?: number
```

期望加载的数据项总数，可以不等于数据源长度（实际传入Repeat的数组的长度）。

取值范围：自然数。

totalCount缺省或超出取值范围时，totalCount取值为数据源长度，列表正常滚动。

totalCount = 0时，不加载数据。

0 < totalCount <= 数据源长度时，界面中只渲染区间[0, totalCount - 1]范围内的数据。

totalCount > 数据源长度时，Repeat将渲染区间[0, totalCount - 1]范围内的数据，容器组件滚动条样式根据totalCount值变化。在容器组件滚动过程中，应用需要保证在列表即将滑动到数据源末尾时请求
后续数据。开发者需要对数据请求的错误场景（如网络延迟）进行保护操作，直到数据源全部加载完成，否则列表滑动过程中会出现滚动效果异常。建议配合使用
[onLazyLoading](arkts-arkui-virtualscrolloptions-i.md#onlazyloading-1)实现数据懒加载。

除totalCount属性外，开发者也可以通过[onTotalCount](arkts-arkui-virtualscrolloptions-i.md#ontotalcount-1)方法设置自定义方法，计算期望加载的数据项总数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

