# Filter

```TypeScript
export declare struct Filter
```

Declare Filter.The Filter is used in scenarios where multi-dimensional filtering is required.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct Filter--><!--Device-unnamed-export declare struct Filter-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';
```

## container

```TypeScript
container: () => void
```

Custom content of the filtering result display area, which is passed in a trailing closure.

**Since:** 10

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Filter-container: () => void--><!--Device-Filter-container: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFilterChanged

```TypeScript
onFilterChanged: (filterResults: Array<FilterResult>) => void
```

Callback invoked when the filter criteria are changed. The input parameter is the list of selected filter criteria.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Filter-onFilterChanged: (filterResults: Array<FilterResult>) => void--><!--Device-Filter-onFilterChanged: (filterResults: Array<FilterResult>) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filterResults | Array&lt;[FilterResult](arkts-arkui-arkui-advanced-filter-filterresult-c.md)&gt; | Yes |  |

## additionFilters

```TypeScript
additionFilters?: FilterParams
```

Additional quick filter criteria. If this parameter is not specified, the additional quick filter criteria are not displayed.

**Type:** [FilterParams](arkts-arkui-arkui-advanced-filter-filterparams-c.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Filter-additionFilters?: FilterParams--><!--Device-Filter-additionFilters?: FilterParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## filterType

```TypeScript
filterType?: FilterType
```

Filter type.

Default value: **FilterType.LIST_FILTER**.

**Type:** [FilterType](arkts-arkui-arkui-advanced-filter-filtertype-e.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Filter-filterType?: FilterType--><!--Device-Filter-filterType?: FilterType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiFilters

```TypeScript
multiFilters: Array<FilterParams>
```

List of filter criteria.

**Type:** Array&lt;[FilterParams](arkts-arkui-arkui-advanced-filter-filterparams-c.md)&gt;

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Filter-multiFilters: Array<FilterParams>--><!--Device-Filter-multiFilters: Array<FilterParams>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
