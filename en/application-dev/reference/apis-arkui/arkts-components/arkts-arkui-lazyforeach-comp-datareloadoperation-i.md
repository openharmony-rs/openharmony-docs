# DataReloadOperation

```TypeScript
interface DataReloadOperation
```

Reloads all data operations and configures whether to allow reuse of old child components during the update. When **onDatasetChange** contains a **DataOperationType.RELOAD** operation, all other operations become invalid, and the framework calls **keyGenerator** to compare keys.

When reuse of old child components during the update is allowed and used together with [@Reusable](../../../ui/state-management/arkts-reusable.md)/[@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md), components in the reuse pool are used first. If no reusable component is available in the reuse pool but a reusable component exists among the old child components of **LazyForEach**, that component will be recycled and reused as a new child component. If no reusable component exists among the old child components of **LazyForEach** either, a new child component will be created.

When reuse of old child components during the update is allowed but **@Reusable/@ReusableV2** is not used, data items whose keys do not change will use the original child components, while those whose keys change will have their child components rebuilt.

When reuse of old child components during the update is not allowed, data items whose keys do not change will use the original child components. For data items whose keys change, if **@Reusable/@ReusableV2** is used and a component is available in the reuse pool, the old component will be reused; otherwise, a new child component will be created.

**Since:** 12

<!--Device-unnamed-interface DataReloadOperation--><!--Device-unnamed-interface DataReloadOperation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reuseImmediately

```TypeScript
reuseImmediately?: boolean
```

Whether to reuse the old child components during the update. **true**: allows reusing the old child components during the update. **false**: does not allow reusing the old child components during the update. Default value: **false**. When the value is **undefined** or **null**, the default value is used.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DataReloadOperation-reuseImmediately?: boolean--><!--Device-DataReloadOperation-reuseImmediately?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.RELOAD
```

Type for reloading all data.

**Type:** [DataOperationType.RELOAD](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataReloadOperation-type: DataOperationType.RELOAD--><!--Device-DataReloadOperation-type: DataOperationType.RELOAD-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
