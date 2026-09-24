# ContentModifier

```TypeScript
declare interface ContentModifier<T>
```

Defines the content modifier.

@interface ContentModifier

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## applyContent

```TypeScript
applyContent(): WrappedBuilder<[T]>
```

Defining applyContent function.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [WrappedBuilder](arkts-arkui-common-comp-wrappedbuilder-c.md)&lt;[T]&gt; | Component attribute class, which is used to distinguish different information required by different components after content areas are customized, for example, ButtonConfiguration for the Button component and CheckBoxConfiguration of the Checkbox component. |
