# LoadingProgress

用于显示加载动效的组件。

加载动效在组件不可见时停止，组件的可见状态基于
[onVisibleAreaChange]{@link CommonMethod#onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback)}
处理，可见阈值ratios大于0即视为可见状态。

> **说明：**

> - 该组件从API版本26.0.0开始支持[WithTheme]{@link with_theme}。

## 子组件

无

## LoadingProgress

```TypeScript
LoadingProgress()
```

创建加载进度组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LoadingProgressInterface-(): LoadingProgressAttribute--><!--Device-LoadingProgressInterface-(): LoadingProgressAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

- [LoadingProgressConfiguration](arkts-arkui-loadingprogress-loadingprogressconfiguration-i.md)
- [LoadingProgressStyle](arkts-arkui-loadingprogress-loadingprogressstyle-e.md)
