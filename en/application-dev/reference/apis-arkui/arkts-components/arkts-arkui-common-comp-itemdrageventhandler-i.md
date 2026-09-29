# ItemDragEventHandler

```TypeScript
declare interface ItemDragEventHandler
```

Defines callbacks for drag events on a data source, allowing you to respond to different drag operations.

**Since:** 20

<!--Device-unnamed-declare interface ItemDragEventHandler--><!--Device-unnamed-declare interface ItemDragEventHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMoveThrough

```TypeScript
onMoveThrough?: OnMoveHandler
```

Callback triggered when passing through other components during page-following sliding. When not set, this callback is not triggered. The parameter **from** is the Start Index of the drag, and the parameter **to** is the Target Index currently passed through. The value range of both is [0, Data Source Length - 1].

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ItemDragEventHandler-onMoveThrough?: OnMoveHandler--><!--Device-ItemDragEventHandler-onMoveThrough?: OnMoveHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDragStart

```TypeScript
onDragStart?: Callback<number>
```

Callback triggered when drag starts. When not set, this callback is not triggered. The parameter **index** is the index of the current target when drag starts. The value range is [0, Data Source Length - 1].

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;number&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ItemDragEventHandler-onDragStart?: Callback<number>--><!--Device-ItemDragEventHandler-onDragStart?: Callback<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDrop

```TypeScript
onDrop?: Callback<number>
```

Callback triggered when drag ends. When not set, this callback is not triggered. The parameter **index** is the index of the current target when drag ends. The value range is [0, Data Source Length - 1].

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;number&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ItemDragEventHandler-onDrop?: Callback<number>--><!--Device-ItemDragEventHandler-onDrop?: Callback<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<number>
```

Callback triggered when long pressed. When not set, this callback is not triggered. The parameter **index** is the index of the current target when long pressed. The value range is [0, Data Source Length - 1].

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;number&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ItemDragEventHandler-onLongPress?: Callback<number>--><!--Device-ItemDragEventHandler-onLongPress?: Callback<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
