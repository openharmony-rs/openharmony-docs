# SliderShowStepOptions

Slider刻度点的无障碍文本信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SliderShowStepOptions--><!--Device-unnamed-export declare interface SliderShowStepOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stepsAccessibility

```TypeScript
stepsAccessibility?: Map<double, SliderStepItemAccessibility>
```

用于设置刻度点提供辅助功能文本，供屏幕阅读器等工具读取，增强无障碍功能。 Key取值范围：[0, INT32\_MAX]，当Key设定为负数和小数时，设定项不生效。 默认值：{}

**类型：** Map&lt;double, SliderStepItemAccessibility&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderShowStepOptions-stepsAccessibility?: Map<double, SliderStepItemAccessibility>--><!--Device-SliderShowStepOptions-stepsAccessibility?: Map<double, SliderStepItemAccessibility>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

