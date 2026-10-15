# StateStyles

```TypeScript
declare interface StateStyles
```

State-specific styles for the component.

> **NOTE:** 
> 
> - The selected state style depends on the value of the component's selected attribute, which can be changed through a click event or **$$**.
> 
> - When both **clicked** and **pressed** are used on the same component, only the last registered state takes effect.

**Since:** 8

<!--Device-unnamed-declare interface StateStyles--><!--Device-unnamed-declare interface StateStyles-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clicked

```TypeScript
clicked?: any
```

Style of the component in the clicked state.

**Type:** any

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StateStyles-clicked?: any--><!--Device-StateStyles-clicked?: any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disabled

```TypeScript
disabled?: any
```

Style of the component in the disabled state.

**Type:** any

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StateStyles-disabled?: any--><!--Device-StateStyles-disabled?: any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## focused

```TypeScript
focused?: any
```

Style of the component in the focused state.

**Type:** any

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StateStyles-focused?: any--><!--Device-StateStyles-focused?: any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hovered

```TypeScript
hovered?: object
```

Style of the component in the hovered state.

**Type:** object

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-StateStyles-hovered?: object--><!--Device-StateStyles-hovered?: object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
normal?: any
```

Style of the component when being stateless.

**Type:** any

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StateStyles-normal?: any--><!--Device-StateStyles-normal?: any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pressed

```TypeScript
pressed?: any
```

Style of the component in the pressed state.

**Type:** any

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-StateStyles-pressed?: any--><!--Device-StateStyles-pressed?: any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: object
```

Style of the component in the selected state.

**Type:** object

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-StateStyles-selected?: object--><!--Device-StateStyles-selected?: object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
