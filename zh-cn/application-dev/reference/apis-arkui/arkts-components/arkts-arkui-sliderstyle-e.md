# SliderStyle

滑动条滑块在滑轨上显示的样式，具体样式请参考[Slider组件滑块与滑轨是如何对齐的](../../../../ui/arkts-select-component-faq.md#slider组件滑块与滑轨是如何对齐的)。

> **说明：**
>
> - Slider无默认padding。
>
> - 当Slider为水平滑动条时，默认高度为40vp，宽度为父容器的宽度，滑动条居中显示，当滑动条的style为SliderStyle.OutSet时，左右间距分别为9vp，即为
> [blockSize](SliderAttribute#blockSize)宽度的一半，当滑动条的style为SliderStyle.InSet时，左右间距分别为6vp，若设置padding，padding不会覆盖左右
> 间距。
>
> - 当Slider为竖直滑动条时，默认宽度为40vp，高度为父容器的高度，滑动条居中显示，当滑动条的style为SliderStyle.OutSet时，上下间距分别为10vp，当滑动条的style为
> SliderStyle.InSet时，上下间距分别为6vp，若设置padding，padding不会覆盖上下间距。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OutSet

```TypeScript
OutSet
```

滑块在滑轨上。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## InSet

```TypeScript
InSet
```

滑块在滑轨内。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE
```

无滑块

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

