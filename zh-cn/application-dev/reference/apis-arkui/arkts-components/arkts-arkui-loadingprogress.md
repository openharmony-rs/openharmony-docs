# LoadingProgress

LoadingProgress是用于显示加载进度条的组件，在数据加载过程中为用户提供视觉反馈，提升用户体验。该组件支持设置前景色、控制动画显示状态等特性，适用于需要在应用内展示加载进度的场景。 加载进度条的动效在组件不可见时停止，组件的可见状态基于 onVisibleAreaChange 处理，可见阈值ratios大于0即视为可见状态。 > **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件 无

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

### 接口

| 名称 | 说明 |
| --- | --- |
| [LoadingProgressConfiguration](arkts-arkui-loadingprogressconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LoadingProgressStyle](arkts-arkui-loadingprogressstyle-e.md) | 表示LoadingProgress的样式类型，不推荐使用。 |

