# RepeatItemBuilder

```TypeScript
declare type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void
```

Defines builder function to render one template type.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void--><!--Device-unnamed-declare type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| repeatItem | [RepeatItem](arkts-arkui-repeat-comp-repeatitem-i.md)&lt;T&gt; | Yes | State variable that combines item and index.<br>When this parameter is omitted, it is ignored by default. Do not use this parameter in the closure function implementation; otherwise, a compile error occurs. |
