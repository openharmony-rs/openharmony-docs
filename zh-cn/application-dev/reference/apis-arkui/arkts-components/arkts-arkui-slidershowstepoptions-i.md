# SliderShowStepOptions

Slider刻度点的无障碍文本信息映射集。

**起始版本：** 20

<!--Device-unnamed-declare interface SliderShowStepOptions--><!--Device-unnamed-declare interface SliderShowStepOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## stepsAccessibility

```TypeScript
stepsAccessibility?: Map<number, SliderStepItemAccessibility>
```

刻度点无障碍文本映射集，供屏幕阅读器等工具读取，增强无障碍功能。 Key取值范围：[0, INT32_MAX]，当Key设定为负数和小数时，设定项不生效。 默认值：{}

**类型：** Map&lt;number, [SliderStepItemAccessibility](arkts-arkui-sliderstepitemaccessibility-i.md)&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SliderShowStepOptions-stepsAccessibility?: Map<number, SliderStepItemAccessibility>--><!--Device-SliderShowStepOptions-stepsAccessibility?: Map<number, SliderStepItemAccessibility>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

