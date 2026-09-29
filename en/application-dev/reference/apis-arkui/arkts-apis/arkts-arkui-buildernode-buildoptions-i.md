# BuildOptions

```TypeScript
export interface BuildOptions
```

Defines the optional build options.

**Since:** 12

<!--Device-unnamed-export interface BuildOptions--><!--Device-unnamed-export interface BuildOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableProvideConsumeCrossing

```TypeScript
enableProvideConsumeCrossing?: boolean
```

Whether two-way synchronization is supported between the [@Consume](../../../ui/state-management/arkts-provide-and-consume.md) decorated variable of the custom component of [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1) inside the BuilderNode and the [@Provide](../../../ui/state-management/arkts-provide-and-consume.md) decorated variable outside the BuilderNode, and whether two-way synchronization is supported between the [@Consumer](../../../ui/state-management/arkts-new-provider-and-consumer.md) decorated variable of the custom component of [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2) inside the BuilderNode and the [@Provider](../../../ui/state-management/arkts-new-provider-and-consumer.md) decorated variable outside the BuilderNode.

API version 20 and later versions support two-way synchronization for the custom component of state management V1. API version 23 and later versions support two-way synchronization for the custom component of state management V2.

The value **true** means that this feature is supported, and **false** means the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-BuildOptions-enableProvideConsumeCrossing?: boolean--><!--Device-BuildOptions-enableProvideConsumeCrossing?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localStorage

```TypeScript
localStorage?: LocalStorage
```

LocalStorage for the current BuilderNode. Custom components mounted under this BuilderNode will share the specified LocalStorage. If LocalStorage is also passed through a custom component's constructor, the constructor parameter takes precedence.

Default value: **null**.

**Type:** [LocalStorage](arkts-arkui-localstorage-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-BuildOptions-localStorage?: LocalStorage--><!--Device-BuildOptions-localStorage?: LocalStorage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## nestingBuilderSupported

```TypeScript
nestingBuilderSupported?: boolean
```

Whether to support nested **@Builder** within **@Builder**. **true** if supported, **false** otherwise.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BuildOptions-nestingBuilderSupported?: boolean--><!--Device-BuildOptions-nestingBuilderSupported?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
