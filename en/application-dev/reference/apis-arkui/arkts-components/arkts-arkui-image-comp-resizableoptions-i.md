# ResizableOptions

```TypeScript
declare interface ResizableOptions
```

Defines the resizable image options.

**Figure 1** Effect of Setting EdgeWidths![edgewidths](../../../reference/apis-arkui/arkui-ts/figures/edgewidths.png)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lattice

```TypeScript
lattice?: DrawingLattice
```

Lattice object, which is used to divide the image by lattice.

**NOTE:** 

Use the [createImageLattice](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-lattice-c.md#createimagelattice) API of **@ohos.graphics.drawing** to create a **Lattice** type as the input parameter. Lattices located at both even columns and even rows are fixed; those at other positions are stretched according to **slice**.

This parameter does not take effect for the [backgroundImageResizable](arkts-arkui-common-comp-commonmethod-c.md#backgroundimageresizable) API.

When a number is passed, the default unit is px.

**Type:** [DrawingLattice](arkts-arkui-image-comp-drawinglattice-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## slice

```TypeScript
slice?: EdgeWidths
```

Edge widths in different directions of a component.

**NOTE:** 

This attribute takes effect only when both **bottom** and **right** are greater than 0.

When **top** is set, the top part of the image is stretched while the pixel values of the image remain unchanged.

When **right** is set, the right part of the image is stretched while the pixel values of the image remain unchanged.

When **bottom** is set, the bottom part of the image is stretched while the pixel values of the image remain unchanged.

When **left** is set, the left part of the image is stretched while the pixel values of the image remain unchanged.

The default width of each direction is **0**. The default unit is vp.

The effect of setting **EdgeWidths** is shown in Figure 1 (Effect of Setting EdgeWidths).

**Type:** EdgeWidths

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
