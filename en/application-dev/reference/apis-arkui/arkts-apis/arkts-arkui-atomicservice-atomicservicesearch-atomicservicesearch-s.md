# AtomicServiceSearch

```TypeScript
export declare struct AtomicServiceSearch
```

**AtomicServiceSearch** allows you to customize the default search area, customizable selection area, and function area (a maximum of two).

> **NOTE:** 
> 
> - If the **AtomicServiceSearch** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md)and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **AtomicServiceSearch** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **AtomicServiceSearch** component.

**Since:** 18

**Decorator:** @Component

<!--Device-unnamed-export declare struct AtomicServiceSearch--><!--Device-unnamed-export declare struct AtomicServiceSearch-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## controller

```TypeScript
controller?: SearchController
```

Set the Search component controller.

**Type:** [SearchController](../arkts-components/arkts-arkui-search-comp-searchcontroller-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AtomicServiceSearch-controller?: SearchController--><!--Device-AtomicServiceSearch-controller?: SearchController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operation

```TypeScript
operation?: OperationParams
```

Function settings in the selection area (right).

**Type:** [OperationParams](arkts-arkui-atomicservice-atomicservicesearch-operationparams-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AtomicServiceSearch-operation?: OperationParams--><!--Device-AtomicServiceSearch-operation?: OperationParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Indicates default prompt text displayed in the search box. The default value is Search, which supports globalization.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AtomicServiceSearch-placeholder?: ResourceStr--><!--Device-AtomicServiceSearch-placeholder?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## search

```TypeScript
search?: SearchParams
```

Events and styles supported by the search area.

**Type:** [SearchParams](arkts-arkui-atomicservice-atomicservicesearch-searchparams-i.md)

**Since:** 18

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AtomicServiceSearch-search?: SearchParams--><!--Device-AtomicServiceSearch-search?: SearchParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## select

```TypeScript
select?: SelectParams
```

Contents, events, and styles of the select area.

**Type:** [SelectParams](arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md)

**Since:** 18

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AtomicServiceSearch-select?: SelectParams--><!--Device-AtomicServiceSearch-select?: SelectParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

Sets the search text content that is currently displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-AtomicServiceSearch-value?: ResourceStr--><!--Device-AtomicServiceSearch-value?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
