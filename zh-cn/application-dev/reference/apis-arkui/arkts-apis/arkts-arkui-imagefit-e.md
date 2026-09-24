# ImageFit

```TypeScript
declare enum ImageFit
```

用于设置图片填充效果。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Contain

```TypeScript
Contain
```

保持宽高比进行缩小或者放大，使得图片或视频完全显示在边界内，对其方式为水平居中。

![ImageFit-Examples01](../../../reference/apis-arkui/arkui-ts/figures/image_fit_contain.png)

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Cover

```TypeScript
Cover
```

保持宽高比进行缩小或者放大，使得图片或视频两边都大于或等于显示边界，对其方式为水平居中。

![ImageFit-Examples02](../../../reference/apis-arkui/arkui-ts/figures/image_fit_cover.png)

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto
```

图片或视频会根据其自身尺寸和组件的尺寸进行适当缩放，以在保持比例的同时填充视图，对其方式为水平居中。

![ImageFit-Examples03](../../../reference/apis-arkui/arkui-ts/figures/image_fit_auto.png)

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Fill

```TypeScript
Fill
```

不保持宽高比进行放大缩小，使得图片或视频充满显示边界，对齐方式为水平居中。

![ImageFit-Examples04](../../../reference/apis-arkui/arkui-ts/figures/image_fit_fill.png)

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ScaleDown

```TypeScript
ScaleDown
```

保持宽高比进行显示，图片或视频缩小或者保持不变，对齐方式为水平居中。

![ImageFit-Examples05](../../../reference/apis-arkui/arkui-ts/figures/image_fit_scaleDown.png)

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None
```

保持原有尺寸进行显示，对齐方式为水平居中。

![ImageFit-Examples06](../../../reference/apis-arkui/arkui-ts/figures/image_fit_none.png)

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP_START

```TypeScript
TOP_START = 7
```

图片或视频显示在组件的顶部起始端，且保持原有尺寸。

![ImageFit-Examples07](../../../reference/apis-arkui/arkui-ts/figures/image_fit_top_start.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 8
```

图片或视频显示在组件的顶部横向居中，且保持原有尺寸。

![ImageFit-Examples08](../../../reference/apis-arkui/arkui-ts/figures/image_fit_top.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP_END

```TypeScript
TOP_END = 9
```

图片或视频显示在组件的顶部尾端，且保持原有尺寸。

![ImageFit-Examples09](../../../reference/apis-arkui/arkui-ts/figures/image_fit_top_end.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## START

```TypeScript
START = 10
```

图片或视频显示在组件的起始端纵向居中，且保持原有尺寸。

![ImageFit-Examples10](../../../reference/apis-arkui/arkui-ts/figures/image_fit_start.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CENTER

```TypeScript
CENTER = 11
```

图片或视频显示在组件的横向和纵向居中，且保持原有尺寸。

![ImageFit-Examples11](../../../reference/apis-arkui/arkui-ts/figures/image_fit_center.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 12
```

图片或视频显示在组件的尾端纵向居中，且保持原有尺寸。

![ImageFit-Examples12](../../../reference/apis-arkui/arkui-ts/figures/image_fit_end.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_START

```TypeScript
BOTTOM_START = 13
```

图片或视频显示在组件的底部起始端，且保持原有尺寸。

![ImageFit-Examples13](../../../reference/apis-arkui/arkui-ts/figures/image_fit_bottom_start.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 14
```

图片或视频显示在组件的底部横向居中，且保持原有尺寸。

![ImageFit-Examples14](../../../reference/apis-arkui/arkui-ts/figures/image_fit_bottom.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_END

```TypeScript
BOTTOM_END = 15
```

图片或视频显示在组件的底部尾端，且保持原有尺寸。

![ImageFit-Examples15](../../../reference/apis-arkui/arkui-ts/figures/image_fit_bottom_end.png)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MATRIX

```TypeScript
MATRIX = 16
```

配合[imageMatrix](../arkts-components/arkts-arkui-image-comp-attribute.md#imagematrix)使用，使图像在Image组件自定义位置显示，且保持原有尺寸。不支持svg图源。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
