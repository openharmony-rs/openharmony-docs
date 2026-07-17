# CanvasParams

定义Canvas的具体配置参数。

**起始版本：** 23

<!--Device-unnamed-declare interface CanvasParams--><!--Device-unnamed-declare interface CanvasParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。

**类型：** ImageAIOptions

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasParams-imageAIOptions?: ImageAIOptions--><!--Device-CanvasParams-imageAIOptions?: ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unit

```TypeScript
unit?: LengthMetricsUnit
```

用于描述Canvas绘制时所采用的单位模式。<br>仅可在创建Canvas时设置，后续不可修改。<br>默认值：**LengthMetricsUnit.DEFAULT**

**类型：** LengthMetricsUnit

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasParams-unit?: LengthMetricsUnit--><!--Device-CanvasParams-unit?: LengthMetricsUnit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

