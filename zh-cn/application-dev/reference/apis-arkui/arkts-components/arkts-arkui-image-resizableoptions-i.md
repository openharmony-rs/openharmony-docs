# ResizableOptions

图像拉伸时可调整大小的图像选项。

**图1** 设置EdgeWidths效果图![edgewidths](../../../../reference/apis-arkui/arkui-ts/figures/edgewidths.png)

**起始版本：** 11

<!--Device-unnamed-declare interface ResizableOptions--><!--Device-unnamed-declare interface ResizableOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lattice

```TypeScript
lattice?: DrawingLattice
```

矩形网格对象。

**说明：**

通过@ohos.graphics.drawing的[createImageLattice](@ohos.graphics.drawing:drawing.Lattice.createImageLattice(xDivs: Array<number>, yDivs: Array<number>,fXCount: number, fYCount: number, fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null,fColors?: Array<common2D.Color> | null))接口创建Lattice类型作为入参。将图像划分为矩形网格，同时处于偶数列和偶数行上的网格图像是固定的，不会被拉伸。其他位置的网格图像会根据slice进行拉伸。

该参数对[backgroundImageResizable](arkts-arkui-common-commonmethod-c.md#backgroundimageresizable-1)接口不生效。

传入数字时默认单位为px。

**类型：** DrawingLattice

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ResizableOptions-lattice?: DrawingLattice--><!--Device-ResizableOptions-lattice?: DrawingLattice-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## slice

```TypeScript
slice?: EdgeWidths
```

边框宽度类型，用于描述组件边框不同方向的宽度。

**说明：**

只有当bottom和right同时大于0时，该属性生效。

当设置了top时，图片顶部拉伸，图片的像素值保持不变。

当设置了right时，图片右部拉伸，图片的像素值保持不变。

当设置了bottom时，图片底部拉伸，图片的像素值保持不变。

当设置了left时，图片左部拉伸，图片的像素值保持不变。

每个方向的宽度默认值为0，传入数字时默认单位为vp。

设置了EdgeWidths后的效果如图1（设置EdgeWidths效果图）所示。

单位：vp

**类型：** EdgeWidths

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ResizableOptions-slice?: EdgeWidths--><!--Device-ResizableOptions-slice?: EdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

