# CanvasParams

定义Canvas的具体配置参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-unnamed-declare interface CanvasParams--><!--Device-unnamed-declare interface CanvasParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。 异常值null和undefined按不开启AI分析功能处理。 默认值：不开启AI分析功能。

**类型：** ImageAIOptions

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasParams-imageAIOptions?: ImageAIOptions--><!--Device-CanvasParams-imageAIOptions?: ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unit

```TypeScript
unit?: LengthMetricsUnit
```

用于描述Canvas绘制时所采用的单位模式，不同单位模式会影响绘制时的坐标和尺寸计算方式，具体说明见 [LengthMetricsUnit]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 仅可在创建Canvas时设置，后续不可修改。 默认值：LengthMetricsUnit.DEFAULT

**类型：** LengthMetricsUnit

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasParams-unit?: LengthMetricsUnit--><!--Device-CanvasParams-unit?: LengthMetricsUnit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

