# Filter

多条件筛选，帮助用户在大量信息中找到所需内容，应结合具体场景选择合适筛选方式。多条件筛选控件由筛选器与悬浮条构成，悬浮条可下拉展示悬浮筛选器。筛选器样式可分为多行可折叠类型与多行列表类型，并可以在筛选器最后一行附加快捷筛选器。
> **说明：**  
>  
> - 该组件仅可在Stage模型下使用。  
>  
> - 如果Filter设置[通用属性](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)和[通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，编译工具链会额外生  
> 成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Filter本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Filter设置通用属性和通用事件。

**起始版本：** 10

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct Filter--><!--Device-unnamed-export declare struct Filter-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { FilterType, Filter, FilterParams, FilterResult } from '@kit.ArkUI';
```

## additionFilters

```TypeScript
@Prop additionFilters?: FilterParams
```

附加快捷筛选项。如果不设置，则不显示附加快捷筛选项。

**类型：** FilterParams

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-@Prop additionFilters?: FilterParams--><!--Device-Filter-@Prop additionFilters?: FilterParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## container

```TypeScript
@BuilderParam container: () => void
```

筛选结果展示区域自定义内容，通过尾随闭包形式传入。

**类型：** () =&gt; void

**起始版本：** 10

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-@BuilderParam container: () => void--><!--Device-Filter-@BuilderParam container: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## filterType

```TypeScript
@Prop filterType?: FilterType
```

筛选器的样式类型。

默认值：FilterType.LIST_FILTER

**类型：** FilterType

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-@Prop filterType?: FilterType--><!--Device-Filter-@Prop filterType?: FilterType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiFilters

```TypeScript
@Prop multiFilters: Array<FilterParams>
```

多条件筛选列表。

**类型：** Array&lt;FilterParams&gt;

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-@Prop multiFilters: Array<FilterParams>--><!--Device-Filter-@Prop multiFilters: Array<FilterParams>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFilterChanged

```TypeScript
onFilterChanged: (filterResults: Array<FilterResult>) => void
```

用户点击后的回调事件。回调函数的参数为选中的筛选项结果列表。

**类型：** (filterResults: Array&lt;FilterResult&gt;) =&gt; void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Filter-onFilterChanged: (filterResults: Array<FilterResult>) => void--><!--Device-Filter-onFilterChanged: (filterResults: Array<FilterResult>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

