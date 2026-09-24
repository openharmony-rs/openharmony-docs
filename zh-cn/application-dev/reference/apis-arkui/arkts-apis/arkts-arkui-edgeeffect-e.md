# EdgeEffect

```TypeScript
declare enum EdgeEffect
```

定义滚动容器的滑动效果。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Spring

```TypeScript
Spring
```

弹性物理动效，滑动到边缘后可以根据初始速度或通过触摸事件继续滑动一段距离，松手后回弹。

API version 22及之前版本，拖动滚动条，滚动组件的弹性物理动效不生效。

从API version 23开始，通过手指拖动滚动条，滚动组件的弹性物理动效可以生效。通过鼠标拖动滚动条，滚动组件的弹性物理动效不能生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Fade

```TypeScript
Fade
```

阴影效果，滑动到边缘后会有圆弧状的阴影。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None
```

滑动到边缘后无效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
