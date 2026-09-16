# Progress

进度条组件，用于显示内容加载或操作处理等进度。支持线性、环形、圆形、胶囊等多种样式，可自定义颜色、渐变效果和动效，适用于文件下载、数据加载、任务处理等需要展示进度状态的场景。通过丰富的样式与动效配置，可快速实现进度可视化，提升用户体验。

## 子组件

无

## Progress

```TypeScript
Progress(options: ProgressOptions<Type>)
```

创建进度条组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ProgressOptions](arkts-arkui-progressoptions-i.md)&lt;[Type](../arkts-apis/arkts-arkui-arkui-statemanagement-type-d.md)&gt; | 是 | 按进度条类型不同，设置不同属性的进度条组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CapsuleStyleOptions](arkts-arkui-capsulestyleoptions-i.md) | 胶囊样式选项。 |
| [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md) | 进度条通用样式选项。 |
| [EclipseStyleOptions](arkts-arkui-eclipsestyleoptions-i.md) | 圆形样式选项。圆形样式的显示类似月圆月缺的进度展示效果，从月牙逐渐变化至满月。 |
| [LinearStyleOptions](arkts-arkui-linearstyleoptions-i.md) | 线性样式选项。 |
| [ProgressConfiguration](arkts-arkui-progressconfiguration-i.md) | 进度条配置。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [ProgressOptions](arkts-arkui-progressoptions-i.md) | 进度条选项。 |
| [ProgressStyleMap](arkts-arkui-progressstylemap-i.md) | 进度条类型和样式的映射表。 |
| [ProgressStyleOptions](arkts-arkui-progressstyleoptions-i.md) | 进度条样式选项。 |
| [RingStyleOptions](arkts-arkui-ringstyleoptions-i.md) | 环形无刻度样式选项。 |
| [ScaleRingStyleOptions](arkts-arkui-scaleringstyleoptions-i.md) | 环形有刻度样式选项。 |
| [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md) | 扫光效果选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ProgressStatus](arkts-arkui-progressstatus-e.md) | 进度条的当前状态。 |
| [ProgressStyle](arkts-arkui-progressstyle-e.md) | 进度条样式。 |
| [ProgressType](arkts-arkui-progresstype-e.md) | 进度条类型。 |

## 示例

```TypeScript
### 示例1（设置进度条的类型）

该示例通过[ProgressOptions](#progressoptions对象说明)的入参type，实现了设置进度条类型的功能。


```

```TypeScript
### 示例2（设置环形进度条属性）

该示例通过[style](#style8)接口的strokeWidth和shadow属性，实现了环形进度条视觉属性设置功能。


```

```TypeScript
### 示例3（设置环形进度条动画）

该示例通过[style](#style8)接口的status和enableScanEffect属性，实现了环形进度条动效的开关功能。


```

```TypeScript
### 示例4（设置胶囊形进度条属性）

该示例通过[style](#style8)接口的borderColor、borderWidth、content、font、fontColor、enableScanEffect、showDefaultPercentage属性，实现胶囊形进度条的视觉属性设置。


```

```TypeScript
### 示例5（设置进度平滑动效）

该示例通过[style](#style8)接口的enableSmoothEffect属性，实现了进度平滑动效开关的功能。


```

```TypeScript
### 示例6（设置定制内容区）

该示例通过[contentModifier](#contentmodifier12)接口，实现了自定义进度条的功能，自定义实现星形，其中总进度为3，且当前值可通过按钮进行增减，达到的进度使用自定义颜色填充。


```

```TypeScript
### 示例7（设置隐私隐藏）

该示例通过[privacySensitive](#privacysensitive12)属性，实现了隐私隐藏效果。效果展示需要卡片框架支持。


```

```TypeScript
### 示例8（设置Capsule进度条圆角半径）

该示例通过[CapsuleStyleOptions](arkts-arkui-capsulestyleoptions-i.md)的入参borderRadius，实现了Capsule类型进度条圆角半径设置。

从API version 18开始，新增borderRadius属性。


```

```TypeScript
### 示例9（设置线性进度条和胶囊进度条属性）

从API version 23开始，该示例通过[color](#color)属性中的LinearGradient，实现线性进度条和胶囊进度条渐变色的功能。
```
