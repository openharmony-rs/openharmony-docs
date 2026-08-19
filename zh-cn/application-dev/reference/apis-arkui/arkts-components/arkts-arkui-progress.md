# Progress

进度条组件，用于显示内容加载或操作处理等进度。支持线性、环形、圆形、胶囊等多种样式，可自定义颜色、渐变效果和动效，适用于文件下载、数据加载、任务处理等需要展示进度状态的场景。通过丰富的样式与动效配置，可快速实现进度可视化，提升用户体 验。

## 子组件 无

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
| options | [ProgressOptions](arkts-arkui-progressoptions-i.md)&lt;[Type](../../apis-arkts/arkts-apis/arkts-arkts-util-type-e.md)&gt; | 是 | 按进度条类型不同，设置不同属性的进度条组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CapsuleStyleOptions](arkts-arkui-capsulestyleoptions-i.md) | 胶囊样式选项。 继承自[ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md)和[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。 |
| [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md) | 进度条通用样式选项。 |
| [EclipseStyleOptions](arkts-arkui-eclipsestyleoptions-i.md) | 圆形样式选项。圆形样式的显示类似月圆月缺的进度展示效果，从月牙逐渐变化至满月。 继承自[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。 |
| [LinearStyleOptions](arkts-arkui-linearstyleoptions-i.md) | 线性样式选项。 继承自[ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md)和[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。 |
| [ProgressConfiguration](arkts-arkui-progressconfiguration-i.md) | 进度条配置。继承自CommonConfiguration。 |
| [ProgressOptions](arkts-arkui-progressoptions-i.md) | 进度条选项。 |
| [ProgressStyleMap](arkts-arkui-progressstylemap-i.md) | 进度条类型和样式的映射表。 |
| [ProgressStyleOptions](arkts-arkui-progressstyleoptions-i.md) | 进度条样式选项。 继承自[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。 |
| [RingStyleOptions](arkts-arkui-ringstyleoptions-i.md) | 环形无刻度样式选项。 继承自[ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md)和[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。 |
| [ScaleRingStyleOptions](arkts-arkui-scaleringstyleoptions-i.md) | 环形有刻度样式选项。 继承自[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。 |
| [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md) | 扫光效果选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ProgressStatus](arkts-arkui-progressstatus-e.md) | 进度条的当前状态。 |
| [ProgressStyle](arkts-arkui-progressstyle-e.md) | 进度条样式。 |
| [ProgressType](arkts-arkui-progresstype-e.md) | 进度条类型。 |

