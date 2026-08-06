# LoadingProgress

LoadingProgress是用于显示加载进度条的组件，在数据加载过程中为用户提供视觉反馈，提升用户体验。该组件支持设置前景色、控制动画显示状态等特性，适用于需要在应用内展示加载进度的场景。 加载进度条的动效在组件不可见时停止，组件的可见状态基于 [onVisibleAreaChange]{@link CommonMethod#onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback)} 处理，可见阈值ratios大于0即视为可见状态。 > **说明：** > > - 该组件从API版本26.0.0开始支持[WithTheme]{@link ./with_theme}。

## 子组件 无

## LoadingProgress

```TypeScript
LoadingProgress()
```

创建加载进度组件。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LoadingProgressInterface-(): LoadingProgressAttribute--><!--Device-LoadingProgressInterface-(): LoadingProgressAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

