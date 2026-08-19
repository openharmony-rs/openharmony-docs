# ChainEdgeEffect（系统接口）

设置链式动效的边缘效果，用于决定列表滚动到边缘后继续拖动时列表项间距的变化方式。

**起始版本：** 10

<!--Device-unnamed-declare enum ChainEdgeEffect--><!--Device-unnamed-declare enum ChainEdgeEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## DEFAULT

```TypeScript
DEFAULT
```

默认效果，列表滚动到边缘以后继续拖动，拖拽方向上的列表项间距缩小， 拖拽反方向上的列表项间距扩大，适用于需要方向性拉伸、回弹反馈的场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChainEdgeEffect-DEFAULT--><!--Device-ChainEdgeEffect-DEFAULT-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## STRETCH

```TypeScript
STRETCH
```

列表滚动到边缘以后继续拖动，所有列表项间距扩大，适用于需要所有列表项同步拉伸反馈的场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChainEdgeEffect-STRETCH--><!--Device-ChainEdgeEffect-STRETCH-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

