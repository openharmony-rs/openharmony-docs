# LoadingProgressConfiguration

```TypeScript
declare interface LoadingProgressConfiguration extends CommonConfiguration<LoadingProgressConfiguration>
```

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** LoadingProgressConfiguration extends CommonConfiguration<LoadingProgressConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableLoading

```TypeScript
enableLoading: boolean
```

Whether to show the loading animation.

Default value: **true**. **true**: Show the loading animation. **false**: Do not show the loading animation.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
