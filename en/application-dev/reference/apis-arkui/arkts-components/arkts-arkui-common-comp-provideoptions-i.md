# ProvideOptions

```TypeScript
declare interface ProvideOptions
```

Options of the **@Provide** decorator. You can use **allowOverride** to override the alias of an @Provide decorated variable with the same name in the same component tree. It is suitable for scenarios where a child component needs to override the alias of the **@Provide** decorated variable with the same name in the parent component, improving the flexibility of cross-level state management. For details, see [Support for the allowOverride Parameter](../../../ui/state-management/arkts-provide-and-consume.md).

**Since:** 11

<!--Device-unnamed-declare interface ProvideOptions--><!--Device-unnamed-declare interface ProvideOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowOverride

```TypeScript
allowOverride?: string
```

Alias of an **@Provide** decorated variable that can be overridden. In detail, you can use this property to override the alias of an @Provide decorated variable with the same name in the same component tree. <br> If the property is not specified, the alias of an **@Provide** decorated variable cannot be overridden. If you define an **@Provide** decorated variable with the same name without setting **allowOverride**, an error will be reported at runtime.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-ProvideOptions-allowOverride?: string--><!--Device-ProvideOptions-allowOverride?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
