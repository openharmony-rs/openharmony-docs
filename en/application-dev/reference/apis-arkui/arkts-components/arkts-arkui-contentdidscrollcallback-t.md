# ContentDidScrollCallback

```TypeScript
declare type ContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void
```

Triggered during the swipe action of the **Swiper** component. For details about the parameters, see [SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedIndex | number | Yes | Index of the currently selected page. |
| index | number | Yes | Index of a page in the viewport. |
| position | number | Yes | Position of the page specified by **index** relative to the start position of the **Swiper** main axis (start position of the page corresponding to **selectedIndex**). |
| mainAxisLength | number | Yes | Length of the page specified by **index** along the main axis, in vp. |
