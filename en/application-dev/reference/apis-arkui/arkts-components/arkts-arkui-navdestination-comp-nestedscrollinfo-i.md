# NestedScrollInfo

```TypeScript
declare interface NestedScrollInfo
```

Provides the information about the nested scrollable containers.

**Since:** 14

<!--Device-unnamed-declare interface NestedScrollInfo--><!--Device-unnamed-declare interface NestedScrollInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## child

```TypeScript
child: Scroller
```

Controller of the scrollable container nested within the target scrollable container. This scrollable container is a child component of the target scrollable container.

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-NestedScrollInfo-child: Scroller--><!--Device-NestedScrollInfo-child: Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## parent

```TypeScript
parent: Scroller
```

Controller of the target scrollable container.

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-NestedScrollInfo-parent: Scroller--><!--Device-NestedScrollInfo-parent: Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
