# Filter

```TypeScript
export declare struct Filter
```

The advanced filter component allows users to filter data with multiple criteria combined. It consists of a floating bar and filters therein. The floating bar can be expanded to reveal the filters, which come in a multi-line collapsible or multi-line list style. For added convenience, you can append an additional quick filter.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **Filter** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **Filter** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **Filter** component.

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
