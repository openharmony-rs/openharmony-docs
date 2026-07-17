# ArcButtonProgressConfig

ArcButton内进度条的参数配置。

**起始版本：** 23

<!--Device-unnamed-export declare class ArcButtonProgressConfig--><!--Device-unnamed-export declare class ArcButtonProgressConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcButtonPosition, ArcButton, ArcButtonStatus, ArcButtonStyleMode, ArcButtonOptions, ArcButtonProgressConfig } from '@kit.ArkUI';
```

## color

```TypeScript
color?: ResourceColor
```

进度条前景色。如果组件设置了背景色（[backgroundColor](arkts-arkui-arkui-advanced-arcbutton-arcbuttonoptions-c.md)），进度条前景色默认值取组件背景色。进度条前景色不受按钮样式（[ArcButtonStyleMode](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)）设置影响。进度条背景色仅依赖进度条前景色设置，取进度条前景色的25%透明度。

默认值："#1F71FF"，显示为蓝色。

**类型：** ResourceColor

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonProgressConfig-color?: ResourceColor--><!--Device-ArcButtonProgressConfig-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## total

```TypeScript
total?: number
```

进度的最大值。

默认值：100

取值范围：[0, 2147483647]，设置0或超出取值范围取默认值为100。

**类型：** number

**默认值：** 100

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonProgressConfig-total?: number--><!--Device-ArcButtonProgressConfig-total?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## value

```TypeScript
value: number
```

进度条当前值。设置小于0的数值时置为0，设置大于total的数值时置为total。

默认值：0

取值范围：[0, total]

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonProgressConfig-value: number--><!--Device-ArcButtonProgressConfig-value: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

