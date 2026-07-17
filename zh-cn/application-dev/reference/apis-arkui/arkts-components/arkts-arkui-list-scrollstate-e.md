# ScrollState

滑动状态枚举。

**起始版本：** 7

<!--Device-unnamed-declare enum ScrollState--><!--Device-unnamed-declare enum ScrollState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Idle

```TypeScript
Idle
```

空闲状态。滚动状态回归空闲时触发，控制器提供的无动画方法控制滚动时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollState-Idle--><!--Device-ScrollState-Idle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Scroll

```TypeScript
Scroll
```

滚动状态。手指拖动List，拖动滚动条和滚动鼠标滚轮时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollState-Scroll--><!--Device-ScrollState-Scroll-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Fling

```TypeScript
Fling
```

惯性滚动状态。动画控制的滚动都会触发。包括快速划动松手后的惯性滚动，

划动到边缘回弹的滚动，快速拖动内置滚动条松手后的惯性滚动，

使用滚动控制器提供的带动画的方法控制的滚动。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollState-Fling--><!--Device-ScrollState-Fling-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

