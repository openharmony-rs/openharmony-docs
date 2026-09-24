# RenderFit

```TypeScript
declare enum RenderFit
```

表示宽高动画过程中组件内容的填充方式。

> **说明：** 
> 
> - 示意图中，蓝色区域表示内容，橙黄色区域表示节点大小。
> 
> - 不同的内容填充方式在宽高动画过程中效果不一致，开发者需要选择合适的内容填充方式以实现需要的动画效果。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CENTER

```TypeScript
CENTER = 0
```

保持动画终态的内容大小，并且内容始终与组件保持中心对齐。 ! [renderfit_center](../../../reference/apis-arkui/arkui-ts/figures/renderfit_center.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 1
```

保持动画终态的内容大小，并且内容始终与组件保持顶部中心对齐。 ! [renderfit_top](../../../reference/apis-arkui/arkui-ts/figures/renderfit_top.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 2
```

保持动画终态的内容大小，并且内容始终与组件保持底部中心对齐。 ! [renderfit_bottom](../../../reference/apis-arkui/arkui-ts/figures/renderfit_bottom.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LEFT

```TypeScript
LEFT = 3
```

保持动画终态的内容大小，并且内容始终与组件保持左侧对齐。 ! [renderfit_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_left.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RIGHT

```TypeScript
RIGHT = 4
```

保持动画终态的内容大小，并且内容始终与组件保持右侧对齐。 ! [renderfit_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_right.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP_LEFT

```TypeScript
TOP_LEFT = 5
```

保持动画终态的内容大小，并且内容始终与组件保持左上角对齐。 ! [renderfit_top_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_top_left.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP_RIGHT

```TypeScript
TOP_RIGHT = 6
```

保持动画终态的内容大小，并且内容始终与组件保持右上角对齐。 ! [renderfit_top_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_top_right.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_LEFT

```TypeScript
BOTTOM_LEFT = 7
```

保持动画终态的内容大小，并且内容始终与组件保持左下角对齐。 ! [renderfit_bottom_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_bottom_left.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_RIGHT

```TypeScript
BOTTOM_RIGHT = 8
```

保持动画终态的内容大小，并且内容始终与组件保持右下角对齐。 ! [renderfit_bottom_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_bottom_right.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_FILL

```TypeScript
RESIZE_FILL = 9
```

不考虑动画终态内容的宽高比，并且内容始终缩放到组件的大小。 ! [renderfit_resize_fill](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_fill.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_CONTAIN

```TypeScript
RESIZE_CONTAIN = 10
```

保持动画终态内容的宽高比进行缩小或放大，使内容完整显示在组件内，且与组件保持中心对齐。 ! [renderfit_resize_contain](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_contain.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_CONTAIN_TOP_LEFT

```TypeScript
RESIZE_CONTAIN_TOP_LEFT = 11
```

保持动画终态内容的宽高比进行缩小或放大，使内容完整显示在组件内。当组件宽方向有剩余时，内容与组件保持左侧对齐，当组件高方向有剩余时，内容与组件保持顶部对齐。 ! [renderfit_resize_contain_top_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_contain_top_left.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_CONTAIN_BOTTOM_RIGHT

```TypeScript
RESIZE_CONTAIN_BOTTOM_RIGHT = 12
```

保持动画终态内容的宽高比进行缩小或放大，使内容完整显示在组件内。当组件宽方向有剩余时，内容与组件保持右侧对齐，当组件高方向有剩余时，内容与组件保持底部对齐。 ! [renderfit_resize_contain_bottom_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_contain_bottom_right.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_COVER

```TypeScript
RESIZE_COVER = 13
```

保持动画终态内容的宽高比进行缩小或放大，使内容两边都大于或等于组件两边，且与组件保持中心对齐，显示内容的中间部分。 ! [renderfit_resize_cover](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_cover.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_COVER_TOP_LEFT

```TypeScript
RESIZE_COVER_TOP_LEFT = 14
```

保持动画终态内容的宽高比进行缩小或放大，使内容的两边都恰好大于或等于组件两边。当内容宽方向有剩余时，内容与组件保持左侧对齐，显示内容的左侧部分。当内容高方向有剩余时，内容与组件保持顶部对齐，显示内容的顶侧部分。 ! [renderfit_resize_cover_top_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_cover_top_left.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_COVER_BOTTOM_RIGHT

```TypeScript
RESIZE_COVER_BOTTOM_RIGHT = 15
```

保持动画终态内容的宽高比进行缩小或放大，使内容的两边都恰好大于或等于组件两边。当内容宽方向有剩余时，内容与组件保持右侧对齐，显示内容的右侧部分。当内容高方向有剩余时，内容与组件保持底部对齐，显示内容的底侧部分。 ! [renderfit_resize_cover_bottom_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_cover_bottom_right.png)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
