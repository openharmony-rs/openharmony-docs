# LoadingProgressConfiguration

```TypeScript
declare interface LoadingProgressConfiguration extends CommonConfiguration<LoadingProgressConfiguration>
```

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** LoadingProgressConfiguration extends CommonConfiguration<LoadingProgressConfiguration>

**Since:** 12

<!--Device-unnamed-declare interface LoadingProgressConfiguration extends CommonConfiguration<LoadingProgressConfiguration>--><!--Device-unnamed-declare interface LoadingProgressConfiguration extends CommonConfiguration<LoadingProgressConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableLoading

```TypeScript
enableLoading: boolean
```

Whether to display the LoadingProgress animation.

Default value: true, where true means to display the LoadingProgress animation and false means not to display the LoadingProgress animation.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LoadingProgressConfiguration-enableLoading: boolean--><!--Device-LoadingProgressConfiguration-enableLoading: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
