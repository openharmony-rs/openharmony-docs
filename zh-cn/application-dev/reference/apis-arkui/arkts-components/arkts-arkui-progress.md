# Progress

进度条组件，用于显示内容加载或操作处理等进度。

## 子组件

无

## Progress

```TypeScript
Progress(options: ProgressOptions<Type>)
```

创建进度条组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressInterface-<Type extends keyof ProgressStyleMap>(options: ProgressOptions<Type>): ProgressAttribute<Type>--><!--Device-ProgressInterface-<Type extends keyof ProgressStyleMap>(options: ProgressOptions<Type>): ProgressAttribute<Type>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ProgressOptions&lt;Type&gt; | 是 | 按进度条类型不同，设置不同属性的进度条组件参数。 |

## 汇总

- [CapsuleStyleOptions](arkts-arkui-progress-capsulestyleoptions-i.md)
- [CommonProgressStyleOptions](arkts-arkui-progress-commonprogressstyleoptions-i.md)
- [EclipseStyleOptions](arkts-arkui-progress-eclipsestyleoptions-i.md)
- [LinearStyleOptions](arkts-arkui-progress-linearstyleoptions-i.md)
- [ProgressConfiguration](arkts-arkui-progress-progressconfiguration-i.md)
- [ProgressOptions](arkts-arkui-progress-progressoptions-i.md)
- [ProgressStyleMap](arkts-arkui-progress-progressstylemap-i.md)
- [ProgressStyleOptions](arkts-arkui-progress-progressstyleoptions-i.md)
- [RingStyleOptions](arkts-arkui-progress-ringstyleoptions-i.md)
- [ScaleRingStyleOptions](arkts-arkui-progress-scaleringstyleoptions-i.md)
- [ScanEffectOptions](arkts-arkui-progress-scaneffectoptions-i.md)
- [ProgressStatus](arkts-arkui-progress-progressstatus-e.md)
- [ProgressStyle](arkts-arkui-progress-progressstyle-e.md)
- [ProgressType](arkts-arkui-progress-progresstype-e.md)
