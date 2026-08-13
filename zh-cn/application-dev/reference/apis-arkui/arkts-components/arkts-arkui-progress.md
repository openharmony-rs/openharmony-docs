# Progress

进度条组件，用于显示内容加载或操作处理等进度。支持线性、环形、圆形、胶囊等多种样式，可自定义颜色、渐变效果和动效，适用于文件下载、数据加载、任务处理等需要展示进度状态的场景。通过丰富的样式与动效配置，可快速实现进度可视化，提升用户体 验。

## 子组件 无

## Progress

```TypeScript
Progress(options: ProgressOptions<Type>)
```

创建进度条组件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressInterface-<Type extends keyof ProgressStyleMap>(options: ProgressOptions<Type>): ProgressAttribute<Type>--><!--Device-ProgressInterface-<Type extends keyof ProgressStyleMap>(options: ProgressOptions<Type>): ProgressAttribute<Type>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ProgressOptions](arkts-arkui-progressoptions-i.md)&lt;[Type](../../apis-arkts/arkts-apis/arkts-arkts-util-type-e.md)&gt; | 是 | 按进度条类型不同，设置不同属性的进度条组件参数。 |

## 汇总

- [CapsuleStyleOptions](arkts-arkui-capsulestyleoptions-i.md)
- [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)
- [EclipseStyleOptions](arkts-arkui-eclipsestyleoptions-i.md)
- [LinearStyleOptions](arkts-arkui-linearstyleoptions-i.md)
- [ProgressConfiguration](arkts-arkui-progressconfiguration-i.md)
- [ProgressOptions](arkts-arkui-progressoptions-i.md)
- [ProgressStyleMap](arkts-arkui-progressstylemap-i.md)
- [ProgressStyleOptions](arkts-arkui-progressstyleoptions-i.md)
- [RingStyleOptions](arkts-arkui-ringstyleoptions-i.md)
- [ScaleRingStyleOptions](arkts-arkui-scaleringstyleoptions-i.md)
- [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md)
- [ProgressStatus](arkts-arkui-progressstatus-e.md)
- [ProgressStyle](arkts-arkui-progressstyle-e.md)
- [ProgressType](arkts-arkui-progresstype-e.md)
