# ComponentOptions

```TypeScript
declare interface ComponentOptions
```

Defines parameters of a custom component, which is used to configure whether to support component freezing and the global reuse pool. They apply to scenarios where the performance of custom components needs to be optimized and the component reuse efficiency needs to be improved.

**Since:** 11

<!--Device-unnamed-declare interface ComponentOptions--><!--Device-unnamed-declare interface ComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## freezeWhenInactive

```TypeScript
freezeWhenInactive : boolean
```

Whether the custom component supports component freezing. The value **true** enables component freezing, and **false** disables it. If **ComponentOptions** is not specified, **false** is used as the default value of **freezeWhenInactive**. <br>Since API version 11, this parameter can be used to configure component freezing for [\@Component](../../../ui/state-management/arkts-create-custom-components.md). For details, see [Freezing a Custom Component (V1)](../../../ui/state-management/arkts-custom-components-freeze.md). <br>Since API version 12, this parameter can be used to configure component freezing for [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md). For details, see [Freezing a Custom Component (V2)](../../../ui/state-management/arkts-custom-components-freezeV2.md).

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-ComponentOptions-freezeWhenInactive : boolean--><!--Device-ComponentOptions-freezeWhenInactive : boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## poolAccepts

```TypeScript
poolAccepts?: Function[]
```

List of custom component names that the global reuse pool can accept (that is, components allowed to be reused). When **reusePool** is set, the system caches the matching reusable components into the global reuse pool based on the component names listed in **poolAccepts** for subsequent reuse. When **reusePool** is set, **poolAccepts** must be a non-empty array. Setting **poolAccepts** alone does not enable global reuse. When neither **poolAccepts** nor **reusePool** is assigned, global reuse does not take effect.

**Type:** Function[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-ComponentOptions-poolAccepts?: Function[]--><!--Device-ComponentOptions-poolAccepts?: Function[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reusePool

```TypeScript
reusePool?: ReusePoolOwnership
```

Type of the global reuse pool on a custom component. This is applicable to scenarios where an app has multiple reusable custom components of the same type and needs to share or isolate reuse resources between component instances to improve reuse efficiency. If this parameter is not passed, the global reuse pool does not take effect. **reusePool** must be used together with **poolAccepts**. When **reusePool** is set, **poolAccepts** must be a non-empty array; otherwise, global reuse does not take effect.

**Type:** [ReusePoolOwnership](arkts-arkui-common-comp-reusepoolownership-t.md)

**Default:** perInstance

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-ComponentOptions-reusePool?: ReusePoolOwnership--><!--Device-ComponentOptions-reusePool?: ReusePoolOwnership-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
