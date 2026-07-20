# CaptionsStyle

字幕风格。

**起始版本：** 8

<!--Device-accessibility-interface CaptionsStyle--><!--Device-accessibility-interface CaptionsStyle-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## backgroundColor

```TypeScript
backgroundColor: number | string
```

描述字幕背景颜色。

number：HEX 格式颜色，支持 rgb 或 argb。

string：支持 '#rrggbb', '#rrggbbaa', '#rgb', '#rgba' 格式。

例：不透明红色，number: 0xffff0000，string: '#ff0000', '#ff0000ff', '#f00', '#f00f'。

**类型：** number \| string

**起始版本：** 8

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsStyle-backgroundColor: int | string--><!--Device-CaptionsStyle-backgroundColor: int | string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## fontColor

```TypeScript
fontColor: number | string
```

描述字幕字体颜色。

number：HEX 格式颜色，支持 rgb 或 argb。

string：支持 '#rrggbb', '#rrggbbaa', '#rgb', '#rgba' 格式。

例：不透明红色，number: 0xffff0000，string: '#ff0000', '#ff0000ff', '#f00', '#f00f'。

**类型：** number \| string

**起始版本：** 8

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsStyle-fontColor: int | string--><!--Device-CaptionsStyle-fontColor: int | string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## fontEdgeType

```TypeScript
fontEdgeType: CaptionsFontEdgeType
```

描述字幕字体边缘。

**类型：** CaptionsFontEdgeType

**起始版本：** 8

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsStyle-fontEdgeType: CaptionsFontEdgeType--><!--Device-CaptionsStyle-fontEdgeType: CaptionsFontEdgeType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## fontFamily

```TypeScript
fontFamily: CaptionsFontFamily
```

描述字幕字体。

**类型：** CaptionsFontFamily

**起始版本：** 8

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsStyle-fontFamily: CaptionsFontFamily--><!--Device-CaptionsStyle-fontFamily: CaptionsFontFamily-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## fontScale

```TypeScript
fontScale: number
```

描述字幕字体缩放系数，单位%，参数范围1~200。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsStyle-fontScale: int--><!--Device-CaptionsStyle-fontScale: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

## windowColor

```TypeScript
windowColor: number | string
```

描述字幕窗口颜色。

number：HEX 格式颜色，支持 rgb 或 argb。

string：支持 '#rrggbb', '#rrggbbaa', '#rgb', '#rgba' 格式。

例：不透明红色，number: 0xffff0000，string: '#ff0000', '#ff0000ff', '#f00', '#f00f'。

**类型：** number \| string

**起始版本：** 8

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CaptionsStyle-windowColor: int | string--><!--Device-CaptionsStyle-windowColor: int | string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

