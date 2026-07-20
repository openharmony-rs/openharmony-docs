# DynamicRangeModeOptions

定义截图所使用的动态范围模式。

**起始版本：** 23

<!--Device-componentSnapshot-interface DynamicRangeModeOptions--><!--Device-componentSnapshot-interface DynamicRangeModeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## dynamicRangeMode

```TypeScript
dynamicRangeMode?: DynamicRangeMode
```

指定截图使用的动态范围模式。

默认情况下，系统以[STANDARD](../arkts-components/arkts-arkui-dynamicrangemode-e.md)模式进行截图。如果知道被截图组件使用的动态范围模式，可通过`dynamicRangeMode`字段指定具体的动态范围模式，并将`isAuto`设置为false，以达到预期的截图效果。

虽然动态范围模式有三种，但是HIGH和CONSTRAINT的表现均为HDR（高动态范围）。STANDARD模式对应表现为SDR（标准动态范围）。

在指定了合法的动态范围模式之后，截图实际采用的动态范围会受到被截图组件和设置值的双重影响，具体如下：

1. 当被截图组件的动态范围为SDR时，即使指定动态范围模式为HIGH，截图实际采用的动态范围为SDR。2. 当被截图组件的动态范围为HDR时，截图实际采用的动态范围为指定的动态范围模式。3. 当配置[色彩空间](arkts-arkui-componentsnapshot-colormodeoptions-i.md)为SRGB或DISPLAY_P3时，截图实际采用的动态范围为SDR。4. 如果被截图组件同时包含SDR和HDR两种动态范围的子组件时，则当作HDR处理。5. 如果3和4的条件同时被满足，则截图实际采用的动态范围为SDR。

取值范围：[DynamicRangeMode](../arkts-components/arkts-arkui-dynamicrangemode-e.md) 枚举值。

默认值：STANDARD

如果值为undefined、null或未设置，则使用默认值截图；其他异常值会导致截图失败，返回错误码160003。

**类型：** DynamicRangeMode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicRangeModeOptions-dynamicRangeMode?: DynamicRangeMode--><!--Device-DynamicRangeModeOptions-dynamicRangeMode?: DynamicRangeMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isAuto

```TypeScript
isAuto?: boolean
```

是否由系统自动决定所使用的动态范围模式。

支持取值为：true表示系统自动决定所使用的动态范围模式；false表示使用通过`dynamicRangeMode`字段设置的动态范围类型进行截图。取非法值时，按默认值false处理。

默认值：false

离屏截图仅支持设置为false，否则会返回错误码160004。

当`isAuto`设置为true时，建议将[SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md)中的`waitUntilRenderFinished`字段也设置为true，以便确保系统可以正常检测到所用的模式。

在不确定组件使用的动态范围模式时，建议将`isAuto`设置为true，让系统根据实际情况自动决定使用的动态范围模式。

当`isAuto`为true时，`dynamicRangeMode`字段设置的值会被忽略。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicRangeModeOptions-isAuto?: boolean--><!--Device-DynamicRangeModeOptions-isAuto?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

