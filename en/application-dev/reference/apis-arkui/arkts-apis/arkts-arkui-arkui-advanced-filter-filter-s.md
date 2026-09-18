# Filter

Declare Filter.The Filter is used in scenarios where multi-dimensional filtering is required.

**Since:** 22

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';
```

## container

```TypeScript
container: () => void
```

Container in the user-defined filtering result display area.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFilterChanged

```TypeScript
onFilterChanged: (filterResults: Array<FilterResult>) => void
```

FilterParams, Callback method after a user clicks a filter item.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filterResults | Array&lt;[FilterResult](arkts-arkui-arkui-advanced-filter-filterresult-c.md)&gt; | Yes |  |

## additionFilters

```TypeScript
additionFilters?: FilterParams
```

FilterParams, Additional filter item parameter. The filter item name is displayed and can be deselected.

**Type:** [FilterParams](arkts-arkui-arkui-advanced-filter-filterparams-c.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## filterType

```TypeScript
filterType?: FilterType
```

FilterType, Filter display style type.

**Type:** [FilterType](arkts-arkui-arkui-advanced-filter-filtertype-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiFilters

```TypeScript
multiFilters: Array<FilterParams>
```

Multi-dimensional filtering parameters.

**Type:** Array&lt;[FilterParams](arkts-arkui-arkui-advanced-filter-filterparams-c.md)&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
