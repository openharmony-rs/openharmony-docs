# SafeAreaInsetOptions (System API)

```TypeScript
declare interface SafeAreaInsetOptions
```

Defines the complete inset configuration for all four edges of a component.

**Since:** 26.1.0

<!--Device-unnamed-declare interface SafeAreaInsetOptions--><!--Device-unnamed-declare interface SafeAreaInsetOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bottom

```TypeScript
bottom?: SafeAreaInsetEdgeConfig
```

Configuration of the content attached to the physical bottom edge. Default value: `undefined`, which means no content is attached to this edge. Omitting this edge or passing `undefined`, `null`, or an invalid edge configuration clears its previous content without affecting other valid edges.

**Type:** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetOptions-bottom?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-bottom?: SafeAreaInsetEdgeConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## end

```TypeScript
end?: SafeAreaInsetEdgeConfig
```

Configuration of the content attached to the logical end edge: right in a left-to-right layout and left in a right-to-left layout. Default value: `undefined`, which means no content is attached to this edge. Omitting this edge or passing `undefined`, `null`, or an invalid edge configuration clears its previous content without affecting other valid edges.

**Type:** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetOptions-end?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-end?: SafeAreaInsetEdgeConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## start

```TypeScript
start?: SafeAreaInsetEdgeConfig
```

Configuration of the content attached to the logical start edge: left in a left-to-right layout and right in a right-to-left layout. Default value: `undefined`, which means no content is attached to this edge. Omitting this edge or passing `undefined`, `null`, or an invalid edge configuration clears its previous content without affecting other valid edges.

**Type:** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetOptions-start?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-start?: SafeAreaInsetEdgeConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## top

```TypeScript
top?: SafeAreaInsetEdgeConfig
```

Configuration of the content attached to the physical top edge. Default value: `undefined`, which means no content is attached to this edge. Omitting this edge or passing `undefined`, `null`, or an invalid edge configuration clears its previous content without affecting other valid edges.

**Type:** [SafeAreaInsetEdgeConfig](arkts-arkui-common-comp-safeareainsetedgeconfig-i-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetOptions-top?: SafeAreaInsetEdgeConfig--><!--Device-SafeAreaInsetOptions-top?: SafeAreaInsetEdgeConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
