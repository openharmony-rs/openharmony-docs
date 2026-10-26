# SafeAreaInsetEdgeConfig (System API)

```TypeScript
declare interface SafeAreaInsetEdgeConfig
```

Defines custom content and layout settings for one safe area inset edge.

**Since:** 26.1.0

<!--Device-unnamed-declare interface SafeAreaInsetEdgeConfig--><!--Device-unnamed-declare interface SafeAreaInsetEdgeConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## alignment

```TypeScript
alignment?: SafeAreaInsetAlignment
```

Alignment of the content along the attachment edge. Default value: `SafeAreaInsetAlignment.CENTER`. An omitted or invalid value falls back to `SafeAreaInsetAlignment.CENTER` without clearing valid content.

**Type:** [SafeAreaInsetAlignment](arkts-arkui-common-comp-safeareainsetalignment-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetEdgeConfig-alignment?: SafeAreaInsetAlignment--><!--Device-SafeAreaInsetEdgeConfig-alignment?: SafeAreaInsetAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## content

```TypeScript
content: CustomBuilder
```

Required builder for the content attached to this edge. An empty build result clears this edge without affecting other valid edges. The space reserved on this edge equals the measured content size perpendicular to the edge plus `spacing`.

Each edge builder must produce one root component, either a built-in or custom component. Wrap multiple components in a single container. Results of builders with multiple roots are not guaranteed.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetEdgeConfig-content: CustomBuilder--><!--Device-SafeAreaInsetEdgeConfig-content: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## spacing

```TypeScript
spacing?: LengthMetrics
```

Gap between the inset content and the component content, measured inward from the attachment edge. Supported units are vp, px, fp, and lpx. The value must be finite and non-negative. Percentage values and resource values are not supported. Default value: `0vp`. An omitted or invalid value falls back to `0vp` without clearing valid content. The gap is added after measuring the content and is not deducted from its measurement space.

**Type:** LengthMetrics

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetEdgeConfig-spacing?: LengthMetrics--><!--Device-SafeAreaInsetEdgeConfig-spacing?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
