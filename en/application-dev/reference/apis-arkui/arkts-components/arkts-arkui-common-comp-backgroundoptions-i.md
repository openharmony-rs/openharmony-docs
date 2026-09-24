# BackgroundOptions

```TypeScript
declare interface BackgroundOptions
```

Defines background options.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## align

```TypeScript
align?: Alignment
```

Set the alignment of the custom background and component.

Anonymous Object Rectification.

**Type:** [Alignment](../arkts-apis/arkts-arkui-alignment-e.md)

**Default:** Alignment.Center

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ignoresLayoutSafeAreaEdges

```TypeScript
ignoresLayoutSafeAreaEdges?: Array<LayoutSafeAreaEdge>
```

The set of edges for which to ignore layout safe area. To respect safe area insets on all edges, explicitly pass empty edge set.

**Type:** Array&lt;[LayoutSafeAreaEdge](arkts-arkui-common-comp-layoutsafeareaedge-e.md)&gt;

**Default:** The default value is LayoutSafeAreaEdge.ALL when background is ResourceColor, otherwise it is an empty array [].

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
