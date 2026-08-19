# ProgressButtonV2ColorOptions

下载按钮色彩信息选项。 设备行为差异：该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**起始版本：** 18

<!--Device-unnamed-export declare interface ProgressButtonV2ColorOptions--><!--Device-unnamed-export declare interface ProgressButtonV2ColorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ProgressButtonV2, ProgressButtonV2Color, ProgressButtonV2ColorOptions } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

按钮背景颜色。<br/>默认值：\\$r('sys.color.ohos_id_color_foreground_contrary')

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2ColorOptions-backgroundColor?: ColorMetrics--><!--Device-ProgressButtonV2ColorOptions-backgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ColorMetrics
```

按钮描边颜色。<br/>默认值：#330A59F7

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2ColorOptions-borderColor?: ColorMetrics--><!--Device-ProgressButtonV2ColorOptions-borderColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## progressColor

```TypeScript
progressColor?: ColorMetrics
```

进度条颜色。<br/>默认值：#330A59F7

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2ColorOptions-progressColor?: ColorMetrics--><!--Device-ProgressButtonV2ColorOptions-progressColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textColor

```TypeScript
textColor?: ColorMetrics
```

按钮文本颜色。<br/>默认值：系统默认值(#CE000000)

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2ColorOptions-textColor?: ColorMetrics--><!--Device-ProgressButtonV2ColorOptions-textColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

