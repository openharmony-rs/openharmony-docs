# RepeatItemBuilder

```TypeScript
declare type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void
```

Defines builder function to render one template type.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| repeatItem | [RepeatItem](arkts-arkui-repeatitem-i.md)&lt;T&gt; | Yes | State variable that combines **item** and **index**. |
